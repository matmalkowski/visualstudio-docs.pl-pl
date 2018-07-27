---
title: Udostępnianie wywołania zwrotnego dziennika środowiska Unity za pomocą rozszerzenia VSTU | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 3bf25ed2764078f2d3e0424ab34f4e4a8e470ff5
ms.sourcegitcommit: e6ef03cc415ca67f75fd1f26e0e7b8846857166d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2018
ms.locfileid: "39310023"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Udostępnianie wywołania zwrotnego dziennika środowiska Unity za pomocą rozszerzenia VSTU
Visual Studio Tools for Unity rejestruje wywołanie zwrotne dziennika przy użyciu aparatu Unity, aby móc przesyłać strumieniowo jego konsoli w programie Visual Studio. Edytor skryptów również zarejestrować wywołanie zwrotne dziennika przy użyciu aparatu Unity, wywołanie zwrotne w narzędziach VSTU może zakłócać wywołanie zwrotne. Aby zapobiec tej możliwości, użyj `VisualStudioIntegration.LogCallback` zdarzenie, aby współpracować za pomocą rozszerzenia VSTU.

## <a name="demonstrates"></a>Demonstracje
 Jak udostępnić wywołania zwrotnego dziennika środowiska Unity, które zostały utworzone przez program Visual Studio Tools for Unity.

## <a name="example"></a>Przykład

```csharp
#if ENABLE_VSTU
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
#endif
```

## <a name="see-also"></a>Zobacz także
 [Przykładzie: Generowanie pliku projektu](../cross-platform/customize-project-files-created-by-vstu.md)
