---
title: IDiaSegment::get_read | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSegment::get_read method
ms.assetid: aafbc86d-352c-4e1a-911a-1472d2d59212
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 119007e4a53cbdce6bfb8bfd59c27cafada351ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasegmentgetread"></a>IDiaSegment::get_read
Pobiera flagę wskazującą, czy mogą być odczytywane segmentu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_read (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca `TRUE` Jeśli segment mogą być odczytywane; w przeciwnym razie zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)