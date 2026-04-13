## 🧭 Arquitetura de Rotas

A aplicação é organizada em dois grupos principais: **rotas públicas** e **rotas privadas**, separando o fluxo de autenticação do restante do sistema.

---

### 🔓 Rotas Públicas

Acessíveis sem autenticação.

#### #🌐 Web

- `/signin`
- `/signup`

#### 📱 Mobile

- `SignInScreen`
- `SignUpScreen`

📌 Usuários autenticados são automaticamente redirecionados para `/dashboard`

---

### 🔐 Rotas Privadas

Acessíveis apenas para usuários autenticados.

---

#### 📋 Dashboard

##### 🌐 Web

- `/dashboard`

##### 📱 Mobile

- `Dashboard` (via Tabs)

**Responsável por:**

- Visualização geral das tarefas
- Ações rápidas

---

#### 📁 Projetos

##### 🌐 Web

- `/projects`
- `/projects/:projectId`

##### 📱 Mobile

- `Projects`
- `ProjectDetail`

**Responsável por:**

- Organização das tarefas por contexto
- Agrupamento por projeto

**Funcionalidades:**

- ➕ Criar projeto
- ✏️ Editar projeto
- 🗑️ Excluir projeto
- 📂 Visualizar projetos

---

#### 📋 Tarefas

##### 🌐 Web

- Gerenciadas via **modais** (sem rotas dedicadas)

##### 📱 Mobile

- `/tasks/create`
- `/tasks/:taskId`
- `/tasks/:taskId/edit`

**Responsável por:**

- Gerenciamento de tarefas
- Associação com projetos
- Controle de status e prioridade

**Funcionalidades:**

- ➕ Criar tarefa
- ✏️ Editar tarefa
- 🗑️ Excluir tarefa
- 🔄 Alterar status
- 🔍 Filtrar tarefas
- ↕️ Ordenar tarefas
- ⚡ Definir prioridade

---

#### 🧩 Status (por Projeto)

##### 🌐 Web

- Integrado à tela de projeto (`/projects/:projectId`)
- Gerenciado via modais

##### 📱 Mobile

- `/projects/:projectId/status`
- `/projects/:projectId/status/create`
- `/projects/:projectId/status/:statusId/edit`

**Responsável por:**

- Definição do fluxo de status das tarefas
- Personalização por projeto

**Funcionalidades:**

- ➕ Criar status
- ✏️ Editar status
- 🗑️ Remover status
- 🔢 Definir ordem do fluxo
- 🎨 Definir cor
- 📝 Definir nome

📌 Cada projeto possui seu próprio fluxo de status
📌 Utilizado para controlar o ciclo de vida das tarefas

---

#### ⚙️ Configurações

##### 🌐 Web

- `/settings`

##### 📱 Mobile

- `Settings`

**Responsável por:**

- Gerenciamento de preferências do usuário
- Configurações gerais da aplicação

**Funcionalidades:**

- ✏️ Atualizar dados do usuário
- 🔐 Alterar senha
- 🔗 Gerenciar contas sociais (Google/GitHub)
- ⚙️ Preferências da aplicação

---
