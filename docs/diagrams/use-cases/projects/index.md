Voltar para [📌 Diagrama de Casos de Uso](../index.md)

---

[Início](../../../../README.md) | [📊 Diagramas](../../index.md) | [📌 Diagrama de Casos de Uso](../index.md) | Projetos

---

## Projetos

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
