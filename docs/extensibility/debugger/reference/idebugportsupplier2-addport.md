---
title: IDebugPortSupplier2::AddPort | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab6348739feba7006e5c18eee6f7dc5f301242d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114433"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Dodaje port.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```csharp  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRequest`  
 [in] [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) obiektu, który opisuje portu, który ma zostać dodana.  
  
 `ppPort`  
 [out] Zwraca [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) obiekt, który reprezentuje port.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda tworzy żądanym porcie, jak i dodanie go do dostawcy portu wewnętrzną listę aktywnych portów. [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) można wywołać metody najpierw Aby uniknąć możliwych opóźnień czasochłonna.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)