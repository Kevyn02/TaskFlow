← [Voltar para Diagramas](../README.md)

---

[Início](../../../README.md) / [Diagramas](../README.md) / Casos de Uso

---

## 📌 Diagrama de Casos de Uso

> 🔐 Todas as funcionalidades exigem usuário autenticado.

### Autenticação

```mermaid
graph TD

    User[👤 Usuário]

    %% Autenticação
    subgraph AUTH[Autenticação]
        Register((🆕 Criar Conta))
        Login((🔐 Realizar Login))
        SocialLogin((🔗 Login com Google/GitHub))
        Logout((🚪 Logout))
        RecoverPassword((♻️ Recuperar senha))
    end

    User --> Register
    User --> Login
    User --> SocialLogin
    User --> Logout
    User --> RecoverPassword
```

### Projetos

```mermaid
graph TD

    User[👤 Usuário]

    %% Projetos
    subgraph PROJECTS[Projetos]
        ViewProjects((💼 Listar))
        ViewDetailsProject((📄 Visualizar detalhes))
        CreateProject((➕ Criar))
        EditProject((✏️ Editar))
        DeleteProject((🗑️ Excluir))
    end

    User --> ViewProjects
    User --> ViewDetailsProject
    User --> CreateProject
    User --> EditProject
    User --> DeleteProject
```

### Colunas (por projeto)

```mermaid
graph TD

    User[👤 Usuário]

    subgraph PROJECT_COLUMNS["Colunas (por projeto)"]
        ViewProjectColumns((💼 Listar))
        ViewDetailsProjectColumn((📄 Visualizar detalhes))
        CreateProjectColumn((➕ Criar))
        EditProjectColumn((✏️ Editar))
        DeleteProjectColumn((🗑️ Excluir))
    end

    User --> ViewProjectColumns
    User --> ViewDetailsProjectColumn
    User --> CreateProjectColumn
    User --> EditProjectColumn
    User --> DeleteProjectColumn
```

### Tarefas (por projeto)

```mermaid
graph TD

    User[👤 Usuário]

    subgraph PROJECT_TASKS["Tarefas (por projeto)"]
        subgraph ORGANIZATION[Organização]
            FilterProjectTasks((🔍 Filtrar))
            SortProjectTasks((↕️ Ordenar))
        end
        subgraph CRUD[Operações]
            ViewProjectTasks((💼 Listar))
            ViewDetailsProjectTask((📄 Visualizar detalhes))
            CreateProjectTask((➕ Criar))
            EditProjectTask((✏️ Editar))
            DeleteProjectTask((🗑️ Excluir))
        end
        subgraph ACTIONS[Ações]
            MoveProjectTask((🔄 Mover entre colunas))
            SetProjectTaskPriority((⚡ Alterar Prioridade))
        end
    end

    User --> FilterProjectTasks
    User --> SortProjectTasks
    User --> ViewProjectTasks
    User --> ViewDetailsProjectTask
    User --> CreateProjectTask
    User --> EditProjectTask
    User --> DeleteProjectTask
    User --> MoveProjectTask
    User --> SetProjectTaskPriority
```

### Configurações

```mermaid
graph TD

    User[👤 Usuário]

    %% Configurações
    subgraph SETTINGS[Configurações]
        UpdateProfile((👤 Editar Perfil))
        ChangePassword((🔒 Alterar Senha))
        Preferences((⚙️ Preferências))
    end

    User --> UpdateProfile
    User --> ChangePassword
    User --> Preferences
```
