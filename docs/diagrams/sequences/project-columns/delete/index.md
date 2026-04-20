Voltar para [Colunas (por projeto)](../index.md)

---

[Início](../../../../../README.md) | [📊 Diagramas](../../../index.md) | [🔄 Diagramas de Sequência](../../index.md) | [Colunas (por projeto)](../index.md) | Excluir coluna de status

---

## Excluir coluna de status

```mermaid
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend(Navegador/Aplicativo)
    participant API as ⚙️ Backend
    participant DB as 🗄️ Banco de Dados

    U->>FE: Clica em "Excluir Coluna"
    FE->>U: Solicita confirmação
    U->>FE: Confirma exclusão
    FE->>API: DELETE /projects/{projectId}/columns/{columnId} (JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Verificar coluna do projeto
        alt Coluna encontrada
            API->>DB: Remover coluna
            DB-->>API: Coluna removida
            API-->>FE: Sucesso
            FE-->>U: Atualizar lista
        else Coluna não encontrada
            API-->>FE: 404 Not Found
            FE-->>U: Exibir erro
        end
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end
```
