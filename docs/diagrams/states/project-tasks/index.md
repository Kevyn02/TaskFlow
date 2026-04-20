Voltar para [🧠 Diagramas de Estados](../index.md)

---

[Início](../../../../README.md) | [📊 Diagramas](../../index.md) | [🧠 Diagramas de Estados](../index.md) | Tarefas (por projeto)

---

## Tarefas (por projeto)

```mermaid
stateDiagram-v2
  direction LR
  Nao_Criada : Tarefa Não Criada
  Tarefa_Criada : Tarefa Criada
  Criando_Tarefa : Criando Tarefa
  Editando_Tarefa : Editando Tarefa
  Excluindo_Tarefa : Excluindo Tarefa
  Alterando_Status : Alterando Status
  Definindo_Prioridade : Definindo Prioridade
  Falha_Tarefa : Falha na operação (CRUD)

  [*] --> Nao_Criada

  Nao_Criada --> Criando_Tarefa : Iniciar criação
  Criando_Tarefa --> Tarefa_Criada : Sucesso
  Criando_Tarefa --> Falha_Tarefa : Erro

  Tarefa_Criada --> Tarefa_Criada : Visualizar / Listar
  Tarefa_Criada --> Editando_Tarefa : Iniciar edição
  Editando_Tarefa --> Tarefa_Criada : Sucesso
  Editando_Tarefa --> Falha_Tarefa : Erro

  Tarefa_Criada --> Alterando_Status : Alterar status
  Alterando_Status --> Tarefa_Criada : Sucesso
  Alterando_Status --> Falha_Tarefa : Erro

  Tarefa_Criada --> Definindo_Prioridade : Alterar prioridade
  Definindo_Prioridade --> Tarefa_Criada : Sucesso
  Definindo_Prioridade --> Falha_Tarefa : Erro

  Tarefa_Criada --> Excluindo_Tarefa : Iniciar exclusão
  Excluindo_Tarefa --> Nao_Criada : Sucesso
  Excluindo_Tarefa --> Falha_Tarefa : Erro

  Falha_Tarefa --> Nao_Criada : Tentar novamente
```

- Descrição do Diagrama:
  - Não Criada: Estado inicial, nenhuma tarefa existe.
  - Criando / Editando / Alterando Status / Definindo Prioridade / Excluindo: Estados temporários de operação.
  - Tarefa Criada: Tarefa existente pronta para qualquer ação.
  - Falha na operação (CRUD): Indica erro em qualquer operação de CRUD ou alteração.
- Transições:
  - Permitem avançar em caso de sucesso ou tentar novamente após falha.
