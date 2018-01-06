---
title: IDebugExpressionEvaluationCompleteEvent2::GetResult | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords: IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dc9988be307b1663d8712e86a94b1fe387af2425
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Pobiera wynik wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetResult(   
   IDebugProperty2** ppResult  
);  
```  
  
```csharp  
int GetResult(   
   out IDebugProperty2 ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppResult`  
 [out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje wynik obliczania wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zwrócona [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiektu zawiera wartość obliczane wyrażenie. Należy pamiętać, że ta wartość może być złożona wartość przykład tablicy, ale wynik końcowy musi być numeryczny lub ciąg wartość, która jest wyświetlana użytkownikowi.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)