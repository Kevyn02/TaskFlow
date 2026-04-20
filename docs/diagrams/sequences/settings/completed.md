Voltar para [🔄 Diagramas de Sequência](../index.md)

---

[Início](../../../../README.md) | [📊 Diagramas](../../index.md) | [🔄 Diagramas de Sequência](../index.md) | Configurações

---

## Configurações

### Atualizar perfil

```mermaid
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend(Navegador/Aplicativo)
    participant API as ⚙️ Backend
    participant DB as 🗄️ Banco de Dados

    U->>FE: Acessa "Meu Perfil"
    FE->>API: GET /profile (JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Buscar dados do usuário
        DB-->>API: Dados do perfil
        API-->>FE: Retorna dados
        FE-->>U: Exibe formulário preenchido

        U->>FE: Edita dados (nome, email, etc)
        FE->>API: PUT /profile (dados + JWT)
        API->>API: Validar JWT

        alt Token válido
            API->>API: Validar dados

            alt Dados válidos
                API->>DB: Atualizar perfil
                DB-->>API: Confirma atualização
                API-->>FE: Retorna dados atualizados
                FE-->>U: Exibe sucesso
            else Dados inválidos
                API-->>FE: 400 Bad Request
                FE-->>U: Exibir erro
            end

        else Token inválido
            API-->>FE: 401 Unauthorized
            FE-->>U: Redirecionar para login
        end

    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end
```

### Trocar senha

```mermaid
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend(Navegador/Aplicativo)
    participant API as ⚙️ Backend
    participant DB as 🗄️ Banco de Dados

    U->>FE: Acessa "Alterar Senha"
    FE->>U: Exibe formulário

    U->>FE: Preenche senha atual + nova senha
    FE->>API: PUT /change-password (dados + JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Buscar usuário
        DB-->>API: Dados do usuário (hash senha)

        API->>API: Comparar senha atual (hash)

        alt Senha atual correta
            API->>API: Validar nova senha

            alt Nova senha válida
                API->>API: Gerar hash da nova senha
                API->>DB: Atualizar senha
                DB-->>API: Confirma atualização

                API-->>FE: 200 OK
                FE-->>U: Exibe sucesso

            else Nova senha inválida
                API-->>FE: 400 Bad Request
                FE-->>U: Exibir erro
            end

        else Senha atual incorreta
            API-->>FE: 401 Unauthorized
            FE-->>U: Exibir erro
        end

    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end
```
