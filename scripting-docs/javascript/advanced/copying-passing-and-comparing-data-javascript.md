---
title: "Kopiowanie, przekazywanie i porównywanie danych (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], passing values
- function parameters
- string comparison
- function parameters, about function parameters
- ByRef argument
- arrays [Visual Studio], setting data types
- arrays [Visual Studio], copying data
- ByVal argument
- string comparison, testing data
ms.assetid: fbccd877-7249-45d4-bd9f-6bcd8ba94a6b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3cf980ca1dfd0c0e09871b6de9756cb2a10364b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="copying-passing-and-comparing-data-javascript"></a>Kopiowanie, przekazywanie i porównywanie danych (JavaScript)
W [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], sposobu obsługi danych zależy od jego typu danych.  
  
## <a name="by-value-vs-by-reference"></a>Przez wartość wersji programu vs. Przez odwołanie  
 Liczby i wartościami logicznymi (**true** i **false**) są kopiowane, przekazane i porównać *przez wartość*. Podczas kopiowania lub przekazywania następuje przydzielenie miejsca w pamięci komputera i skopiowanie do niego wartości oryginału. Jeśli później oryginał ulegnie zmianie, nie będzie to miało wpływu na kopię, ponieważ istnieją dwie odrębne jednostki (zasada działa także w drugą stronę).  
  
 Obiektów, tablic i funkcje są kopiowane, przekazane i porównywane *przez odwołanie*. Podczas kopiowania lub przekazywania według odwołania zasadniczo tworzy się wskaźnik do oryginalnego elementu, po czym używa wskaźnika jako swego rodzaju kopii. Modyfikacja oryginału powoduje zmianę oryginału i kopii (działa również zależność odwrotna). W rzeczywistości istnieje tylko jedna jednostka; „kopia” nie jest faktycznie kopią, a jedynie kolejnym odwołaniem do danych.  
  
 Aby porównanie według odwołania dało wynik pozytywny, dwie zmienne muszą się odwoływać dokładnie do tej samej jednostki. Na przykład dwóch odrębnych **tablicy** obiektów zawsze zostanie porównany jako nierównej, nawet jeśli zawierają one te same elementy. Porównanie da wynik pozytywny, jeśli jedna ze zmiennych jest odwołaniem do drugiej. Aby sprawdzić, jeśli dwie tablice pomieścić te same elementy, porównaj wyniki działania **toString()** metody.  
  
 Wreszcie ciągi są kopiowane i przekazywane według odwołania, ale porównywane według wartości. Należy pamiętać, że jeśli dwie **ciąg** obiektów (utworzone za pomocą **nowe** String("something")), są one porównywane przez odwołanie, ale w przypadku jednego lub obu wartości wartość ciągu, są one porównywane przez wartość.  
  
> [!NOTE]
>  Ze względu na konstrukcję zestawów znaków ASCII i ANSI w sekwencjach wielkie litery następują przed małymi. Na przykład "Zoo" porównuje jako *mniej* niż "aardvark." Możesz wywołać **toUpperCase()** lub **toLowerCase()** na obu ciągów, jeśli chcesz wykonać dopasowanie bez uwzględniania wielkości liter.  
  
## <a name="passing-parameters-to-functions"></a>Przekazywanie parametrów do funkcji  
 W trakcie przekazywania parametru do funkcji według wartości powstaje osobna kopia parametru, która będzie istniała tylko wewnątrz tej funkcji. Mimo że obiekty i tablice są przekazywane według odwołania, w przypadku bezpośredniego zastąpienia ich nowymi wartościami w funkcjach nowe wartości nie są widoczne poza tymi funkcjami. Poza funkcją widać tylko modyfikacje właściwości obiektów oraz elementów tablic.  
  
 Na przykład (przy użyciu modelu obiektów programu Internet Explorer):  
  
```JavaScript  
// This clobbers (over-writes) its parameter, so the change  
// is not reflected in the calling code.  
function Clobber(param)   
{  
    // clobber the parameter; this will not be seen in   
    // the calling code  
    param = new Object();  
    param.message = "This will not work";  
}  
  
// This modifies a property of the parameter, which  
// can be seen in the calling code.  
function Update(param)  
{  
    // Modify the property of the object; this will be seen  
    // in the calling code.  
    param.message = "I was changed";  
}  
  
// Create an object, and give it a property.  
var obj = new Object();  
obj.message = "This is the original";  
  
// Call Clobber, and print obj.message. Note that it hasn't changed.  
Clobber(obj);  
window.alert(obj.message); // Still displays "This is the original".  
  
// Call Update, and print obj.message. Note that is has changed.  
Update(obj);  
window.alert(obj.message); // Displays "I was changed".  
```  
  
## <a name="testing-data"></a>Testowanie danych  
 Wykonywanie testu według wartości polega na porównaniu dwóch odrębnych elementów w celu sprawdzenia, czy są sobie równe. Zwykle porównanie odbywa się bajt po bajcie. Testowanie według odwołania polega na sprawdzeniu, czy dwa elementy odwołują się do tego samego oryginalnego elementu. Jeśli tak, są interpretowane jako równe sobie. Jeśli nie, są uznawane za nierówne sobie, nawet jeśli zawierają dokładnie te same wartości w każdym bajcie.  
  
 Kopiowanie i przekazywanie ciągów według odwołania oszczędza pamięć, ale ponieważ utworzonych ciągów nie można zmienić, możliwe staje się porównywanie ich według wartości. Dzięki temu można sprawdzić, czy dwa ciągi mają taką samą zawartość, nawet jeśli zostały wygenerowane całkowicie odrębnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Obliczanie dat i godzin (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)