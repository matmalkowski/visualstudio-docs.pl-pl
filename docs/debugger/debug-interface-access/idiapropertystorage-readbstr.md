---
title: IDiaPropertyStorage::ReadBSTR | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7c8fc8520791228158ad336a7bb709cdbf83a5dc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Odczytuje `BSTR` wartości w zestawie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator właściwości do odczytu (`PROPID` jest zdefiniowany w WTypes.h jako `ULONG`).  
  
 `pValue`  
 [out] Zwraca wartość właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_INVALIDARG` Jeśli właściwość nie jest typu `BSTR`.  
  
## <a name="remarks"></a>Uwagi  
 A `BSTR` jest zdefiniowany przez system Windows jako ciąg znaków typu wide zakończony zerem.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)