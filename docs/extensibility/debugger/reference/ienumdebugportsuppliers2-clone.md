---
title: IEnumDebugPortSuppliers2::Clone | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPortSuppliers2::Clone
helpviewer_keywords: IEnumDebugPortSuppliers2::Clone
ms.assetid: 98b9914d-4f32-44da-b422-68830bce44b4
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 611399ed8bd403b0f8f19f0b62e1743fab4cb525
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugportsuppliers2clone"></a>IEnumDebugPortSuppliers2::Clone
Zwraca kopię bieżącego wyliczenie jako oddzielny obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Clone(  
   IEnumDebugPortSuppliers2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugPortSuppliers2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca kopię tego wyliczenia jako oddzielny obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kopiuj wyliczenia ma takim samym stanie, co oryginalne w czasie, gdy ta metoda zostanie wywołana. Jednak kopiowania i oryginalny stan są oddzielone i można zmieniać pojedynczo.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)