## 🛢️ Banco de dados

### 🧱 Tabelas

#### Usuários (users)

```sql
-- TABELA: users
-- Descrição: Contém os usuários do sistema
-- Relacionamentos:
--   - Criador, atualizador e desativador de projetos, tarefas e membros
-- Indexes:
--   - email, external_id, google_id, github_id

CREATE TABLE users (
    id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    external_id CHAR(36) NOT NULL UNIQUE,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) NOT NULL UNIQUE,
    password VARCHAR(255) NULL,
    google_id VARCHAR(100) NULL UNIQUE,
    github_id VARCHAR(100) NULL UNIQUE,
    avatar_url VARCHAR(255) NULL,
    email_verified_at DATETIME NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    disabled_at DATETIME NULL
);
```

#### Projetos (projects)

```sql
-- TABELA: projects
-- Descrição: Contém os projetos do sistema
-- Relacionamentos:
--   - created_by → users(id)
--   - updated_by → users(id)
--   - disabled_by → users(id)
-- Indexes:
--   - created_by, disabled_at

CREATE TABLE projects (
    id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    external_id CHAR(36) NOT NULL UNIQUE,
    name VARCHAR(150) NOT NULL,
    description TEXT NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    created_by BIGINT UNSIGNED NOT NULL,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    updated_by BIGINT UNSIGNED NULL,
    disabled_at DATETIME NULL,
    disabled_by BIGINT UNSIGNED NULL
);
```

#### Membros do Projeto (project_members)

```sql
-- TABELA: project_members
-- Descrição: Relaciona usuários com projetos
-- Relacionamentos:
--   - project_id → projects(id)
--   - user_id → users(id)
--   - created_by/updated_by/disabled_by → users(id)
-- Indexes:
--   - project_id, user_id
-- UNIQUE:
--   - project_id + user_id

CREATE TABLE project_members (
    id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    external_id CHAR(36) NOT NULL UNIQUE,
    project_id BIGINT UNSIGNED NOT NULL,
    user_id BIGINT UNSIGNED NOT NULL,
    role ENUM('owner','admin','member') DEFAULT 'member',
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    created_by BIGINT UNSIGNED NOT NULL,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    updated_by BIGINT UNSIGNED NULL,
    disabled_at DATETIME NULL,
    disabled_by BIGINT UNSIGNED NULL
);
```

#### Status de Tarefa (task_statuses)

```sql
-- TABELA: task_statuses
-- Descrição: Status que uma tarefa pode ter dentro de um projeto
-- Relacionamentos:
--   - project_id → projects(id)
--   - created_by/updated_by/disabled_by → users(id)
-- Indexes:
--   - project_id, disabled_at
-- UNIQUE:
--   - project_id + slug

CREATE TABLE task_statuses (
    id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    external_id CHAR(36) NOT NULL UNIQUE,
    project_id BIGINT UNSIGNED NOT NULL,
    name VARCHAR(100) NOT NULL,
    slug VARCHAR(50) NOT NULL,
    color VARCHAR(20) NULL,
    position INT NOT NULL DEFAULT 0,
    is_default BOOLEAN DEFAULT FALSE,
    is_final BOOLEAN DEFAULT FALSE,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    created_by BIGINT UNSIGNED NOT NULL,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    updated_by BIGINT UNSIGNED NULL,
    disabled_at DATETIME NULL,
    disabled_by BIGINT UNSIGNED NULL
);
```

#### Tarefas (tasks)

```sql
-- TABELA: tasks
-- Descrição: Contém as tarefas de cada projeto
-- Relacionamentos:
--   - project_id → projects(id)
--   - status_id → task_statuses(id)
--   - created_by/updated_by/disabled_by → users(id)
-- Indexes:
--   - project_id, status_id, created_by, priority, disabled_at

CREATE TABLE tasks (
    id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    external_id CHAR(36) NOT NULL UNIQUE,
    project_id BIGINT UNSIGNED NOT NULL,
    status_id BIGINT UNSIGNED NOT NULL,
    title VARCHAR(150) NOT NULL,
    description TEXT NULL,
    priority TINYINT UNSIGNED NOT NULL DEFAULT 0,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    created_by BIGINT UNSIGNED NOT NULL,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    updated_by BIGINT UNSIGNED NULL,
    disabled_at DATETIME NULL,
    disabled_by BIGINT UNSIGNED NULL
);
```

#### Membros da Tarefa (task_assignees)

```sql
-- TABELA: task_assignees
-- Descrição: Relaciona usuários com tarefas (1 ou mais por tarefa)
-- Relacionamentos:
--   - task_id → tasks(id)
--   - user_id → users(id)
--   - created_by/updated_by/disabled_by → users(id)
-- Indexes:
--   - task_id, user_id
-- UNIQUE:
--   - task_id + user_id

CREATE TABLE task_assignees (
    id BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    external_id CHAR(36) NOT NULL UNIQUE,
    task_id BIGINT UNSIGNED NOT NULL,
    user_id BIGINT UNSIGNED NOT NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    created_by BIGINT UNSIGNED NOT NULL,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    updated_by BIGINT UNSIGNED NULL,
    disabled_at DATETIME NULL,
    disabled_by BIGINT UNSIGNED NULL
);
```
