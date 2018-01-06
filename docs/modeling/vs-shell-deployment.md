---
title: "VS powłoki wdrożenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: aeb4ca2153d4c060862d31e53202312f061bf1ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell
Powłoka w trybie izolowanym pozwala określić, którego program Visual Studio funkcje muszą wchodzić w interakcje z języka specyficznego dla domeny i sposób wyświetlania tego rozwiązania. Aby uzyskać więcej informacji na temat powłoki programu Visual Studio samodzielnie, zobacz [Dostosowywanie programu Isolated Shell](../extensibility/customizing-the-isolated-shell.md). Można znaleźć więcej informacji na temat sposobu dostosowywania programu isolated shell w [Dostosowywanie programu Isolated Shell](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Aby ustawić jako cel wdrożenia programu Visual Studio Shell  
  
1.  W **DslPackage** otwarciu projektu **source.extension.tt**.  
  
2.  W obszarze `<SupportedProducts>` Wstaw:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Zastąp *MyIsolatedShell* z nazwą pakietu programu isolated shell.