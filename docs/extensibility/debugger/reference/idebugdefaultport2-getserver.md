---
title: IDebugDefaultPort2::GetServer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDefaultPort2::GetServer
helpviewer_keywords: IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c1d5839db305c1395edc24a95de706cfc2072d8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Ta metoda uzyskuje interfejs do serwera, który znajduje się na tym porcie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```csharp  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppServer`  
 [out] Zwraca obiekt implementacja [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) jest zaimplementowana przez program Visual Studio i reprezentuje serwer, który port znajduje się na.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)