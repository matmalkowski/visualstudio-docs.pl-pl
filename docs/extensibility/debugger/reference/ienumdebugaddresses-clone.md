---
title: IEnumDebugAddresses::Clone | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugAddresses::Clone
helpviewer_keywords: IEnumDebugAddresses::Clone method
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89ad14a37966b81235a100d3102e80bddb978782
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugaddressesclone"></a>IEnumDebugAddresses::Clone
Ta metoda zwraca kopię bieżącego wyliczenie jako oddzielny obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Clone(  
   IEnumDebugAddresses** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugAddresses ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca kopię tego wyliczenia jako oddzielny obiekt.  
  
## <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kopiuj wyliczenia ma takim samym stanie, co oryginalne w czasie, gdy ta metoda zostanie wywołana. Jednak kopiowania i oryginalny stan są oddzielone i można zmieniać pojedynczo.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)