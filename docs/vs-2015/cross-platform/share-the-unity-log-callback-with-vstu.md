---
title: Udostępnianie wywołania zwrotnego dziennika środowiska Unity za pomocą rozszerzenia VSTU | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 5
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 8e1e0f2062195830443a169c67d9b75d2b1915ec
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685519"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Udostępnianie wywołania zwrotnego dziennika środowiska Unity za pomocą rozszerzenia VSTU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [udostępnianie wywołania zwrotnego dziennika środowiska Unity za pomocą rozszerzenia VSTU](https://docs.microsoft.com/visualstudio/cross-platform/share-the-unity-log-callback-with-vstu).  
  
  
Visual Studio Tools for Unity rejestruje wywołanie zwrotne dziennika przy użyciu aparatu Unity, aby móc przesyłać strumieniowo jego konsoli w programie Visual Studio. Edytor skryptów również zarejestrować wywołanie zwrotne dziennika przy użyciu aparatu Unity, wywołanie zwrotne w narzędziach VSTU może zakłócać wywołanie zwrotne. Aby zapobiec tej możliwości, użyj `VisualStudioIntegration.LogCallback` zdarzenie, aby współpracować za pomocą rozszerzenia VSTU.  
  
## <a name="demonstrates"></a>Demonstracje  
 Jak udostępnić wywołania zwrotnego dziennika środowiska Unity, które zostały utworzone przez program Visual Studio Tools for Unity.  
  
## <a name="example"></a>Przykład  
  
```csharp  
using System;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class LogCallbackHook  
{  
    static LogCallbackHook()  
    {  
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>  
        {  
            // place code that implements your log callback here  
        };  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładzie: Generowanie pliku projektu](../cross-platform/customize-project-files-created-by-vstu.md)

