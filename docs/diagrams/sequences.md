← Voltar para [Diagramas](../diagrams.md)

## 🔄 Diagramas de Sequência

### Login (Email e Senha)

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

### Cadastro (Sign Up)

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

### Login/Cadastro com Google/GitHub

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

### Projetos (CRUD Completo)

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

### Status (CRUD Completo)

```mermaid id="seq-project-status-crud"
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

### Tarefas (CRUD Completo)

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
