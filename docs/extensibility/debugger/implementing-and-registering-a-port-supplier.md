---
title: "Wdrażanie i rejestrowanie dostawcy portu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1c05dc0bd15dc5c1959024327396d848cd0b1112
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-and-registering-a-port-supplier"></a>Wdrażanie i rejestrowanie dostawcy portu
Rolą port dostawcy jest śledzenie i podaj portów, które z kolei zarządzania procesami. W momencie port musi zostać utworzona dostawca portu zostanie uruchomiony przy użyciu CoCreate z identyfikatorem GUID dostawcy portu (manager debugowania sesji [SDM] będzie używać portu dostawcy wybrany przez użytkownika lub dostawcę port określony przez system projektów). Następnie wywoła SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) aby zobaczyć, czy żadnych portów może być dodany. Jeśli port można dodać, nowy port jest wymagany przez wywołanie [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) i przekazanie jej [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) port, który opisuje. `AddPort`Zwraca nowy port reprezentowany przez [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfejsu.  
  
## <a name="discussion"></a>Omówienie  
 Port jest tworzony przez dostawcę portu, który jest skojarzony z serwerem maszyny lub debugowania. Serwer można wyliczyć dostawców za pośrednictwem portu[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) — metoda i dostawcy portu można wyliczyć jego portów za pomocą [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) metody.  
  
 Oprócz typowych rejestracji modelu COM portu dostawcy musi zarejestrować się z programem Visual Studio przez umieszczenie jej identyfikator CLSID i nazwy w lokalizacji rejestru. Wywołuje funkcję pomocnika debugowanie zestawu SDK `SetMetric` obsługi tej kwestii: jest wywoływana raz dla każdego elementu mają być zarejestrowane w związku z tym:  
  
```cpp  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 Dostawca portu wyrejestrowuje przez wywołanie metody `RemoveMetric` (innej funkcji pomocnika debugowanie zestawu SDK) raz dla każdego elementu, który został zarejestrowany w związku z tym:  
  
```cpp  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
>  [Pomocników zestawu SDK dla debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` i `RemoveMetric` są statyczne funkcje zdefiniowane w dbgmetric.h i kompilowane do ad2de.lib. `metrictypePortSupplier`, `metricCLSID`, I `metricName` w dbgmetric.h można zdefiniować pomocników.  
  
 Dostawca portu podać jego nazwę i identyfikator GUID za pomocą metody [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) i [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)odpowiednio.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementacja dostawcy portu](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Pomocnicy zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)