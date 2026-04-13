# 📝 TaskFlow

<p align="center">
  <b>Gerenciamento simples e eficiente de tarefas para o dia a dia</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-em%20desenvolvimento-yellow" />
  <img src="https://img.shields.io/badge/plataforma-web%20%7C%20mobile-blue" />
  <img src="https://img.shields.io/badge/licença-MIT-green" />
  <img src="https://img.shields.io/github/last-commit/Kevyn02/TaskFlow" />
  <img src="https://img.shields.io/github/repo-size/Kevyn02/TaskFlow" />
</p>

---

## 📖 Sobre o Projeto

O **TaskFlow** é um aplicativo de gerenciamento de tarefas (to-do list) focado em produtividade, simplicidade e organização.

O sistema permite que usuários gerenciem suas tarefas de forma eficiente, organizando-as por projetos e acompanhando seu progresso no dia a dia.

---

## ✨ Funcionalidades

- 🔐 Sistema de autenticação (login, cadastro e login social)

### 📁 Projetos

- ➕ Criar, ✏️ editar e 🗑️ excluir projetos
- 📂 Visualizar e organizar projetos
- 🎨 Definir identificação visual (cor)

### 📋 Tarefas

- ➕ Criar, ✏️ editar e 🗑️ excluir tarefas
- 🔄 Alterar status da tarefa (fluxo personalizado)
- 🔍 Filtrar e ↕️ ordenar tarefas
- ⚡ Definir prioridade (baixa, média, alta)
- 📁 Organização por projeto

### 🧩 Status personalizados

- 📊 Fluxo de status por projeto
- 🔢 Definição de ordem dos status
- 📝 Nome customizável
- 🎨 Cor para identificação visual

---

## 🧭 Arquitetura de Rotas

A aplicação é organizada em rotas públicas e privadas, separando o fluxo de autenticação do restante do sistema.

👉 Veja a estrutura completa em: [Arquitetura de Rotas](./docs/rotes.md)

## 🧱 Layout da Aplicação

Define a estrutura visual da aplicação para web e mobile, incluindo navegação e organização das telas.

👉 Veja os detalhes em: [Layout da Aplicação](./docs/layout.md)

## 🖼️ Wireframes

Os wireframes foram utilizados como base para definição da interface e experiência do usuário nas versões web e mobile.

👉 Veja todos os wireframes em: [Wireframes](./docs/wireframes.md)

## 🗄️ Banco de Dados

O sistema utiliza um modelo relacional com suporte a usuários, projetos e tarefas.

👉 Veja a modelagem completa em: [Database](./docs/database.md)

## 📊 Diagramas

O sistema possui diversos diagramas para representar seu funcionamento:

- Casos de uso
- Diagramas de sequência
- Diagramas de estados
- Diagrama entidade-relacionamento (ER)

👉 Acesse todos em: [Diagramas](./docs/diagrams.md)

## 🧩 Tecnologias

### 🎨 Frontend (Web)

- React
- TypeScript
- Vite

### 📱 Mobile

- React Native

### ⚙️ Backend

- Python (FastAPI)

### 🗄️ Banco de Dados

- PostgreSQL ou MySQL

### 🔧 Arquitetura e Ferramentas

- API REST
- JWT (autenticação)
- Context API / Zustand (estado)

---

## 📌 Requisitos do Sistema

### 🎯 Requisitos Funcionais

#### 🔐 Autenticação

- [ ] RF01: O sistema deve permitir o cadastro de usuários ([#1](../../issues/1))
- [ ] RF02: O sistema deve permitir o login de usuários ([#2](../../issues/2))
- [ ] RF03: O sistema deve permitir o logout do sistema ([#3](../../issues/3))
- [ ] RF04: O sistema deve validar as credenciais informadas ([#4](../../issues/4))

---

#### 📊 Dashboard

- [ ] RF05: O sistema deve exibir um resumo geral das informações ([#5](../../issues/5))
- [ ] RF06: O sistema deve listar tarefas recentes ([#6](../../issues/6))
- [ ] RF07: O sistema deve exibir projetos do usuário ([#7](../../issues/7))

---

#### 📁 Projetos

- [ ] RF08: O sistema deve permitir a criação de projetos ([#8](../../issues/8))
- [ ] RF09: O sistema deve permitir a edição de projetos ([#9](../../issues/9))
- [ ] RF10: O sistema deve permitir a exclusão de projetos ([#10](../../issues/10))
- [ ] RF11: O sistema deve listar todos os projetos cadastrados ([#11](../../issues/11))
- [ ] RF12: O sistema deve exibir os detalhes de um projeto ([#12](../../issues/12))
- [ ] RF13: O sistema deve utilizar modal para criação e edição de projetos ([#13](../../issues/13))

---

#### ✅ Tarefas

- [ ] RF14: O sistema deve permitir a criação de tarefas ([#14](../../issues/14))
- [ ] RF15: O sistema deve permitir a edição de tarefas ([#15](../../issues/15))
- [ ] RF16: O sistema deve permitir a exclusão de tarefas ([#16](../../issues/16))
- [ ] RF17: O sistema deve permitir marcar tarefas como concluídas ([#17](../../issues/17))
- [ ] RF18: O sistema deve listar tarefas por projeto ([#18](../../issues/18))
- [ ] RF19: O sistema deve exibir o status das tarefas ([#19](../../issues/19))

---

### ⚙️ Requisitos Não Funcionais

#### ⚡ Performance

- [ ] RNF01: O sistema deve responder requisições em até 2 segundos ([#20](../../issues/20))
- [ ] RNF02: O sistema deve possuir carregamento otimizado ([#21](../../issues/21))
- [ ] RNF03: O sistema deve utilizar paginação ou carregamento sob demanda nas listas ([#22](../../issues/22))

---

#### 🔒 Segurança

- [ ] RNF04: O sistema deve garantir autenticação segura ([#23](../../issues/23))
- [ ] RNF05: O sistema deve proteger os dados do usuário ([#24](../../issues/24))
- [ ] RNF06: O sistema deve validar todas as entradas de dados ([#25](../../issues/25))

---

#### 🧩 Usabilidade

- [ ] RNF07: O sistema deve possuir interface intuitiva ([#26](../../issues/26))
- [ ] RNF08: O sistema deve apresentar feedback visual (carregamento, erro e sucesso) ([#27](../../issues/27))
- [ ] RNF09: O sistema deve possuir estados bem definidos (vazio, carregando, erro) ([#28](../../issues/28))

---

#### 📱 Responsividade

- [ ] RNF10: O sistema deve ser responsivo (desktop e mobile) ([#29](../../issues/29))
- [ ] RNF11: O layout deve se adaptar a diferentes tamanhos de tela ([#30](../../issues/30))

---

#### 🔄 Escalabilidade

- [ ] RNF12: O sistema deve suportar múltiplos usuários simultaneamente ([#31](../../issues/31))
- [ ] RNF13: O sistema deve possuir arquitetura escalável ([#32](../../issues/32))

---

#### 🛠️ Manutenibilidade

- [ ] RNF14: O código deve ser organizado por responsabilidade ([#33](../../issues/33))
- [ ] RNF15: O sistema deve ser modular e de fácil manutenção ([#34](../../issues/34))

## 🚀 Roadmap do Projeto

### 🧱 Fase 1 — Base do Sistema (Fundação)

**Objetivo:** deixar o sistema utilizável com autenticação

- [ ] Cadastro de usuários _(RF01)_
- [ ] Login de usuários _(RF02)_
- [ ] Logout _(RF03)_
- [ ] Validação de credenciais _(RF04)_

💡 **Resultado:**
Usuário já consegue acessar o sistema com segurança

---

### 📊 Fase 2 — Dashboard Inicial

**Objetivo:** dar visão geral do sistema

- [ ] Exibir resumo geral _(RF05)_
- [ ] Listar tarefas recentes _(RF06)_
- [ ] Exibir projetos do usuário _(RF07)_

💡 **Resultado:**
Usuário tem visão rápida do que está acontecendo

---

### 📁 Fase 3 — Gestão de Projetos

**Objetivo:** estruturar organização principal

- [ ] Criar projetos _(RF08)_
- [ ] Editar projetos _(RF09)_
- [ ] Excluir projetos _(RF10)_
- [ ] Listar projetos _(RF11)_
- [ ] Detalhes do projeto _(RF12)_
- [ ] Modal de criação/edição _(RF13)_

💡 **Resultado:**
Usuário consegue organizar o trabalho por projetos

---

### ✅ Fase 4 — Gestão de Tarefas

**Objetivo:** controle operacional

- [ ] Criar tarefas _(RF14)_
- [ ] Editar tarefas _(RF15)_
- [ ] Excluir tarefas _(RF16)_
- [ ] Marcar como concluída _(RF17)_
- [ ] Listar por projeto _(RF18)_
- [ ] Exibir status _(RF19)_

💡 **Resultado:**
Sistema passa a ser realmente útil no dia a dia

---

### ⚙️ Fase 5 — Qualidade e Performance

**Objetivo:** melhorar experiência e eficiência

- [ ] Tempo de resposta até 2s _(RNF01)_
- [ ] Carregamento otimizado _(RNF02)_
- [ ] Paginação / lazy loading _(RNF03)_

💡 **Resultado:**
Sistema mais rápido e escalável

---

### 🔒 Fase 6 — Segurança

**Objetivo:** proteger dados e acesso

- [ ] Autenticação segura _(RNF04)_
- [ ] Proteção de dados _(RNF05)_
- [ ] Validação de entradas _(RNF06)_

💡 **Resultado:**
Sistema confiável

---

### 🧩 Fase 7 — Experiência do Usuário (UX)

**Objetivo:** melhorar usabilidade

- [ ] Interface intuitiva _(RNF07)_
- [ ] Feedback visual _(RNF08)_
- [ ] Estados bem definidos _(RNF09)_

💡 **Resultado:**
Sistema mais agradável de usar

---

### 📱 Fase 8 — Responsividade

**Objetivo:** funcionar bem em qualquer dispositivo

- [ ] Responsivo (mobile/desktop) _(RNF10)_
- [ ] Layout adaptável _(RNF11)_

💡 **Resultado:**
Uso completo em celular e desktop

---

### 🔄 Fase 9 — Escalabilidade

**Objetivo:** preparar crescimento

- [ ] Suporte a múltiplos usuários _(RNF12)_
- [ ] Arquitetura escalável _(RNF13)_

---

### 🛠️ Fase 10 — Manutenibilidade

**Objetivo:** facilitar evolução do sistema

- [ ] Código organizado _(RNF14)_
- [ ] Arquitetura modular _(RNF15)_

## 💡 Melhorias Futuras

- Login com Google
- Login com GitHub
- Notificações em tempo real
- Drag and drop
- Modo offline
- Sincronização entre dispositivos
- Compartilhamento de projetos
- Integração com calendário

---

## 📄 Licença

Este projeto está sob a licença **MIT**.

---

## 👨‍💻 Autor

Desenvolvido por **Kevyn Aparecido**
