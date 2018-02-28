---
title: IDebugPort2::GetPortId | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPort2::GetPortId
helpviewer_keywords:
- IDebugPort2::GetPortId
ms.assetid: 837cb924-c113-4224-aa86-3e02b33dfa70
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 75f4d952ac1f4f9a3350eba973c5fac7d557f50b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugport2getportid"></a>IDebugPort2::GetPortId
Pobiera identyfikator portów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPortId(   
   GUID* pguidPort  
);  
```  
  
```csharp  
int GetPortId(   
   out Guid pguidPort  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pguidPort`  
 [out] Zwraca identyfikator GUID, który identyfikuje port.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)