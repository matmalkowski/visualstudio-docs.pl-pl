---
title: IDebugObject::GetValue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::GetValue
helpviewer_keywords: IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a9e79c808c02d5c2d04631e6a2981269c5e3a32
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Pobiera wartość obiektu jako serię kolejnych bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pValue`  
 [w, out] Tablica jest wypełniane kolejnych serię bajtów reprezentujący wartość obiektu.  
  
 `nSize`  
 [in] Maksymalna liczba bajtów do pobrania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Pobierz całkowitą liczbę bajtów wartości, które mogą być pobierane przez wywołanie metody [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)