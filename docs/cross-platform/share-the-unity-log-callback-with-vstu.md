---
title: "Udostępnianie wywołania zwrotnego dziennika środowiska Unity za pomocą rozszerzenia VSTU | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-unity-tools
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: da0a8b98e358060cf11de87d9af2edf7e6b15f58
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
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
