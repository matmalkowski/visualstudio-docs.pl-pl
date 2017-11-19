---
title: IDebugPort2::GetPortRequest | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPort2::GetPortRequest
helpviewer_keywords: IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df00ec25a4f417e6a84a5c42f04f082df6e0b05c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Pobiera opis portu, który był wcześniej używany do utworzenia portu (jeśli jest dostępna).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```csharp  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppRequest`  
 [out] Zwraca [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) obiekt reprezentujący żądania, który został użyty do utworzenia portu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  Zwraca `E_PORT_NO_REQUEST` Jeśli port nie został utworzony przy użyciu [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) port żądania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)