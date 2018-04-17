---
title: VS powłoki wdrożenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4964ce162efac640ea7581b4d3f26f3d50087319
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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