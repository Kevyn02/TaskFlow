Voltar para [Configurações](../index.md)

---

[Início](../../../../../README.md) | [📊 Diagramas](../../../index.md) | [🔄 Diagramas de Sequência](../../index.md) | [Configurações](../index.md) | Atualizar perfil

---

## Atualizar perfil

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
