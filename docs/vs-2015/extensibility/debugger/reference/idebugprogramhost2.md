---
title: IDebugProgramHost2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd8e0b54765f20dce21eae135b0942547f967836
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679689"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugProgramHost2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramhost2).  
  
Ten interfejs zawiera hosta (proces) informacje dotyczące programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania implementuje ten interfejs na ten sam obiekt jako [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu do dostarczania informacji dotyczących procesu hostingu. Jest to opcjonalny interfejs.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na `IDebugProgram2` interfejsu w celu uzyskania tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugProgramHost2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Gethostname —](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Pobiera tytuł, przyjazną nazwę lub nazwę pliku procesu hostingu tego programu.|  
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Pobiera identyfikator procesu procesu hostingu tego programu.|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Pobiera nazwę komputera, procesu hostingu tego programu na którym uruchomiona jest.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

