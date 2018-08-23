---
title: Wdrażanie powłoki VS Shell | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e1a1bd92d1a0b91aa01d940695cd780f7e63c098
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42691679"
---
# <a name="vs-shell-deployment"></a>Wdrażanie powłoki VS Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wdrażanie powłoki VS Shell](https://docs.microsoft.com/visualstudio/modeling/vs-shell-deployment).  
  
Powłoka w trybie izolowanym pozwala określić, które program Visual Studio funkcji należy korzystać z języka specyficznego dla domeny i wygląd tego rozwiązania. Aby uzyskać więcej informacji na temat powłoki programu Visual Studio, izolowany zobacz [Dostosowywanie programu Isolated Shell](../extensibility/customizing-the-isolated-shell.md). Można znaleźć więcej informacji na temat sposobu dostosowywania programu isolated shell w [Dostosowywanie programu Isolated Shell](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Aby ustawić Visual Studio Shell jako cel wdrożenia  
  
1.  W **DslPackage** otwarty projekt **source.extension.tt**.  
  
2.  W obszarze `<SupportedProducts>` Wstaw:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Zastąp *MyIsolatedShell* o nazwie pakietu shell w trybie izolowanym.



