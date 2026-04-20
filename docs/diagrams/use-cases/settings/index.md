Voltar para [📌 Diagrama de Casos de Uso](../index.md)

---

[Início](../../../../README.md) | [📊 Diagramas](../../index.md) | [📌 Diagrama de Casos de Uso](../index.md) | Configurações

---

## Configurações

```mermaid
graph TD

    User[👤 Usuário]

    %% Configurações
    subgraph SETTINGS[Configurações]
        UpdateProfile((👤 Editar Perfil))
        ChangePassword((🔒 Alterar Senha))
        Preferences((⚙️ Preferências))
    end

    User --> UpdateProfile
    User --> ChangePassword
    User --> Preferences
```
