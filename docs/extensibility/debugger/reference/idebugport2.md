---
title: IDebugPort2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1811ad7e46865d00eed2066d061daec78d7ab2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugport2"></a>IDebugPort2
Ten interfejs reprezentuje port debugowania na maszynie.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego numeru portu implementuje ten interfejs do reprezentowania portem debugowania na maszynie.  
  
 Jeśli port obsługuje wysyłanie zdarzeń portu, musi implementować też <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfejs do obsługi <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejs, który z kolei udostępnia [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołuje się [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) lub [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) zwracać ten interfejs reprezentujący żądanym porcie.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugPort2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Zwraca nazwę portu.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Zwraca identyfikator portu.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Zwraca żądanie użyty do utworzenia portu (jeśli jest dostępna).|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Zwraca dostawcę portu dla tego portu.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Zwraca interfejs do procesu podany identyfikator procesu.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Wylicza wszystkie procesy, które są uruchomione na porcie.|  
  
## <a name="remarks"></a>Uwagi  
 Port lokalny zapewnia dostęp do wszystkich procesów i programy uruchomione na komputerze lokalnym. Inne porty może reprezentować połączenie kabel szeregowy do urządzenia z systemem Windows CE lub połączenie sieciowe z komputerem z systemem innym niż DCOM. `IDebugPort2` Interfejs jest używany, aby znaleźć nazwę i identyfikator portu, wyliczyć wszystkich procesów działających w porcie i zapewnić urządzeń uruchamianie i kończenie procesów na porcie.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)