---
title: Jscreatetypedarray — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df33d0e1aadec9d7ed5aebf743e2c2f840e51fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788407"
---
# <a name="jscreatetypedarray-function"></a>JsCreateTypedArray — funkcja
Tworzy obiekt typizowaną tablicę JavaScript.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `arrayType`  
 Typ tablicy, tak aby utworzyć.  
  
 `baseArray`  
 Tablica podstawowej nowej tablicy. Użyj `JS_INVALID_REFERENCE` Jeśli żadna macierz podstawowej.  
  
 `byteOffset`  
 Przesunięcie w bajtach od początku `baseArray` (`ArrayBuffer`) dla wyniku typu tablicy ma dotyczyć odwołanie. Stosuje się tylko w przypadku `baseArray` jest `ArrayBuffer` obiektu. Musi mieć wartość 0 w przeciwnym razie wartość.  
  
 `elementLength`  
 Liczba elementów w tablicy. Stosuje się tylko podczas tworzenia nowej tablicy typu bez `baseArray` (`baseArray` jest `JS_INVALID_REFERENCE`) lub gdy `baseArray` jest `ArrayBuffer` obiektu. Musi mieć wartość 0 w przeciwnym razie wartość.  
  
 `result`  
 Nowy obiekt typu tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kod `JsNoError` Jeśli operacja powiodła się, kod błędu w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 `baseArray` Może być `ArrayBuffer`, innego typu tablicy lub JavaScript `Array`. Użyje zwrócony typizowaną tablicę `baseArray` przypadku `ArrayBuffer`, lub inny sposób tworzenia i używania kopii podstawowej tablicy źródłowej.  
  
 Wymaga kontekstu aktywnego skryptu.  
  
 Ten interfejs API jest obsługiwana tylko w trybie krawędzi.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jsrt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie (środowisko uruchomieniowe JavaScript)](../chakra-hosting/reference-javascript-runtime.md)