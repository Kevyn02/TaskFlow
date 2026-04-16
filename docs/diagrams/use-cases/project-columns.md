← [Voltar para Casos de Uso](./README.md)

---

[Início](../../../README.md) / [Diagramas](../README.md) / [Casos de Uso](./README.md) / Colunas (por projeto)

---

## Colunas (por projeto)

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
