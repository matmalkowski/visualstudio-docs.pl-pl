---
title: IDebugParsedExpression::EvaluateSync | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugParsedExpression::EvaluateSync
helpviewer_keywords: IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 261359ae3dc82f8544d0f48cf0e8f1103ccedd5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Ta metoda oblicza wyrażenie przeanalizowany i opcjonalnie rzutuje wynik, który ma inny typ danych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```csharp  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwEvalFlags`  
 [in] Kombinację [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) stałe, które kontrolują sposób wyrażenie, które ma zostać obliczone.  
  
 `dwTimeout`  
 [in] Określa maksymalny czas (w milisekundach) oczekiwania przed powrotem z tej metody. Użyj `INFINITE` będzie czekać w nieskończoność.  
  
 `pSymbolProvider`  
 [in] Dostawca symbolu, wyrażony jako [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interfejsu.  
  
 `pAddress`  
 [in] Bieżąca lokalizacja wykonywania w metodzie, wyrażony jako [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.  
  
 `pBinder`  
 [in] Obiekt wiążący, wyrażony jako [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfejsu.  
  
 `bstrResultType`  
 [in] Typ wyniku powinny być rzutowane na. Ten argument może być wartością null.  
  
 `ppResult`  
 [out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfejs, który reprezentuje wyniki oceny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kontekst oceny wyrażenia jest określany przez `pAddress`, co umożliwia ustalenie zawierające metody i następnie użyj języka zakresu reguły do określenia wartości symboli w wyrażeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)