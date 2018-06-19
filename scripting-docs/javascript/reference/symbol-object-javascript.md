---
title: Symbol — obiekt (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2ad059f1-4b7f-4758-882a-c74ce1283ab0
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd755d5b753eb91b89b869645287685a97f8f571
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791902"
---
# <a name="symbol-object-javascript"></a>Symbol — obiekt (JavaScript)
Pozwala utworzyć unikatowy identyfikator.  
  
## <a name="syntax"></a>Składnia  
  
```  
obj = Symbol(desc)  
```  
  
#### <a name="parameters"></a>Parametry  
 `desc`  
 Opcjonalny. Opis symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Obiekty symbol umożliwia właściwości mają zostać dodane do istniejących obiektów z możliwości ingerencji z istniejącej właściwości obiektów, nie niezamierzone widoczność i innych dodatków nieskoordynowane przez inny kod.  
  
 Symbol jest typem danych pierwotnych. Nie można utworzyć obiektów symbol przy użyciu `new` operatora.  
  
 Aby dodać symbol obiekty rejestru globalnego symbolu, użyj `Symbol.for` i `Symbol.keyFor` funkcji. Jeśli serializować symboli jako ciągi, umożliwia rejestru symbol globalnego upewnij się, że określony ciąg mapowana poprawne symbol dla wszystkich wyszukiwań.  
  
 JavaScript obejmuje następujące wartości symbol wbudowany, które są dostępne w zakresie globalnym.  
  
|Symbol|Opis|  
|------------|-----------------|  
|`Symbol.hasInstance`|Ta metoda określa, czy obiekt konstruktora rozpoznaje obiekt jako jedno wystąpienie konstruktora. Jest używana wewnętrznie przez `instanceof` operatora.|  
|`Symbol.isConcatSpreadable`|Ta właściwość zwraca wartość logiczną wskazującą, czy obiekt powinien jako spłaszczone do jego elementów tablicy przez `Array.concat`.|  
|`Symbol.iterator`|Ta metoda zwraca iteratora domyślny dla obiekt. Jest używana wewnętrznie przez `for...of` instrukcji.|  
|`Symbol.toPrimitive`|Ta metoda Konwertuje obiekt odpowiadającej jej wartości pierwotnych. Jest używana wewnętrznie przez `ToPrimitive` abstrakcyjnej działania.|  
|`Symbol.toStringTag`|Ta właściwość zwraca wartość ciągu, która jest używana w celu tworzenia domyślny opis ciągu obiektu. Jest używana wewnętrznie przez metodę wbudowanych `Object.toString` metody.|  
|`Symbol.unscopables`|Ta właściwość zwraca obiekt, którego właściwości są wykluczone z `with` powiązań środowiska skojarzonego obiektu.|  
  
## <a name="functions"></a>Funkcje  
 W poniższej tabeli wymieniono funkcje `Symbol` obiektu.  
  
|||  
|-|-|  
|Właściwość|Opis|  
|[Symbol.for —](../../javascript/reference/symbol-for-function-javascript.md)|Zwraca symbol dla określonego klucza, lub jeśli klucz nie jest obecny, tworzy nowy obiekt symbol za pomocą nowego klucza.|  
|[Symbol.keyfor —](../../javascript/reference/symbol-keyfor-function-javascript.md)|Zwraca klucz dla określonego symbolu.|  
|||  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
(function() {  
  
    // module-scoped symbol  
    var key = Symbol("description");  
  
    function MyClass(privateData) {  
      this[key] = privateData;  
    }  
  
    MyClass.prototype = {  
      someFunc: function() {  
        return "data: " + this[key];  
      }  
    };  
  
    var c = new MyClass("private data")  
    console.log(key);  
    console.log(c["key"]);  
    console.log(c.someFunc());  
  
})();  
  
// Output:  
// undefined  
// undefined  
// data: private data  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]