## <a name="create-a-kubernetes-development-environment-in-azure"></a>Utwórz Środowisko deweloperskie Kubernetes na platformie Azure
W środowiskach połączone można utworzyć Kubernetes środowisk pełni zarządzanych przez usługę Azure i zoptymalizowane pod kątem tworzenia. Polecenie tworzy ze środowiska o nazwie `mydevenvironment` w `eastus`.
```cmd
vsce env create --name mydevenvironment --location eastus
```

Obsługiwane lokalizacje: `eastus`, `westeurope`

> [!Note]
> To polecenie wymaga około 6 minut. Ten przewodnik nie czekając można kontynuować.
