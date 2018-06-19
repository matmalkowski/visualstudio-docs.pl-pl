---
title: split — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- split
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- split method
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea90dda2e8e4d52451af247d139eeee44f83917
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791599"
---
# <a name="split-method-string-javascript"></a>split — Metoda (Ciąg) (JavaScript)
Dzieli ciąg na podciągi przy użyciu określonego separatora i zwraca je jako tablicę.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. `String` Obiektu lub literału ciągu do podziału. Ten obiekt nie jest modyfikowany przez **podzielić** metody.  
  
 `separator`  
 Opcjonalny. Ciąg lub a **wyrażenia regularnego** obiekt, który identyfikuje znak lub używanych do oddzielania ciąg znaków. W przypadku pominięcia zwracana jest jednoelementowa tablica zawierająca cały ciąg.  
  
 `limit`  
 Opcjonalny. Wartość używana do ograniczania liczby elementów zwracanych w tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik **podzielić** metoda jest tablicą ciągów podziału w każdym punkcie gdzie `separator` występuje w `stringObj`. `separator` Nie są zwracane jako część każdy element tablicy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **podzielić** metody.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Metoda concat (ciąg)](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp — obiekt](../../javascript/reference/regexp-object-javascript.md)   
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Przewijanie, przesuwać i powiększać przykładowej aplikacji](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)