Voltar para [Colunas (por projeto)](../index.md)

---

[Início](../../../../../README.md) | [📊 Diagramas](../../../index.md) | [🔄 Diagramas de Sequência](../../index.md) | [Colunas (por projeto)](../index.md) | Editar coluna de status

---

## Editar coluna de status

```mermaid
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend(Navegador/Aplicativo)
    participant API as ⚙️ Backend
    participant DB as 🗄️ Banco de Dados

    U->>FE: Clica em "Editar Coluna"
    FE->>U: Exibe formulário com dados atuais
    U->>FE: Atualiza nome, ordem ou cor
    FE->>API: PUT /projects/{projectId}/columns/{columnId} (dados + JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Verificar coluna do projeto
        alt Coluna encontrada
            API->>API: Validar dados
            alt Dados válidos
                API->>DB: Atualizar coluna
                DB-->>API: Coluna atualizada
                API-->>FE: Retorna coluna atualizada
                FE-->>U: Atualizar lista
            else Dados inválidos
                API-->>FE: 400 Bad Request
                FE-->>U: Exibir erro
            end
        else Coluna não encontrada
            API-->>FE: 404 Not Found
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end
```
