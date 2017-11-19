---
title: IDebugFunctionObject::Evaluate | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugFunctionObject::Evaluate
helpviewer_keywords: IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4eb9140ae74cd758525dba30fd4b4da49d82db9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Wywołuje funkcję i zwraca wartość wynikową jako obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppParams`  
 [in] Tablica [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekty reprezentujące parametry wejściowe. Każdy z tych parametrów został utworzony za pomocą `Create` metod w [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfejsu.  
  
 `dwParams`  
 [in] Liczba parametrów w `ppParams` tablicy.  
  
 `dwTimeout`  
 [in] Określa maksymalny czas (w milisekundach) oczekiwania przed powrotem z tej metody. Użyj `INFINITE` będzie czekać w nieskończoność.  
  
 `ppResult`  
 [out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący wartość funkcji jako obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda konfiguruje i wykonuje wywołanie funkcji reprezentowany przez [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)