---
title: IDebugExpressionEvaluator2::GetService | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d907bdd93d2c17eb86ae07f9c9cfa3034fa3c09d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Pobiera obiekt usługi na podstawie jego unikatowy identyfikator.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```csharp  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `uid`  
 [in] Unikatowy identyfikator usługi do pobrania.  
  
 `ppService`  
 [out] Zwraca obiekt, który reprezentuje usługę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 To może być zużyte przez ewaluatora wyrażenia innych firm, można uzyskać usług z innego ewaluatora wyrażenia. Na przykład tej metody może zostać użyty do uzyskania interfejsu usługi wizualizatora z domyślnego ewaluatora wyrażenia. Ewaluatory wyrażeń innych firm prawdopodobnie nie muszą zawierać implementację tego interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)