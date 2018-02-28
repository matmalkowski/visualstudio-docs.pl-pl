---
title: "Jsserializescript — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSerializeScript
helpviewer_keywords:
- JsSerializeScript function
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92bc6c1de0f2cd43dfe9566413fb64188fd5a382
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializescript-function"></a>JsSerializeScript — Funkcja
Serializuje przeanalizowany skryptu w buforze, nie mogą być ponownie używane.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `script`  
 Skrypt do serializacji.  
  
 `buffer`  
 Bufor umieścić serializacji skrypt do. Może być równa zeru.  
  
 `bufferSize`  
 Podczas wprowadzania — rozmiar buforu, w bajtach; Po zakończeniu rozmiar buforu, w bajtach, wymagane do przechowywania skryptów serializacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 `JsSerializeScript`analizuje skrypt, a następnie zapisuje przeanalizowane formularza skryptu w formacie niezależnym od środowiska wykonawczego. Skrypt serializacji następnie może być zdeserializowany w dowolnym środowisku uruchomieniowym bez konieczności ponownie przeanalizowane skryptu.  
  
 Wymaga kontekstu aktywnego skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)