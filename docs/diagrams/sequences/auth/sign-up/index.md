Voltar para [Autenticação](../index.md)

---

[Início](../../../../../README.md) | [📊 Diagramas](../../../index.md) | [🔄 Diagramas de Sequência](../../index.md) | [Autenticação](../index.md) | Cadastro (Sign Up)

---

## Cadastro (Sign Up)

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
