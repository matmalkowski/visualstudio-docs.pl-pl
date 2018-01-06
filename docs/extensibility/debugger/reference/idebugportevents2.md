---
title: IDebugPortEvents2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEvents2
helpviewer_keywords: IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0a5782f0a50ac37b45c4b7e3402bcdded96b4683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
|[Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Wysyła zdarzenia, które opisują tworzenie i likwidacja procesów i programów na tym porcie.|  
  
## <a name="remarks"></a>Uwagi  
 `IDebugPortEvents2`Umożliwia również przez SDM debugowanie programów uruchamianych w ramach procesu, który jest już debugowany.  
  
 Port zdarzenia są przekazywane do SDM przez ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)