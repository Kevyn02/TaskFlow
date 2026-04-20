Voltar para [🧠 Diagramas de Estados](../index.md)

---

[Início](../../../../README.md) | [📊 Diagramas](../../index.md) | [🧠 Diagramas de Estados](../index.md) | Colunas (por projeto)

---

## Colunas (por projeto)

```mermaid
stateDiagram-v2
  direction LR
  Nao_Criado : Status Não Criado
  Status_Criado : Status Criado
  Criando_Status : Criando Status
  Editando_Status : Editando Status
  Excluindo_Status : Excluindo Status
  Falha_Status : Falha na operação (CRUD)

  [*] --> Nao_Criado

  Nao_Criado --> Criando_Status : Iniciar criação
  Criando_Status --> Status_Criado : Sucesso
  Criando_Status --> Falha_Status : Erro

  Status_Criado --> Status_Criado : Visualizar / Listar
  Status_Criado --> Editando_Status : Iniciar edição
  Editando_Status --> Status_Criado : Sucesso
  Editando_Status --> Falha_Status : Erro

  Status_Criado --> Excluindo_Status : Iniciar exclusão
  Excluindo_Status --> Nao_Criado : Sucesso
  Excluindo_Status --> Falha_Status : Erro

  Falha_Status --> Nao_Criado : Tentar novamente
```

- Descrição do Diagrama:
  - Não Criado: Estado inicial, nenhum status existe no projeto.
  - Criando Status / Editando Status / Excluindo Status: Estados temporários enquanto a ação é processada.
  - Status Criado: Status disponível no projeto.
  - Falha na operação (CRUD): Indica erro durante qualquer operação de CRUD.

- Transições:
  - Sempre permitem voltar a tentar após falha, ou avançar em caso de sucesso.
