---
title: IDebugProperty2::GetReference | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetReference
helpviewer_keywords: IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f8b8a5e5ba359f60d80c30e73645f3fe121c82e5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
Zwraca odwołanie do wartości właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetReference(  
   IDebugReference2** ppReference  
);  
```  
  
```csharp  
int GetReference(  
   out IDebugReference2 ppReference  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppRererence`  
 [out] Zwraca [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiekt reprezentujący odwołania do wartości właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu, zwykle `E_NOTIMPL` lub `E_GETREFERENCE_NO_REFERENCE`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)