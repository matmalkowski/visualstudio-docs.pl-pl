---
title: for — instrukcja (JavaScript) | Dokumentacja firmy Microsoft
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
- for_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, for statements
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7142dbb8c00a351918d0821c3ca7dba3d7b2acb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790651"
---
# <a name="for-statement-javascript"></a>for — Instrukcja (JavaScript)
Wykonuje bloku instrukcji dla tak długo, jak określony warunek jest spełniony.  
  
## <a name="syntax"></a>Składnia  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## <a name="parameters"></a>Parametry  
 `initialization`  
 Opcjonalny. Wyrażenie. To wyrażenie jest wykonywane tylko raz, przed wykonaniem pętli.  
  
 `test`  
 Opcjonalny. Wyrażenie logiczne. Jeśli `test` jest `true`, `statement` jest wykonywana. Jeśli `test` Jeśli `false`, pętla zostanie zakończony.  
  
 `increment`  
 Opcjonalny. Wyrażenie. Wyrażenie przyrostowe jest wykonywana na końcu każdej przekazywania pętli.  
  
 `statement`  
 Opcjonalny. Co najmniej jeden instrukcje do wykonania, jeśli `test` jest **true**. Może być złożonej instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj jest używany `for` pętli po pętli, należy wykonać znane wiele razy. A `for` pętla jest przydatne do Iterowanie przez tablice za i wykonywania przetwarzania sekwencyjnych.  
  
 Występuje przed wykonywania pętli, więc testu wyrażenie warunkowe `for` zero lub więcej razy wykonywania instrukcji.  
  
 Na każdej linii w `for` blok instrukcji pętli, można użyć `break` oświadczenie zakończenie pętli, albo można użyć `continue` instrukcji do przekazywania kontroli do następnej iteracji pętli.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `for` instrukcji wykonuje instrukcje zamknięte w następujący sposób:  
  
-   Po pierwsze, początkowej wartości zmiennej `i` oceny.  
  
-   Następnie, tak długo, jak wartość `i` jest mniejsza niż 9, `document.write` instrukcje są wykonywane i `i` jest ponownie oceniane.  
  
-   Gdy `i` jest większa niż 9, przestanie być spełniony warunek i sterowania są przesyłane poza pętli.  
  
```JavaScript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## <a name="example"></a>Przykład  
 Wszystkie wyrażenia z `for` instrukcji są opcjonalne. W poniższym przykładzie `for` instrukcje tworzenia nieskończoną pętlę, a `break` używana jest instrukcja, aby zakończyć pętli.  
  
```JavaScript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [for... w instrukcji](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while — instrukcja](../../javascript/reference/while-statement-javascript.md)