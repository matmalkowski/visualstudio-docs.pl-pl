---
title: IDiaInjectedSource::get_sourceCompression | Dokumentacja firmy Microsoft
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
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 68b0d80d57e8e29aa326946b6cf94fe119ca30fd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiainjectedsourcegetsourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Pobiera wskaźnik źródła kompresji używany.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca wskaźnik źródła kompresji używany. Wartość zero oznacza, użyto bez źródła kompresji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez tę metodę jest specyficzne dla kompilatora używane. Na przykład kompilatora może użyć kodowania długości Uruchom lub stylu Huffmana kompresji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)