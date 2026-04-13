← Voltar para [Diagramas](../diagrams.md)

## 🧠 Diagramas de Estados

### Autenticação

```mermaid id="seq-state-auth"
stateDiagram-v2
  direction LR
  Nao_Autenticado : Não Autenticado
  Falha_Autenticacao : Falha Autenticação

  [*] --> Nao_Autenticado

  Nao_Autenticado --> Autenticando : Iniciar Login / Cadastro / SocialLogin
  Autenticando --> Autenticado : Sucesso
  Autenticando --> Falha_Autenticacao : Erro

  Autenticado --> Autenticado : Acessar sistema

  Falha_Autenticacao --> Nao_Autenticado : Tentar novamente
```

- Descrição do Diagrama:
  - Não Autenticado: Estado inicial do usuário antes de realizar qualquer ação de login.
  - Autenticando: Estado temporário enquanto o sistema processa o login, cadastro ou autenticação social.
  - Autenticado: Estado final quando o usuário realiza login com sucesso.
  - Falha Autenticação: Estado que indica que ocorreu um erro no login, senha incorreta ou falha na autenticação social.
- Transições:
  - O usuário passa de Não Autenticado para Autenticando ao iniciar qualquer processo de autenticação.
  - Se o processo for bem-sucedido, vai para Autenticado.
  - Se houver erro, vai para Falha Autenticação, que permite tentar novamente voltando a Não Autenticado.

### Projetos

```mermaid id="seq-state-project"
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

### Status do Projeto

```mermaid id="seq-state-project-status"
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

### Tarefas

```mermaid id="seq-state-task"
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
