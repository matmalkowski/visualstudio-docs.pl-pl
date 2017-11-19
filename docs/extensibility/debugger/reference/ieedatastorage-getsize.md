---
title: IEEDataStorage::GetSize | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEDataStorage::GetSize
helpviewer_keywords: IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dd0ec398877a581109f864411ede684147e86ebd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Zwraca liczbę bajtów zawartych w tym obiekcie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSize(  
   ULONG* size  
);  
```  
  
```csharp  
int GetSize(  
   out uint size  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `size`  
 [out] Liczba bajtów zawartych w tym obiekcie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Użyj [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) metoda pobierania bajtów danych rzeczywistych.  
  
## <a name="see-also"></a>Zobacz też  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)