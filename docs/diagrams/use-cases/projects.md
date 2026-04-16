← [Voltar para Casos de Uso](./README.md)

---

[Início](../../../README.md) / [Diagramas](../README.md) / [Casos de Uso](./README.md) / Projetos

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
