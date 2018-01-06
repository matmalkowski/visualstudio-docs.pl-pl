---
title: IDebugExpressionEvaluator::Parse | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluator::Parse
helpviewer_keywords: IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e64d7419973f0505a2413d7ea56be12a31d01a1c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Ta metoda konwertuje ciąg wyrażenia przeanalizowany wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `upstrExpression`  
 [in] Ciąg wyrażenia do przeanalizowania.  
  
 `dwFlags`  
 [in] Kolekcja [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) stałe, które określają sposób wyrażenia do przeanalizowania.  
  
 `nRadix`  
 [in] Podstawa ma być używany do interpretować wszystkie informacje numeryczne.  
  
 `pbstrError`  
 [out] Zwraca błąd jako tekst zrozumiałą dla użytkownika.  
  
 `pichError`  
 [out] Zwraca ciąg wyrażenia znaku na pozycji początkowej błędu.  
  
 `ppParsedExpression`  
 [out] Zwraca wyrażenie przeanalizowany w [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda tworzy wyrażenie przeanalizowany, a nie rzeczywistą wartość. Przeanalizowana wyrażenie jest gotowy do obliczenia, oznacza to, przekonwertowana na wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)