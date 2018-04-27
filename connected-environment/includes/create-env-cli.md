---
ms.topic: include
ms.openlocfilehash: 97f9885780c9f697cfc6a58b78054761fdcd725d
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
## <a name="create-a-kubernetes-development-environment-in-azure"></a>Utwórz Środowisko deweloperskie Kubernetes na platformie Azure
W środowiskach połączone można utworzyć Kubernetes środowisk pełni zarządzanych przez usługę Azure i zoptymalizowane pod kątem tworzenia. Polecenie tworzy ze środowiska o nazwie `mydevenvironment` w `eastus`.
```cmd
vsce env create --name mydevenvironment --location eastus
```

Obsługiwane lokalizacje: `eastus`, `westeurope`

> [!Note]
> To polecenie wymaga około 6 minut. Ten przewodnik nie czekając można kontynuować.
