---
title: IDiaEnumStackFrames::Next | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68e84c31cb98cdbbe69e62aa1e572386100277a0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458710"
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