---
title: IDebugPortEvents2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af2652bd18ff5d371389e8d3a7d3ab4c477eaa34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Ten interfejs powiadamia słuchacz (zazwyczaj sesji debugowania Menedżera [SDM] lub aparat debugowania) proces i program tworzenie i likwidacja na określonym porcie. Te informacje można przedstawić w czasie rzeczywistym widoku procesów i programy uruchomione na tym porcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Visual Studio zwykle implementuje ten interfejs, aby otrzymywać powiadomienia o program tworzenie i likwidacja. Aparat debugowania mogą również zawierać implementację tego interfejsu do nasłuchiwania zdarzeń takich portów.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wszystkie [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejsy mogą być przeszukiwane dla <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfejsu. Następnie przy użyciu <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> metodę `IDebugPortEvents2` jest wywoływana <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfejsu, aby uzyskać <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejsu. Na koniec <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metody w <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> wywoływany jest interfejs do wysyłania zdarzeń za pomocą [zdarzeń](../../../extensibility/debugger/reference/idebugportevents2-event.md) metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugPortEvents2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Wysyła zdarzenia, które opisują tworzenie i likwidacja procesów i programów na tym porcie.|  
  
## <a name="remarks"></a>Uwagi  
 `IDebugPortEvents2` Umożliwia również przez SDM debugowanie programów uruchamianych w ramach procesu, który jest już debugowany.  
  
 Port zdarzenia są przekazywane do SDM przez ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)