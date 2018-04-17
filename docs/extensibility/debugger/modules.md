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
ms.openlocfilehash: f587e015263336436588d14edeeb5c6935872950
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="modules"></a>Moduły
Pod względem architektury debugera **modułu**:  
  
-   Jest kontenerem fizycznych kodu, na przykład plik wykonywalny lub biblioteka DLL.  
  
-   Można ponownie załadować jego symbole i opisania siebie. Opisy modułu są wyświetlane w oknie moduły IDE.  
  
-   Jest reprezentowana przez [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfejsu tworzony przez aparat debugowania, opisujący modułu.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)