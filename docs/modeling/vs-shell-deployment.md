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
ms.openlocfilehash: e7df1991832e954def71a6cee5bd5516dfd4e961
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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