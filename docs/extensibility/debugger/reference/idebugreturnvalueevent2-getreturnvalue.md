---
title: IDebugReturnValueEvent2::GetReturnValue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReturnValueEvent2::GetReturnValue
helpviewer_keywords: IDebugReturnValueEvent2::GetReturnValue
ms.assetid: 86c50d5a-6df6-4798-818a-c587a8741f90
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2d0fbf4aa020436da8b269b2bea187f6154f371b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugreturnvalueevent2getreturnvalue"></a>IDebugReturnValueEvent2::GetReturnValue
Pobiera wartość zwracana na wykonywanie krok po kroku z lub za pośrednictwem funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetReturnValue (   
   IDebugProperty2** ppReturnValue  
);  
```  
  
```csharp  
int GetReturnValue (   
   out IDebugProperty2 ppReturnValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppReturnValue`  
 [out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje wartości, które mają zostać pobrane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)