---
title: IDebugProperty2::SetValueAsReference | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::SetValueAsReference
helpviewer_keywords: IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d27a087c67401e90e8a3f4629c27d1255d0ade75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Ustawia wartość tej właściwości wartość danego odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rgpArgs`  
 [in] Tablica argumenty do przekazania do metody ustawiającej właściwość kodu zarządzanego. Jeśli metoda ustawiająca właściwości nie przyjmuje argumentów lub jeśli [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiektu nie odwołuje się do takich właściwości metody ustawiającej, `rgpArgs` powinien mieć wartości null. Ten parametr jest zwykle wartość null.  
  
 `dwArgCount`  
 [in] Liczba argumentów w `rgpArgs` tablicy.  
  
 `pValue`  
 [in] Odwołanie w formie [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiektu wartości do użycia, aby ustawić tę właściwość.  
  
 `dwTimeout`  
 [in] Jak długo potrwać można ustawić wartości, w milisekundach. Typowe wartości to `INFINITE`. Ma to wpływ na czas prowadzące wszystkie możliwe oceny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca błąd kodu, zazwyczaj jedną z następujących czynności:  
  
|Błąd|Opis|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Ustawienie wartości z odwołania nie jest obsługiwane.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Nie można ustawić wartości, ponieważ ta właściwość odwołuje się do metody.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Wartość jest tylko do odczytu i nie można ustawić.|  
|`E_NOTIMPL`|Metoda nie jest zaimplementowana.|  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)