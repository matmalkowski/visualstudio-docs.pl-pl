---
title: IDiaEnumStackFrames::Next | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8bfdf9e71bfb13c9f8cc730a33ecb2813e117e5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Pobiera określoną liczbę elementów w ramce stosu z sekwencji wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba elementów stackframe modułu wyliczającego mają zostać pobrane.  
  
 rgelt  
 [out] Tablica, która ma być wypełnione z żądanym [idiastackframe —](../../debugger/debug-interface-access/idiastackframe.md) obiektów.  
  
 pceltFetched  
 [out] Zwraca liczbę stosu ramki elementów w pobranych modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie ma żadnych więcej ramek stosu. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumstackframes —](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)