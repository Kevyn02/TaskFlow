Voltar para [📌 Diagrama de Casos de Uso](../index.md)

---

[Início](../../../../README.md) | [📊 Diagramas](../../index.md) | [📌 Diagrama de Casos de Uso](../index.md) | Autenticação

---

## Autenticação

```mermaid
graph TD

    User[👤 Usuário]

    %% Autenticação
    subgraph AUTH[Autenticação]
        Register((🆕 Criar Conta))
        Login((🔐 Realizar Login))
        SocialLogin((🔗 Login com Google/GitHub))
        Logout((🚪 Logout))
        RecoverPassword((♻️ Recuperar senha))
    end

    User --> Register
    User --> Login
    User --> SocialLogin
    User --> Logout
    User --> RecoverPassword
```
