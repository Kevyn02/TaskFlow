← Voltar para [Diagramas](../diagrams.md)

## 🧩 Diagrama ER (Entidade - Relacionamento)

### Diagrama ER — Usuários e Projetos

- Inclui users, projects, project_members, task_statuses
- Mostra quem criou/atualizou/desativou e membros do projeto

```mermaid id='seq-database-diagram-er-users-projects'
erDiagram
    "Usuarios (users)" ||--o{ "Projetos (projects)" : "created_by"
    "Usuarios (users)" ||--o{ "Membros_projeto (project_members)" : "user_id"
    "Usuarios (users)" ||--o{ "Status_tarefas (task_statuses)" : "created_by"

    "Projetos (projects)" ||--o{ "Membros_projeto (project_members)" : "project_id"
    "Projetos (projects)" ||--o{ "Status_tarefas (task_statuses)" : "project_id"
```

💡 Comentário:
Esse diagrama mostra estrutura de projetos e usuários, incluindo membros e status das tarefas vinculados ao projeto.

### Diagrama ER — Tarefas e Membros

- Inclui tasks, task_statuses, task_assignees
- Mostra status, tarefas e quais usuários estão atribuídos

```mermaid id='seq-database-diagram-er-tasks-assignees'
erDiagram
    "Usuarios (users)" ||--o{ "Tarefas (tasks)" : "created_by"
    "Usuarios (users)" ||--o{ "Membros_tarefa (task_assignees)" : "user_id"

    "Status_tarefas (task_statuses)" ||--o{ "Tarefas (tasks)" : "status_id"
    "Tarefas (tasks)" ||--o{ "Membros_tarefa (task_assignees)" : "task_id"
```

💡 Comentário:
Esse diagrama mostra as tarefas e os usuários atribuídos, mantendo os status e relacionamentos visíveis.
