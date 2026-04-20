Voltar para [🧠 Diagramas de Estados](../index.md)

---

[Início](../../../../README.md) | [📊 Diagramas](../../index.md) | [🧠 Diagramas de Estados](../index.md) | Projetos

---

## Projetos

```mermaid
stateDiagram-v2
  direction LR
  Nao_Criado : Projeto Não Criado
  Projeto_Criado : Projeto Criado
  Criando_Projeto : Criando Projeto
  Editando_Projeto : Editando Projeto
  Excluindo_Projeto : Excluindo Projeto
  Falha_Projeto : Falha na operação (CRUD)

  [*] --> Nao_Criado

  Nao_Criado --> Criando_Projeto : Iniciar criação
  Criando_Projeto --> Projeto_Criado : Sucesso
  Criando_Projeto --> Falha_Projeto : Erro

  Projeto_Criado --> Projeto_Criado : Visualizar / Listar
  Projeto_Criado --> Editando_Projeto : Iniciar edição
  Editando_Projeto --> Projeto_Criado : Sucesso
  Editando_Projeto --> Falha_Projeto : Erro

  Projeto_Criado --> Excluindo_Projeto : Iniciar exclusão
  Excluindo_Projeto --> Nao_Criado : Sucesso
  Excluindo_Projeto --> Falha_Projeto : Erro

  Falha_Projeto --> Nao_Criado : Tentar novamente
```

- Descrição do Diagrama:
  - Não Criado: Estado inicial, nenhum projeto existe.
  - Criando Projeto / Editando Projeto / Excluindo Projeto: Estados temporários durante a operação.
  - Projeto Criado: Projeto existente e disponível para ações.
  - Falha na operação (CRUD): Indica erro em qualquer operação de CRUD.
- Transições:
  - Permitem tentar novamente após falha ou avançar em caso de sucesso.
