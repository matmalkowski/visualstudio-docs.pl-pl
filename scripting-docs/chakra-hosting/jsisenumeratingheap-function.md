---
title: "Jsisenumeratingheap — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsIsEnumeratingHeap
helpviewer_keywords: JsIsEnumeratingHeap function
ms.assetid: 5d14518e-3153-43f2-9a9c-068580cbd54f
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ff27c12dce29d03d2516dfd7cfba34f22020da3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsisenumeratingheap-function"></a>JsIsEnumeratingHeap — Funkcja
Zwraca wartość wskazującą, czy jest wyliczany sterty bieżącego kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsIsEnumeratingHeap(  
   _Out_ bool *isEnumeratingHeap  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isEnumeratingHeap`  
 Określa, czy sterty jest wyliczany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Wymaga kontekstu aktywnego skryptu.  
  
 Ten interfejs API jest obsługiwane w aplikacjach klasycznych, ale nie jest obsługiwane w aplikacjach w sklepie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)