---
title: Wdrażanie powłoki VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 61cf6e716f082abf28043d56d1a8803853d894aa
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566676"
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell

Powłoka w trybie izolowanym pozwala określić, które program Visual Studio funkcji należy korzystać z języka specyficznego dla domeny i wygląd tego rozwiązania. Aby uzyskać więcej informacji na temat powłoki programu Visual Studio, izolowany zobacz [Dostosowywanie programu Isolated Shell](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Aby ustawić Visual Studio Shell jako cel wdrożenia

1.  W **DslPackage** otwarty projekt **source.extension.tt**.

2.  W obszarze `<SupportedProducts>` Wstaw:

    ```xml
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Zastąp *MyIsolatedShell* o nazwie pakietu shell w trybie izolowanym.