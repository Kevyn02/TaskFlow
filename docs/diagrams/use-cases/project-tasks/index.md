Voltar para [📌 Diagrama de Casos de Uso](../index.md)

---

[Início](../../../../README.md) | [📊 Diagramas](../../index.md) | [📌 Diagrama de Casos de Uso](../index.md) | Tarefas (por projeto)

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
