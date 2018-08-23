---
title: IEnumDebugPrograms2 | Dokumentacja firmy Microsoft
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
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2871a64ce618d03a96900d916a56fb0c598e47e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681331"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IEnumDebugPrograms2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugprograms2).  
  
Ten interfejs wylicza programów uruchomionych w bieżącej sesji debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs, aby udostępnić listę programów, które jest debugowane DE.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Visual Studio wywołania [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) uzyskać ten interfejs. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) nie jest używany przez program Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumDebugPrograms2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Pobiera określoną liczbę programów w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Pomija określoną liczbę programów w kolejności wyliczenia.|  
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Pobiera liczbę programów w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio używa tego interfejsu:  
  
-   Wypełnij **modułów** okna (przez wywołanie metody [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) , a następnie wywołując [enummodules —](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) na każdy program).  
  
-   Wypełnij **dołączyć do procesu** listy (przez wywołanie metody `IDebugProcess2::EnumPrograms` , a następnie wywołując [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na każdym [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejs do uzyskiwania [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) interfejsu).  
  
-   Generowanie listy DEs, który można debugować każdy program w procesie (przy użyciu [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Stosowanie aktualizacji Edytuj i Kontynuuj (ENC) do każdego programu (przez wywołanie IDebugProcess2::EnumPrograms, a następnie wywołując [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

