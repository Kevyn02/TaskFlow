← [Voltar para Casos de Uso](./README.md)

---

[Início](../../../README.md) / [Diagramas](../README.md) / [Casos de Uso](./README.md) / Tarefas (por projeto)

---

## Tarefas (por projeto)

```mermaid
graph TD

    User[👤 Usuário]

    subgraph PROJECT_TASKS["Tarefas (por projeto)"]
        subgraph ORGANIZATION[Organização]
            FilterProjectTasks((🔍 Filtrar))
            SortProjectTasks((↕️ Ordenar))
        end
        subgraph CRUD[Operações]
            ViewProjectTasks((💼 Listar))
            ViewDetailsProjectTask((📄 Visualizar detalhes))
            CreateProjectTask((➕ Criar))
            EditProjectTask((✏️ Editar))
            DeleteProjectTask((🗑️ Excluir))
        end
        subgraph ACTIONS[Ações]
            MoveProjectTask((🔄 Mover entre colunas))
            SetProjectTaskPriority((⚡ Alterar Prioridade))
        end
    end

    User --> FilterProjectTasks
    User --> SortProjectTasks
    User --> ViewProjectTasks
    User --> ViewDetailsProjectTask
    User --> CreateProjectTask
    User --> EditProjectTask
    User --> DeleteProjectTask
    User --> MoveProjectTask
    User --> SetProjectTaskPriority
```
