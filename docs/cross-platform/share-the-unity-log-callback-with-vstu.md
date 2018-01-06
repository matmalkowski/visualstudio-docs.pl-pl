---
title: "Udostępnianie wywołania zwrotnego dziennika środowiska Unity za pomocą rozszerzenia VSTU | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: "2"
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload: unity
ms.openlocfilehash: 6c078affefbb24a9fbbb65c854911f4b91f12183
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Udostępnianie wywołania zwrotnego dziennika środowiska Unity za pomocą rozszerzenia VSTU
Visual Studio Tools for Unity rejestruje wywołanie zwrotne dziennika Unity, aby można było strumienia jego konsoli dla programu Visual Studio. Jeśli Edytor skryptów również zarejestrowane wywołanie zwrotne dziennika środowiska Unity, wywołania zwrotnego pomocą rozszerzenia VSTU może zakłócać wywołanie zwrotne. Aby zapobiec tej możliwości, użyj `VisualStudioIntegration.LogCallback` zdarzeń do współpracy za pomocą rozszerzenia VSTU.  

## <a name="demonstrates"></a>Demonstracje  
 Jak udostępnić wywołanie zwrotne dziennika Unity, które zostały utworzone przez Visual Studio Tools for Unity.  

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
 [Przykład: Generowanie pliku projektu](../cross-platform/customize-project-files-created-by-vstu.md)
