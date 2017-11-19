---
title: IDebugField::GetAddress | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetAddress
helpviewer_keywords: IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 499606cab18fa8eac4c1e9dcee72aed094cc84a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldgetaddress"></a>IDebugField::GetAddress
Ta metoda pobiera adres debugowania pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAddress(   
   IDebugAddress** ppAddress  
);  
```  
  
```csharp  
int GetAddress(  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppAddress`  
 [out] Zwraca adres jako [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)