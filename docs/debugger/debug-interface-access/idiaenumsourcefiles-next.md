---
title: IDiaEnumSourceFiles::Next | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddbb711554289fc53e3f09b3d2129910ad720f6b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
Pobiera określoną liczbę plików źródłowych w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Next (   
   ULONG            celt,  
   IDiaSourceFile** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba pliki źródłowe do pobrania modułu wyliczającego.  
  
 rgelt  
 [out] Tablica, która ma być wypełnione przy użyciu [idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md) obiekty reprezentujące pliki źródłowe żądany.  
  
 pceltFetched  
 [out] Zwraca liczbę plików źródłowych w pobranych modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie ma żadnych więcej plików źródła. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumsourcefiles —](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)