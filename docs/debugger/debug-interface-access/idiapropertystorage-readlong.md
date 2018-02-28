---
title: IDiaPropertyStorage::ReadLONG | Dokumentacja firmy Microsoft
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
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fca0d07dab3559bbd806a6eb5a34b2a9dbe466eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
Odczytuje `LONG` wartości w zestawie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [in] Identyfikator właściwości do odczytu (`PROPID` jest zdefiniowany w WTypes.h jako `ULONG`).  
  
 `pValue`  
 [out] Zwraca wartość właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_INVALIDARG` Jeśli właściwość nie jest typu `LONG`.  
  
## <a name="remarks"></a>Uwagi  
 A `LONG` jest zdefiniowany przez system Windows jako całkowita 32-bitowych.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)