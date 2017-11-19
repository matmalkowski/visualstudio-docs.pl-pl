---
title: "Jsenumerateheap — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsEnumerateHeap
helpviewer_keywords: JsEnumerateHeap function
ms.assetid: 3e518e0b-b959-4686-899c-83e6b1946c9d
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48d7698218df49b8ffd680cf26df370c2f97b7c0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsenumerateheap-function"></a>JsEnumerateHeap — Funkcja
Wylicza sterty bieżącego kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsEnumerateHeap(  
   _Out_ IActiveScriptProfilerHeapEnum **enumerator  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `enumerator`  
 Moduł wyliczający stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Podczas wyliczania sterty, nie można usunąć bieżącego kontekstu, a wszystkie wywołania do modyfikowania stanu kontekstu zakończy się niepowodzeniem, dopóki zwolnieniu modułu wyliczającego sterty.  
  
 Wymaga kontekstu aktywnego skryptu.  
  
 Ten interfejs API jest obsługiwane w aplikacjach klasycznych, ale nie jest obsługiwane w aplikacjach w sklepie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)