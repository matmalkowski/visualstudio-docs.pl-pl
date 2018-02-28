---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 612cdb579615acb7ca5b4b6a34c0c485683c4fe1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Ta metoda konwertuje metody lokalizacji i Przesunięcie na adres pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `upstrFullyQualifiedMethodPlusOffset`  
 [in] Metoda lokalizacji i przesunięcie, wyrażony jako ciąg.  
  
 `pSymbolProvider`  
 [in] Dostawca symbol wyrażonej w postaci [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) obiektu.  
  
 `pAddress`  
 [in] Adres w metodzie, wyrażony jako [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektu.  
  
 `pBinder`  
 [in] Obiekt wiążący wyrażonej w postaci [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obiektu.  
  
 `ppProperty`  
 [out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfejs, który reprezentuje adres pamięci.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zwrócony adres można na przykład ustawić punktu przerwania.  
  
 Pomimo nazwę `upstrFullyQualifiedMethodPlusOffset`, nazwę metody częściowo kwalifikowanej można przekazać tego parametru. W takim przypadku wybranej metody jest ten, który umieszcza `pAddress`. Sposób ten parametr jest interpretowany zależy od implementacji ewaluatora wyrażeń i język, który go obsługuje.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)