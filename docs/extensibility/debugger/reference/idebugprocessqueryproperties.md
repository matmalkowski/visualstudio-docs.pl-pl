---
title: IDebugProcessQueryProperties | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 66c2c3800d5f571595d7aec1a1e145cbccd38ff5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Ten interfejs jest implementowany przez interfejs rozszerzenia [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) implementacji. Umożliwia on czynności uzyskać informacje o debugowaniu środowiska procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Implementuje ten interfejs, aby uzyskać informacje o środowiska wykonawczego debugowania procesu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugProcessQueryProperties`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Zapytania dotyczące wartości właściwości.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Zapytania dotyczące wartości właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest implementowany rzadko.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)