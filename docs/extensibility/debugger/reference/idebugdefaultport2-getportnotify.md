---
title: IDebugDefaultPort2::GetPortNotify | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 26eefb5dc1e30d9d9b8b6584159ce5f942b8e4e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Ta metoda pobiera [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfejs dla tego portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppPortNotify`  
 [out] [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zwykle `QueryInterface` metoda jest wywoływana na implementacji obiektu [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejsu uzyskanie [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfejsu. Istnieją jednak okoliczności, w których żądany interfejs jest wdrażany na inny obiekt. Ta metoda powoduje ukrycie tych sytuacji i zwraca `IDebugPortNotify2` interfejsu z najbardziej odpowiedniego obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)