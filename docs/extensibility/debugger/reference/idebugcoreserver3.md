---
title: IDebugCoreServer3 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5066521dbed42790d508becc1a3591dff3ae559d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108534"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Ten interfejs umożliwia dostęp do informacji o serwerze, który proces jest uruchomiony w.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Visual Studio implementuje ten interfejs.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj [QueryInterface](/cpp/atl/queryinterface) uzyskać ten interfejs z [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfejsu. Wywołanie [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) można także wrócić tego interfejsu. Ten interfejs jest najczęściej używany przez dostawcę niestandardowego numeru portu do uruchamiania programów na serwerze (lokalnego lub zdalnego).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz metod na [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfejsu, tego interfejsu implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Pobiera nazwę serwera.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Pobiera wersję przyjaznej nazwy serwera|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Określa, że aparatami debugowania określonych umożliwia automatyczne dołączanie do procesów, po uruchomieniu tych procesów.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Pobiera określonego kodu błędu, gdy automatyczne dołączanie kończy się niepowodzeniem.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Tworzy wystąpienie aparatu debugowania na serwerze.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Pobiera flagę wskazującą, czy serwer jest w tym samym komputerze co obiekt wywołujący.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Pobiera wartość wskazującą, protokół używany do komunikacji z serwerem.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Wyłącza wszystkie automatyczne dołączanie Ustawienia wszelkie aparatami debugowania, który zna tego serwera.|  
  
## <a name="remarks"></a>Uwagi  
 Odbiera dostawcy niestandardowego numeru portu [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfejsu na wywołanie [zdarzeń](../../../extensibility/debugger/reference/idebugportevents2-event.md). `IDebugCoreServer3` Interfejsu można uzyskać z tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)