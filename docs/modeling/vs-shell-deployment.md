---
title: Wdrażanie powłoki VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 816997f971e90ddd27f8e24cdc1857559e04ff70
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell

Powłoka w trybie izolowanym pozwala określić, którego program Visual Studio funkcje muszą wchodzić w interakcje z języka specyficznego dla domeny i sposób wyświetlania tego rozwiązania. Aby uzyskać więcej informacji na temat powłoki programu Visual Studio samodzielnie, zobacz [Dostosowywanie programu Isolated Shell](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Aby ustawić jako cel wdrożenia programu Visual Studio Shell

1.  W **DslPackage** otwarciu projektu **source.extension.tt**.

2.  W obszarze `<SupportedProducts>` Wstaw:

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Zastąp *MyIsolatedShell* z nazwą pakietu programu isolated shell.