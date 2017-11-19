---
title: IDiaPropertyStorage::ReadBSTR | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93ab7271ccef1819e16e4cdb4c690f82bfaeec35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Idiapropertystorage —](../../debugger/debug-interface-access/idiapropertystorage.md)