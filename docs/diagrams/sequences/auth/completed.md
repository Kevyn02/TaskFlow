Voltar para [🔄 Diagramas de Sequência](../index.md)

---

[Início](../../../../README.md) | [📊 Diagramas](../../index.md) | [🔄 Diagramas de Sequência](../index.md) | Autenticação

---

## Autenticação

### Login (Email e Senha)

```mermaid
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend(Navegador/Aplicativo)
    participant API as ⚙️ Backend
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

```mermaid
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend(Navegador/Aplicativo)
    participant API as ⚙️ Backend
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

```mermaid
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend(Navegador/Aplicativo)
    participant OAUTH as 🔗 Google/GitHub
    participant API as ⚙️ Backend
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
