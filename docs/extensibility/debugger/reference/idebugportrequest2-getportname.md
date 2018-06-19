---
title: IDebugPortRequest2::GetPortName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c81bdc6586766cb4a241bf29e653cb1b10f66f2f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114336"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Pobiera nazwę portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrPortName`  
 [out] Zwraca nazwę portu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interfejsu jest zwykle przekazane z pakietem debugowania (klienta) do portu dostawcy (serwera) można uzyskać połączenia do portu. Możliwe opcje portu znane są zarówno pakietu debugowania i portu dostawcy. Jeśli prosty ciąg opisujący portu, a następnie `IDebugPortRequest2::GetPortName` metoda ma za mało informacji do nawiązania połączenia. W przeciwnym razie można podać dodatkowe interfejsy przez klienta, który można uzyskać za pomocą serwera `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)