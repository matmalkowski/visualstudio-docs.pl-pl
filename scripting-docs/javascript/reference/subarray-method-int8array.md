---
title: Metoda subarray (Int8Array) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e32c3a0da7e3173273eb40bf52bb6583bd77df51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-int8array"></a>Metoda subarray (Int8Array)
Pobiera nowy widok Int8Array magazynu ArrayBuffer dla tej tablicy, odwołując się do elementów od początkowego, włącznie, aż do końcowego, wyłącznie.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## <a name="parameters"></a>Parametry  
 `newInt8Array`  
 Podtablica zwracana przez tę metodę.  
  
 `begin`  
 Indeks początku tablicy.  
  
 `end`  
 Indeks końca tablicy. Jest to wyłącznie.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli któraś z wartości begin lub end jest ujemna, to dotyczy indeksu liczonego od końca tablicy, a nie od początku. Jeśli parametr end jest nieokreślony, podtablica zawiera wszystkie elementy od początku do końca tablicy TypedArray. Zakres określony przez wartości begin i end jest powiązany z prawidłowym zakresem indeksu dla bieżącej tablicy. Jeśli obliczona długość nowej tablicy TypedArray będzie ujemna, zostanie ona zablokowana na poziomie wartości zero. Zwracana tablica TypedArray będzie tego samego typu, co tablica, na której ta metoda jest wywoływana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uzyskać podtablicę o długości dwóch elementów, poczynając od pierwszego elementu tablicy.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]