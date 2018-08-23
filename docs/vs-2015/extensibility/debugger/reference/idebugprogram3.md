---
title: IDebugProgram3 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8fd061a8321fffa30befcfc9290e6819d96d90fc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690093"
---
# <a name="idebugprogram3"></a>IDebugProgram3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugProgram3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram3).  
  
Ten interfejs reprezentuje program, który jest uruchomiony w procesie i rozszerza [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md) , podając informacje o wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) i dostawcy niestandardowego portu należy zaimplementować ten interfejs do reprezentowania program w procesie. Menedżer debugowania sesji (SDM) również implementuje ten interfejs, aby zapewnić informacje [Dołącz](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzeń zwraca ten interfejs dla nowego programu. Ten interfejs jest również używany jako parametr dla wielu metod w wielu interfejsach.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugProgram3`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Wykonuje program. Wątek jest zwracany do przedstawienia informacji debugera, na który wątek wyświetlanie użytkownika podczas wykonywania.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Uwagi  
 Program jest kontenerem wątków, uruchomiony w ramach określonej architektury czasu wykonywania, podczas procesu składa się z jednego lub wielu programów.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Dalej](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

