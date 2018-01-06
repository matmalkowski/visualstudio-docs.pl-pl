---
title: IDebugExpressionEvaluator::SetLocale | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluator::SetLocale
helpviewer_keywords: IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fe9dd81fad59c526233a56f1c5bcd1a178ad46f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Ta metoda określa język używać do tworzenia wyniki do druku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wLangID`  
 [in] Identyfikator języka.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może zostać wywołana wiele razy podczas ewaluatora wyrażenia (EE) jest załadowany, więc EE musi mieć możliwość przełączania języków na bieżąco. EE używa tych ustawień regionalnych, aby zwrócić komunikaty o błędach i ciągi w odpowiednim języku.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)