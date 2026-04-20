Voltar para [Colunas (por projeto)](../index.md)

---

[Início](../../../../../README.md) | [📊 Diagramas](../../../index.md) | [🔄 Diagramas de Sequência](../../index.md) | [Colunas (por projeto)](../index.md) | Listar colunas de status

---

## Listar colunas de status

```mermaid
sequenceDiagram
    autonumber
    participant U as 👤 Usuário
    participant FE as 🌐 Frontend(Navegador/Aplicativo)
    participant API as ⚙️ Backend
    participant DB as 🗄️ Banco de Dados

    U->>FE: Acessa tela de colunas do projeto
    FE->>API: GET /projects/{projectId}/columns (JWT)
    API->>API: Validar JWT

    alt Token válido
        API->>DB: Buscar colunas do projeto
        DB-->>API: Lista de colunas
        API-->>FE: Retorna colunas
        FE-->>U: Exibir lista
    else Token inválido
        API-->>FE: 401 Unauthorized
        FE-->>U: Redirecionar para login
    end
```
