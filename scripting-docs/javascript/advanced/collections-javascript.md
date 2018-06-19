---
title: Kolekcje (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 23c26185-6a7b-4b69-9d22-63e1841b4905
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fab554f50f6d2fcdac92c562333e625dc0eb32f6
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2018
ms.locfileid: "27783055"
---
# <a name="collections-javascript"></a>Kolekcje (JavaScript)
Można użyć kolekcji obiektów [mapy](../../javascript/reference/map-object-javascript.md), [ustawić](../../javascript/reference/set-object-javascript.md), i [WeakMap](../../javascript/reference/weakmap-object-javascript.md) do przechowywania obiektów i wartości. Te obiekty oferują wygodne metody dodawania i pobierania elementów członkowskich przy użyciu klucza lub wartości zamiast indeksu. Aby dostęp do elementów członkowskich kolekcji przy użyciu indeksu, należy użyć `Array` obiektu. Aby uzyskać więcej informacji, zobacz [tablic przy użyciu](../../javascript/advanced/using-arrays-javascript.md).  
  
> [!CAUTION]
>  `Map`, `Set`, i `WeakMap` nie są obsługiwane w wersjach przeglądarki przed programu Internet Explorer 11. Aby uzyskać więcej informacji na temat obsługi wersji, zobacz [informacje o wersji](../../javascript/reference/javascript-version-information.md).  
  
## <a name="using-collections"></a>Używanie kolekcji  
 `Map` i `WeakMap` obiektów przechowywać pary klucz wartość i umożliwia dodawanie, pobieranie i usuwanie elementów członkowskich przy użyciu klucza. Ten klucz i wartość mogą być dowolnego typu. `Set` Obiekt przechowuje wartości dowolnego typu.  
  
 `Map` i `Set` obiektów umożliwiają wyliczania elementów kolekcji za pomocą `forEach` — metoda i sprawdzić rozmiar kolekcji przy użyciu `size` metody. `WeakMap` Obiektu, natomiast nie jest wyliczalny. Dla tej kolekcji odwołania kluczy nie są dobrze obsługiwane. Użyj `WeakMap` Jeśli chcesz, aby moduł zbierający elementy bezużyteczne w celu ustalenia, czy aplikacja ma zostać zachowany każdy element członkowski kolekcji w pamięci. Może to być przydatne w scenariuszach buforowania, w których obiekty w pamięci podręcznej są bardzo duże, a nie chcesz niepotrzebnie przechowywać obiektów w pamięci. W niektórych scenariuszach, aby zapobiec przeciekom pamięci, można użyć tego obiektu.  
  
 Poniższy przykład przedstawia użycie `Map` obiektu. W tym przykładzie użytkownik dostęp do elementów członkowskich za pomocą obu `get` i `forEach`. Funkcja wywołania zwrotnego w `forEach` może potrwać maksymalnie trzech parametrów, które zawierają wartość bieżącego elementu kolekcji, klucz bieżącego elementu, a sam obiekt kolekcji.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
document.write(m.get(2));  
document.write("<br />");  
  
m.forEach(function (value, key, mapObj) {  
    document.write(value.toString() + "<br />");  
});  
  
// Output:  
// red  
  
// black  
// red  
// 2  
// 3  
  
```  
  
 Korzystanie z `WeakMap` jest podobny do `Map`, ale można pobrać elementów członkowskich tylko przy użyciu `get`. Na przykład zobacz [WeakMap](../../javascript/reference/weakmap-object-javascript.md) obiektu.  
  
 Poniższy przykład przedstawia użycie `Set` obiektu. W tym przykładzie funkcja wywołania zwrotnego przyjmuje jeden parametr, który jest wartością elementu bieżącej kolekcji.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (value) {  
    document.write(value.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowany język JavaScript](../../javascript/advanced/advanced-javascript.md)