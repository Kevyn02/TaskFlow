# 📝 TaskFlow

<p align="center">
  <b>Gerenciamento simples e eficiente de tarefas para o dia a dia</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-em%20desenvolvimento-yellow" />
  <img src="https://img.shields.io/badge/plataforma-web%20%7C%20mobile-blue" />
  <img src="https://img.shields.io/badge/licença-MIT-green" />
  <img src="https://img.shields.io/github/last-commit/Kevyn02/TaskFlow" />
  <img src="https://img.shields.io/github/repo-size/Kevyn02/TaskFlow" />
</p>

---

## 📖 Sobre o Projeto

O **TaskFlow** é um aplicativo de gerenciamento de tarefas (to-do list) focado em produtividade, simplicidade e organização.

O sistema permite que usuários gerenciem suas tarefas de forma eficiente, organizando-as por projetos e acompanhando seu progresso no dia a dia.

---

## ✨ Funcionalidades

- 🔐 Sistema de autenticação (login, cadastro e login social)

### 📁 Projetos

- ➕ Criar, ✏️ editar e 🗑️ excluir projetos
- 📂 Visualizar e organizar projetos
- 🎨 Definir identificação visual (cor)

### 📋 Tarefas

- ➕ Criar, ✏️ editar e 🗑️ excluir tarefas
- 🔄 Alterar status da tarefa (fluxo personalizado)
- 🔍 Filtrar e ↕️ ordenar tarefas
- ⚡ Definir prioridade (baixa, média, alta)
- 📁 Organização por projeto

### 🧩 Status personalizados

- 📊 Fluxo de status por projeto
- 🔢 Definição de ordem dos status
- 📝 Nome customizável
- 🎨 Cor para identificação visual

---

## 🧭 Arquitetura de Rotas

A aplicação é organizada em dois grupos principais: **rotas públicas** e **rotas privadas**, separando o fluxo de autenticação do restante do sistema.

---

## 🔓 Rotas Públicas

Acessíveis sem autenticação.

### 🌐 Web

- `/signin`
- `/signup`

### 📱 Mobile

- `SignInScreen`
- `SignUpScreen`

📌 Usuários autenticados são automaticamente redirecionados para `/dashboard`

---

## 🔐 Rotas Privadas

Acessíveis apenas para usuários autenticados.

---

### 📋 Dashboard

#### 🌐 Web

- `/dashboard`

#### 📱 Mobile

- `Dashboard` (via Tabs)

**Responsável por:**

- Visualização geral das tarefas
- Ações rápidas

---

### 📁 Projetos

#### 🌐 Web

- `/projects`
- `/projects/:projectId`

#### 📱 Mobile

- `Projects`
- `ProjectDetail`

**Responsável por:**

- Organização das tarefas por contexto
- Agrupamento por projeto

**Funcionalidades:**

- ➕ Criar projeto
- ✏️ Editar projeto
- 🗑️ Excluir projeto
- 📂 Visualizar projetos

---

### 📋 Tarefas

#### 🌐 Web

- Gerenciadas via **modais** (sem rotas dedicadas)

#### 📱 Mobile

- `/tasks/create`
- `/tasks/:taskId`
- `/tasks/:taskId/edit`

**Responsável por:**

- Gerenciamento de tarefas
- Associação com projetos
- Controle de status e prioridade

**Funcionalidades:**

- ➕ Criar tarefa
- ✏️ Editar tarefa
- 🗑️ Excluir tarefa
- 🔄 Alterar status
- 🔍 Filtrar tarefas
- ↕️ Ordenar tarefas
- ⚡ Definir prioridade

---

### 🧩 Status (por Projeto)

#### 🌐 Web

- Integrado à tela de projeto (`/projects/:projectId`)
- Gerenciado via modais

#### 📱 Mobile

- `/projects/:projectId/status`
- `/projects/:projectId/status/create`
- `/projects/:projectId/status/:statusId/edit`

**Responsável por:**

- Definição do fluxo de status das tarefas
- Personalização por projeto

**Funcionalidades:**

- ➕ Criar status
- ✏️ Editar status
- 🗑️ Remover status
- 🔢 Definir ordem do fluxo
- 🎨 Definir cor
- 📝 Definir nome

📌 Cada projeto possui seu próprio fluxo de status
📌 Utilizado para controlar o ciclo de vida das tarefas

---

### ⚙️ Configurações

#### 🌐 Web

- `/settings`

#### 📱 Mobile

- `Settings`

**Responsável por:**

- Gerenciamento de preferências do usuário
- Configurações gerais da aplicação

**Funcionalidades:**

- ✏️ Atualizar dados do usuário
- 🔐 Alterar senha
- 🔗 Gerenciar contas sociais (Google/GitHub)
- ⚙️ Preferências da aplicação

---

## 🧱 Layout da Aplicação

Define a estrutura visual e organizacional das telas da aplicação, separando o fluxo de autenticação do restante do sistema.

---

### 🌐 Web

```
/ (App Layout)
 ├── Sidebar        # Navegação principal
 ├── Header         # Ações globais e informações do usuário
 └── Content        # Área dinâmica (renderização das páginas)
```

**Características:**

- Layout persistente entre páginas
- Navegação lateral fixa (Sidebar)
- Header com ações rápidas e contexto

**Rotas que utilizam o layout:**

- `/dashboard`
- `/projects`
- `/settings`

📌 Rotas públicas (`/signin`, `/signup`) utilizam layout independente

---

### 📱 Mobile

```
Stack (Auth)
 ├── SignIn
 └── SignUp

Stack (App)
 ├── Tabs
 │    ├── Dashboard
 │    ├── Projects
 │    └── Settings
 ├── ProjectDetail
 │    ├── StatusList
 │    ├── StatusCreate
 │    └── StatusEdit
 ├── TaskCreate
 ├── TaskDetail
 └── TaskEdit
```

**Características:**

- Separação entre fluxo de autenticação e aplicação
- Navegação principal baseada em abas (Tabs)
- Uso de Stack para telas secundárias (tarefas e status)
- Status vinculados ao contexto do projeto

**Comportamento:**

- Usuário não autenticado → Stack (Auth)
- Usuário autenticado → Stack (App)

---

## 🖼️ Wireframes

> ⚠️ Os wireframes apresentados foram gerados com auxílio de Inteligência Artificial e têm como objetivo servir como base conceitual para o design da aplicação. As interfaces finais podem sofrer alterações durante o desenvolvimento.

Abaixo estão os wireframes utilizados para definir a estrutura e experiência do sistema, organizados por plataforma e fluxo de usuário.

---

### 🌐 Versão Web

#### 🔐 Autenticação

##### 🔑 Sign In

📌 Wireframe: `/wireframes/web/tela-signin.png`

- Campo de e-mail e senha
- Botão de login
- Opção de login com Google e GitHub (futuro)
- Link para cadastro

---

##### 🆕 Sign Up

📌 Wireframe: `/wireframes/web/tela-signup.png`

- Campos de cadastro (nome, e-mail, senha e confirmação de senha)
- Botão de criar conta
- Opção de cadastro com Google e GitHub (futuro)

---

#### 📁 Projetos

##### 📂 Lista de Projetos

📌 Wireframe: `/wireframes/web/tela-projetos.png`

- Lista de projetos do usuário
- Botão para criar novo projeto
- Acesso rápido aos projetos

---

##### ➕ Criar / Editar Projeto (Modal)

📌 Wireframe: `/wireframes/web/modal-criar-editar-projeto.png`

- Formulário em modal com campos para nome e descrição
- Seleção de cor ou identificação visual (opcional)
- Botões de salvar e cancelar

---

#### 📋 Dashboard e Tarefas

##### 📋 Dashboard

📌 Wireframe: `/wireframes/web/tela-dashboard.png`

- Navegação lateral (sidebar)
- Barra superior com ações
- Lista de tarefas com ações rápidas

---

##### ➕ Criar / Editar Tarefa (Modal)

📌 Wireframe: `/wireframes/web/modal-criar-editar-task.png`

- Formulário em modal
- Campos para título, descrição e prioridade

---

##### 🔍 Detalhes da Tarefa

📌 Wireframe: `/wireframes/web/modal-detalhes-tarefa.png`

- Visualização completa da tarefa
- Ações de editar e excluir

---

#### ⚙️ Configurações

📌 Wireframe: `/wireframes/web/tela-configuracoes.png`

- Preferências do sistema
- Configurações de tema e comportamento

---

### 📱 Versão Mobile

#### 🔐 Autenticação

##### 🔑 Sign In

📌 Wireframe: `/wireframes/mobile/tela-signin.png`

- Campo de e-mail e senha
- Botão de login e link para cadastro

---

##### 🆕 Sign Up

📌 Wireframe: `/wireframes/mobile/tela-signup.png`

- Campos de cadastro e botão de criar conta
- Navegação simples

---

#### 📁 Projetos

##### 📂 Lista de Projetos

📌 Wireframe: `/wireframes/mobile/tela-projetos.png`

- Lista vertical de projetos
- Botão de criar projeto

---

##### ➕ Criar / Editar Projeto

📌 Wireframe: `/wireframes/mobile/tela-criar-editar-projeto.png`

- Tela dedicada para criação/edição
- Campos de nome, descrição e seleção de cor
- Botão de salvar e navegação simples (voltar/cancelar)

---

#### 📋 Dashboard e Tarefas

##### 📋 Dashboard

📌 Wireframe: `/wireframes/mobile/tela-dashboard.png`

- Lista vertical de tarefas
- Botão de ação flutuante (+)

---

##### ➕ Criar / Editar Tarefa

📌 Wireframe: `/wireframes/mobile/tela-criar-editar-tarefa.png`

- Tela dedicada para criação/edição
- Inputs otimizados para mobile

---

##### 🔍 Detalhes da Tarefa

📌 Wireframe: `/wireframes/mobile/tela-detalhes-tarefa.png`

- Visualização simplificada
- Ações rápidas

---

#### ⚙️ Configurações

📌 Wireframe: `/wireframes/mobile/tela-configuracoes.png`

- Preferências do usuário
- Ajustes do aplicativo

---

## 📊 Diagramas

### 📌 Diagrama de Casos de Uso

#### Diagrama de Autenticação

```mermaid id="seq-authentication"
graph TD

    User[👤 Usuário]

    %% Autenticação
    subgraph AUTH[🔐 Autenticação]
        Register[🆕 Criar Conta]
        Login[🔐 Realizar Login]
        SocialLogin[🔗 Login com Google/GitHub]
        Authenticated[🔓 Usuário Autenticado]
    end

    User --> Register
    User --> Login
    User --> SocialLogin

    Register --> Authenticated
    Login --> Authenticated
    SocialLogin --> Authenticated
```

#### Diagrama de Funcionalidades da aplicação

```mermaid id="seq-app-functions"
graph TD

    Authenticated[🔓 Usuário Autenticado]

    %% Projetos
    subgraph PROJECTS[📁 Projetos]
        ViewProjects[📂 Visualizar Projetos]
        CreateProject[➕ Criar Projeto]
        EditProject[✏️ Editar Projeto]
        DeleteProject[🗑️ Excluir Projeto]
    end

     %% Status (por projeto)
    subgraph PROJECT_STATUS[📊 Status]
        CreateStatus[➕ Criar Status]
        EditStatus[✏️ Editar Status]
        DeleteStatus[🗑️ Excluir Status]
    end

    %% Tarefas
    subgraph TASKS[📋 Tarefas]
        ViewTasks[📋 Visualizar Tarefas]
        CreateTask[➕ Criar Tarefa]
        EditTask[✏️ Editar Tarefa]
        DeleteTask[🗑️ Excluir Tarefa]
        ChangeStatus[🔄 Alterar Status]
        FilterTasks[🔍 Filtrar Tarefas]
        SortTasks[↕️ Ordenar Tarefas]
        SetPriority[⚡ Definir Prioridade]
    end

    %% Configurações
    subgraph SETTINGS[⚙️ Configurações]
        Settings[⚙️ Gerenciar Configurações]
    end

    %% Relações principais
    Authenticated --> ViewProjects
    Authenticated --> CreateProject
    Authenticated --> EditProject
    Authenticated --> DeleteProject

    Authenticated --> ViewTasks
    Authenticated --> CreateTask
    Authenticated --> EditTask
    Authenticated --> DeleteTask
    Authenticated --> ChangeStatus
    Authenticated --> SetPriority

    Authenticated --> CreateStatus
    Authenticated --> EditStatus
    Authenticated --> DeleteStatus

    ViewTasks --> FilterTasks
    ViewTasks --> SortTasks

    Authenticated --> Settings

    %% Relação de projeto com status
    CreateProject --> CreateStatus
    CreateProject --> EditStatus
    CreateProject --> DeleteStatus

    %% Relação de status com tarefas
    CreateStatus --> ChangeStatus
    EditStatus --> ChangeStatus
    DeleteStatus --> ChangeStatus
```

---

### 🔄 Diagramas de Sequência

#### Login (Email e Senha)

```mermaid id="seq-login-basic"
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend
    participant API as ⚙️ Backend (FastAPI)
    participant DB as 🗄️ Banco de Dados

    %% 1. Preencher credenciais
    U->>FE: Digita email e senha
    FE->>API: POST /login (email, senha)

    %% 2. Buscar usuário
    API->>DB: Buscar usuário por email

    alt Usuário encontrado
        DB-->>API: Retorna dados do usuário

        %% 3. Verificar senha
        API->>API: Verificar hash da senha

        alt Senha correta
            %% 4. Gerar token
            API->>API: Gerar JWT
            API-->>FE: Retorna token

            %% 5. Armazenar token
            FE->>FE: Armazenar token (localStorage / secure storage)
            FE-->>U: Login realizado com sucesso
        else Senha incorreta
            API-->>FE: 401 Unauthorized
            FE-->>U: Exibir erro de login
        end

    else Usuário não encontrado
        DB-->>API: null
        API-->>FE: 404 / 401
        FE-->>U: Usuário inválido
    end
```

#### Cadastro (Sign Up)

```mermaid id="seq-signup-basic"
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend
    participant API as ⚙️ Backend (FastAPI)
    participant DB as 🗄️ Banco de Dados

    %% 1. Preencher dados do usuário
    U->>FE: Digita nome, email e senha
    FE->>API: POST /register (dados do usuário)

    %% 2. Validar dados no backend
    API->>API: Validar formato de dados e senha

    alt Dados válidos
        %% 3. Verificar se email já existe
        API->>DB: Buscar usuário por email

        alt Email já cadastrado
            DB-->>API: Usuário existente
            API-->>FE: 409 Conflict
            FE-->>U: Exibir erro (email já em uso)
        else Email disponível
            %% 4. Criar usuário
            API->>API: Gerar hash da senha
            API->>DB: Inserir novo usuário
            DB-->>API: Usuário criado

            %% 5. Gerar token JWT
            API->>API: Gerar JWT
            API-->>FE: Retorna token

            %% 6. Armazenar token e autenticar
            FE->>FE: Armazenar token
            FE-->>U: Cadastro realizado e usuário autenticado
        end

    else Dados inválidos
        API-->>FE: 400 Bad Request
        FE-->>U: Exibir erros de validação
    end
```

#### Login/Cadastro com Google/GitHub

```mermaid id="seq-social-auth"
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend
    participant OAUTH as 🔗 Google/GitHub
    participant API as ⚙️ Backend (FastAPI)
    participant DB as 🗄️ Banco de Dados

    %% 1. Usuário inicia login social
    U->>FE: Clica em "Continuar com Google/GitHub"
    FE->>OAUTH: Redireciona para autenticação

    %% 2. Retorno do OAuth
    OAUTH-->>FE: Retorna código/token OAuth
    FE->>API: Envia token OAuth

    %% 3. Validação do token no backend
    API->>OAUTH: Validar token

    alt Token válido
        OAUTH-->>API: Dados do usuário (email, nome)

        %% 4. Verificar se usuário já existe
        API->>DB: Buscar usuário por email

        alt Usuário já existe
            DB-->>API: Usuário encontrado
        else Novo usuário
            %% 5. Criar usuário automaticamente
            API->>DB: Inserir novo usuário
            DB-->>API: Usuário criado
        end

        %% 6. Gerar token JWT
        API->>API: Gerar JWT
        API-->>FE: Retorna token

        %% 7. Armazenar token e autenticar
        FE->>FE: Armazenar token
        FE-->>U: Login realizado com sucesso

    else Token inválido
        OAUTH-->>API: Erro de validação
        API-->>FE: 401 Unauthorized
        FE-->>U: Exibir erro de autenticação
    end
```

#### Projetos (CRUD Completo)

```mermaid id="seq-projects-crud"
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend
    participant API as ⚙️ Backend (FastAPI)
    participant DB as 🗄️ Banco de Dados

    %% 1. Listar projetos
    U->>FE: Acessa tela de projetos
    FE->>API: GET /projects (JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Buscar projetos do usuário
        DB-->>API: Lista de projetos
        API-->>FE: Retorna projetos
        FE-->>U: Exibir lista
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end

    %% 2. Criar projeto
    U->>FE: Clica em "Novo Projeto"
    FE->>U: Exibe formulário
    U->>FE: Preenche nome e descrição
    FE->>API: POST /projects (dados + JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>API: Validar dados
        alt Dados válidos
            API->>DB: Inserir projeto
            DB-->>API: Projeto criado
            API-->>FE: Retorna projeto
            FE-->>U: Atualizar lista
        else Dados inválidos
            API-->>FE: 400 Bad Request
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end

    %% 3. Editar projeto
    U->>FE: Clica em "Editar Projeto"
    FE->>U: Exibe formulário com dados atuais
    U->>FE: Atualiza informações
    FE->>API: PUT /projects/{id} (dados + JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Verificar projeto do usuário
        alt Projeto encontrado
            API->>API: Validar dados
            alt Dados válidos
                API->>DB: Atualizar projeto
                DB-->>API: Projeto atualizado
                API-->>FE: Retorna projeto atualizado
                FE-->>U: Atualizar lista
            else Dados inválidos
                API-->>FE: 400 Bad Request
                FE-->>U: Exibir erro
            end
        else Projeto não encontrado
            API-->>FE: 404 Not Found
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end

    %% 4. Excluir projeto
    U->>FE: Clica em "Excluir Projeto"
    FE->>U: Solicita confirmação
    U->>FE: Confirma exclusão
    FE->>API: DELETE /projects/{id} (JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Verificar projeto do usuário
        alt Projeto encontrado
            API->>DB: Remover projeto
            DB-->>API: Projeto removido
            API-->>FE: Sucesso
            FE-->>U: Atualizar lista
        else Projeto não encontrado
            API-->>FE: 404 Not Found
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end
```

#### Status (CRUD Completo)

```mermaid id="seq-tasks-crud"
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend
    participant API as ⚙️ Backend (FastAPI)
    participant DB as 🗄️ Banco de Dados

    %% 1. Listar status do projeto
    U->>FE: Acessa tela de status do projeto
    FE->>API: GET /projects/{projectId}/status (JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Buscar status do projeto
        DB-->>API: Lista de status
        API-->>FE: Retorna status
        FE-->>U: Exibir lista
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end

    %% 2. Criar status
    U->>FE: Clica em "Novo Status"
    FE->>U: Exibe formulário
    U->>FE: Preenche nome, ordem e cor
    FE->>API: POST /projects/{projectId}/status (dados + JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>API: Validar dados
        alt Dados válidos
            API->>DB: Inserir status
            DB-->>API: Status criado
            API-->>FE: Retorna status
            FE-->>U: Atualizar lista
        else Dados inválidos
            API-->>FE: 400 Bad Request
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end

    %% 3. Editar status
    U->>FE: Clica em "Editar Status"
    FE->>U: Exibe formulário com dados atuais
    U->>FE: Atualiza nome, ordem ou cor
    FE->>API: PUT /projects/{projectId}/status/{statusId} (dados + JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Verificar status do projeto
        alt Status encontrado
            API->>API: Validar dados
            alt Dados válidos
                API->>DB: Atualizar status
                DB-->>API: Status atualizado
                API-->>FE: Retorna status atualizado
                FE-->>U: Atualizar lista
            else Dados inválidos
                API-->>FE: 400 Bad Request
                FE-->>U: Exibir erro
            end
        else Status não encontrado
            API-->>FE: 404 Not Found
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end

    %% 4. Excluir status
    U->>FE: Clica em "Excluir Status"
    FE->>U: Solicita confirmação
    U->>FE: Confirma exclusão
    FE->>API: DELETE /projects/{projectId}/status/{statusId} (JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Verificar status do projeto
        alt Status encontrado
            API->>DB: Remover status
            DB-->>API: Status removido
            API-->>FE: Sucesso
            FE-->>U: Atualizar lista
        else Status não encontrado
            API-->>FE: 404 Not Found
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end
```

#### Tarefas (CRUD Completo)

```mermaid id="seq-tasks-crud"
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend
    participant API as ⚙️ Backend (FastAPI)
    participant DB as 🗄️ Banco de Dados

    %% 1. Listar tarefas
    U->>FE: Acessa dashboard / projeto
    FE->>API: GET /tasks?project_id (JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Buscar tarefas do projeto (usuário)
        DB-->>API: Lista de tarefas
        API-->>FE: Retorna tarefas
        FE-->>U: Exibir lista
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end

    %% 2. Criar tarefa
    U->>FE: Clica em "Nova Tarefa"
    FE->>U: Exibe formulário
    U->>FE: Preenche título, descrição, prioridade
    FE->>API: POST /tasks (dados + JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>API: Validar dados
        alt Dados válidos
            API->>DB: Inserir tarefa
            DB-->>API: Tarefa criada
            API-->>FE: Retorna tarefa
            FE-->>U: Atualizar lista
        else Dados inválidos
            API-->>FE: 400 Bad Request
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end

    %% 3. Editar tarefa
    U->>FE: Clica em "Editar Tarefa"
    FE->>U: Exibe formulário com dados atuais
    U->>FE: Atualiza informações
    FE->>API: PUT /tasks/{id} (dados + JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Verificar tarefa do usuário
        alt Tarefa encontrada
            API->>API: Validar dados
            alt Dados válidos
                API->>DB: Atualizar tarefa
                DB-->>API: Tarefa atualizada
                API-->>FE: Retorna tarefa atualizada
                FE-->>U: Atualizar lista
            else Dados inválidos
                API-->>FE: 400 Bad Request
                FE-->>U: Exibir erro
            end
        else Tarefa não encontrada
            API-->>FE: 404 Not Found
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end

    %% 4. Alterar status da tarefa
    U->>FE: Seleciona novo status (personalizado)
    FE->>API: PATCH /tasks/{id}/status (status + JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Verificar tarefa do usuário
        alt Tarefa encontrada
            API->>DB: Atualizar status
            DB-->>API: Tarefa atualizada
            API-->>FE: Retorna tarefa atualizada
            FE-->>U: Atualizar status na tela
        else Tarefa não encontrada
            API-->>FE: 404 Not Found
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end

    %% 5. Definir prioridade
    U->>FE: Altera prioridade da tarefa
    FE->>API: PATCH /tasks/{id}/priority (prioridade + JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Atualizar prioridade
        DB-->>API: Tarefa atualizada
        API-->>FE: Retorna tarefa atualizada
        FE-->>U: Atualizar prioridade na tela
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end

    %% 6. Excluir tarefa
    U->>FE: Clica em "Excluir Tarefa"
    FE->>U: Solicita confirmação
    U->>FE: Confirma exclusão
    FE->>API: DELETE /tasks/{id} (JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Verificar tarefa do usuário
        alt Tarefa encontrada
            API->>DB: Remover tarefa
            DB-->>API: Tarefa removida
            API-->>FE: Sucesso
            FE-->>U: Atualizar lista
        else Tarefa não encontrada
            API-->>FE: 404 Not Found
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end
```

### Diagramas de Estados

#### Autenticação

```mermaid id="seq-state-auth"
stateDiagram-v2
  direction LR
  Nao_Autenticado : Não Autenticado
  Falha_Autenticacao : Falha Autenticação

  [*] --> Nao_Autenticado

  Nao_Autenticado --> Autenticando : Iniciar Login / Cadastro / SocialLogin
  Autenticando --> Autenticado : Sucesso
  Autenticando --> Falha_Autenticacao : Erro

  Autenticado --> Autenticado : Acessar sistema

  Falha_Autenticacao --> Nao_Autenticado : Tentar novamente
```

- Descrição do Diagrama:
  - Não Autenticado: Estado inicial do usuário antes de realizar qualquer ação de login.
  - Autenticando: Estado temporário enquanto o sistema processa o login, cadastro ou autenticação social.
  - Autenticado: Estado final quando o usuário realiza login com sucesso.
  - Falha Autenticação: Estado que indica que ocorreu um erro no login, senha incorreta ou falha na autenticação social.
- Transições:
  - O usuário passa de Não Autenticado para Autenticando ao iniciar qualquer processo de autenticação.
  - Se o processo for bem-sucedido, vai para Autenticado.
  - Se houver erro, vai para Falha Autenticação, que permite tentar novamente voltando a Não Autenticado.

#### Projetos

```mermaid id="seq-state-project"
stateDiagram-v2
  direction LR
  Nao_Criado : Projeto Não Criado
  Projeto_Criado : Projeto Criado
  Criando_Projeto : Criando Projeto
  Editando_Projeto : Editando Projeto
  Excluindo_Projeto : Excluindo Projeto
  Falha_Projeto : Falha na operação (CRUD)

  [*] --> Nao_Criado

  Nao_Criado --> Criando_Projeto : Iniciar criação
  Criando_Projeto --> Projeto_Criado : Sucesso
  Criando_Projeto --> Falha_Projeto : Erro

  Projeto_Criado --> Projeto_Criado : Visualizar / Listar
  Projeto_Criado --> Editando_Projeto : Iniciar edição
  Editando_Projeto --> Projeto_Criado : Sucesso
  Editando_Projeto --> Falha_Projeto : Erro

  Projeto_Criado --> Excluindo_Projeto : Iniciar exclusão
  Excluindo_Projeto --> Nao_Criado : Sucesso
  Excluindo_Projeto --> Falha_Projeto : Erro

  Falha_Projeto --> Nao_Criado : Tentar novamente
```

- Descrição do Diagrama:
  - Não Criado: Estado inicial, nenhum projeto existe.
  - Criando Projeto / Editando Projeto / Excluindo Projeto: Estados temporários durante a operação.
  - Projeto Criado: Projeto existente e disponível para ações.
  - Falha na operação (CRUD): Indica erro em qualquer operação de CRUD.
- Transições:
  - Permitem tentar novamente após falha ou avançar em caso de sucesso.

#### Status do Projeto

```mermaid id="seq-state-project-status"
stateDiagram-v2
  direction LR
  Nao_Criado : Status Não Criado
  Status_Criado : Status Criado
  Criando_Status : Criando Status
  Editando_Status : Editando Status
  Excluindo_Status : Excluindo Status
  Falha_Status : Falha na operação (CRUD)

  [*] --> Nao_Criado

  Nao_Criado --> Criando_Status : Iniciar criação
  Criando_Status --> Status_Criado : Sucesso
  Criando_Status --> Falha_Status : Erro

  Status_Criado --> Status_Criado : Visualizar / Listar
  Status_Criado --> Editando_Status : Iniciar edição
  Editando_Status --> Status_Criado : Sucesso
  Editando_Status --> Falha_Status : Erro

  Status_Criado --> Excluindo_Status : Iniciar exclusão
  Excluindo_Status --> Nao_Criado : Sucesso
  Excluindo_Status --> Falha_Status : Erro

  Falha_Status --> Nao_Criado : Tentar novamente
```

- Descrição do Diagrama:
  - Não Criado: Estado inicial, nenhum status existe no projeto.
  - Criando Status / Editando Status / Excluindo Status: Estados temporários enquanto a ação é processada.
  - Status Criado: Status disponível no projeto.
  - Falha na operação (CRUD): Indica erro durante qualquer operação de CRUD.

- Transições:
  - Sempre permitem voltar a tentar após falha, ou avançar em caso de sucesso.

#### Tarefas

```mermaid id="seq-state-task"
stateDiagram-v2
  direction LR
  Nao_Criada : Tarefa Não Criada
  Tarefa_Criada : Tarefa Criada
  Criando_Tarefa : Criando Tarefa
  Editando_Tarefa : Editando Tarefa
  Excluindo_Tarefa : Excluindo Tarefa
  Alterando_Status : Alterando Status
  Definindo_Prioridade : Definindo Prioridade
  Falha_Tarefa : Falha na operação (CRUD)

  [*] --> Nao_Criada

  Nao_Criada --> Criando_Tarefa : Iniciar criação
  Criando_Tarefa --> Tarefa_Criada : Sucesso
  Criando_Tarefa --> Falha_Tarefa : Erro

  Tarefa_Criada --> Tarefa_Criada : Visualizar / Listar
  Tarefa_Criada --> Editando_Tarefa : Iniciar edição
  Editando_Tarefa --> Tarefa_Criada : Sucesso
  Editando_Tarefa --> Falha_Tarefa : Erro

  Tarefa_Criada --> Alterando_Status : Alterar status
  Alterando_Status --> Tarefa_Criada : Sucesso
  Alterando_Status --> Falha_Tarefa : Erro

  Tarefa_Criada --> Definindo_Prioridade : Alterar prioridade
  Definindo_Prioridade --> Tarefa_Criada : Sucesso
  Definindo_Prioridade --> Falha_Tarefa : Erro

  Tarefa_Criada --> Excluindo_Tarefa : Iniciar exclusão
  Excluindo_Tarefa --> Nao_Criada : Sucesso
  Excluindo_Tarefa --> Falha_Tarefa : Erro

  Falha_Tarefa --> Nao_Criada : Tentar novamente
```

- Descrição do Diagrama:
  - Não Criada: Estado inicial, nenhuma tarefa existe.
  - Criando / Editando / Alterando Status / Definindo Prioridade / Excluindo: Estados temporários de operação.
  - Tarefa Criada: Tarefa existente pronta para qualquer ação.
  - Falha na operação (CRUD): Indica erro em qualquer operação de CRUD ou alteração.
- Transições:
  - Permitem avançar em caso de sucesso ou tentar novamente após falha.

## 🧩 Tecnologias

### 🎨 Frontend (Web)

- React
- TypeScript
- Vite

### 📱 Mobile

- React Native

### ⚙️ Backend

- Python (FastAPI)

### 🗄️ Database

- PostgreSQL

### 🔧 Arquitetura e Ferramentas

- API REST
- JWT (autenticação)
- Context API / Zustand (estado)

---

## 🚀 Roadmap

### 🔐 Autenticação

- [ ] Login
- [ ] Cadastro
- [ ] Validação de formulário
- [ ] Sessão de usuário

---

### 📁 Projetos

- [ ] Criar projeto
- [ ] Editar projeto
- [ ] Excluir projeto
- [ ] Listar projetos
- [ ] Filtros
- [ ] Ordenação

---

### 📋 Tarefas

- [ ] CRUD completo
- [ ] Filtros
- [ ] Ordenação
- [ ] Prioridades
- [ ] Vincular a projetos

---

### ⚙️ Configurações

- [ ] Tema (light/dark)
- [ ] Preferências do usuário
- [ ] Conta

---

## 💡 Melhorias Futuras

- Login com Google
- Login com GitHub
- Notificações em tempo real
- Drag and drop
- Modo offline
- Sincronização entre dispositivos
- Compartilhamento de projetos
- Integração com calendário

---

## 📄 Licença

Este projeto está sob a licença **MIT**.

---

## 👨‍💻 Autor

Desenvolvido por **Kevyn Aparecido**
