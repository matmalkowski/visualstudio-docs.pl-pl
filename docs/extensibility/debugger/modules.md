---
title: Moduły | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8750c1f6676966be8564fbf4a175a66fa180a401
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233168"
---
# <a name="modules"></a>Moduły
Pod względem architektury debugera *modułu*:  
  
-   Jest kontenerem fizycznych kodu, takie jak plik wykonywalny lub bibliotekę DLL.  
  
-   Można ponownie załadować jej symboli i opisania siebie. Moduł opisy są wyświetlane w oknie moduły środowiska IDE.  
  
-   Jest reprezentowany przez [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfejsu, utworzonych przez aparat debugowania w celu opisania modułu.  
  
## <a name="see-also"></a>Zobacz także  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)