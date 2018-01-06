---
title: IEnumDebugPorts2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPorts2
helpviewer_keywords: IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 277189c9b5510df1da4802e42225ffafa4b6995c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Ten interfejs wylicza portów komputera lub portu dostawcy.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego numeru portu implementuje ten interfejs reprezentujący listę portów tworzone przez dostawcę. Visual Studio implementuje ten interfejs, w związku z własnego portu dostawcy.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) uzyskać ten interfejs reprezentujący listę portów tworzone przez dostawcę portu. Wywołanie [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) uzyskać ten interfejs reprezentujący listę portów, które zostały zapisane na dysku.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IEnumDebugPorts2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Pobiera określoną liczbę portów w kolejności wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Pomija określoną liczbę portów w kolejności wyliczenia.|  
|[Resetowanie](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Resetuje sekwencję wyliczenia na początku.|  
|[Klonowania](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Pobiera liczbę portów w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio korzysta ten interfejs, aby wypełnić listy portów używanych do dołączanie do procesu.  
  
 Aparat debugowania zwykle nie korzysta z tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)