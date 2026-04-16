← [Voltar para Casos de Uso](./README.md)

---

[Início](../../../README.md) / [Diagramas](../README.md) / [Casos de Uso](./README.md) / Configurações

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
