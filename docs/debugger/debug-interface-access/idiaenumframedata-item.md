---
title: IDiaEnumFrameData::Item | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3b2379d1f535583b3ff729342657cf44861c4939
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Pobiera element danych ramki za pomocą indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 indeks  
 [in] Indeks o [idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md) obiektu do pobrania. Indeks znajduje się w zakresie od 0 do `count`-1, gdy `count` zwróconego przez [IDiaEnumFrameData::get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) metody.  
  
 sekcja  
 [out] Zwraca [idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md) obiekt reprezentujący element danych żądanego ramki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumframedata —](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)