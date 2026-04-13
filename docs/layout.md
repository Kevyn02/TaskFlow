← Voltar para [Documentação](../README.md)

## 🧱 Layout da Aplicação

Define a estrutura visual e organizacional das telas da aplicação, separando o fluxo de autenticação do restante do sistema.

### 🌐 Web

```
/ (App Layout)
 ├── Sidebar        # Navegação principal
 ├── Header         # Ações globais e informações do usuário
 └── Content        # Área dinâmica (renderização das páginas)
```

**Características:**

- Layout persistente entre páginas
- Navegação lateral fixa (Sidebar)
- Header com ações rápidas e contexto

**Rotas que utilizam o layout:**

- `/dashboard`
- `/projects`
- `/settings`

📌 Rotas públicas (`/signin`, `/signup`) utilizam layout independente

---

### 📱 Mobile

```
Stack (Auth)
 ├── SignIn
 └── SignUp

Stack (App)
 ├── Tabs
 │    ├── Dashboard
 │    ├── Projects
 │    └── Settings
 ├── ProjectDetail
 │    ├── StatusList
 │    ├── StatusCreate
 │    └── StatusEdit
 ├── TaskCreate
 ├── TaskDetail
 └── TaskEdit
```

**Características:**

- Separação entre fluxo de autenticação e aplicação
- Navegação principal baseada em abas (Tabs)
- Uso de Stack para telas secundárias (tarefas e status)
- Status vinculados ao contexto do projeto

**Comportamento:**

- Usuário não autenticado → Stack (Auth)
- Usuário autenticado → Stack (App)

---
