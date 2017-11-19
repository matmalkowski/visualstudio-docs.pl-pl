---
title: "Używanie konstruktorów w celu definiowania typów | Dokumentacja firmy Microsoft"
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
- creating objects, constructor functions
- constructor functions
- functions, constructor functions
- objects, creating [JavaScript]
- constructors, creating
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bff42606fda27e00a537cc227a0b636e016f7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="using-constructors-to-define-types"></a>Używanie konstruktorów w celu definiowania typów
Konstruktor to funkcja, która tworzy wystąpienie określonego typu [obiektu](../../javascript/objects-and-arrays-javascript.md). Wywołanie konstruktora z **nowe** — słowo kluczowe. Oto kilka przykładów konstruktorów z wbudowanymi obiektami JavaScript i obiektami niestandardowymi.  
  
## <a name="constructor-examples"></a>Przykłady konstruktorów  
  
```JavaScript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 Funkcja konstruktora zawiera **to** — słowo kluczowe, w której jest odwołanie do nowo utworzony obiekt puste. Inicjuje nowy obiekt przez tworzenie właściwości i przyznanie im wartości początkowych. Konstruktor zwraca odwołanie do obiektu, który wygenerował.  
  
## <a name="writing-constructors"></a>Konstruktorzy pisania  
 Można utworzyć obiektów przy użyciu **nowe** operatora w połączeniu z takich jak wstępnie zdefiniowane funkcje konstruktora **Object()**, **Date()**, i **Function()** . Możesz również tworzyć niestandardowe funkcje konstruktora, które definiują zestaw właściwości i metody. Oto przykład niestandardowego konstruktora.  
  
```JavaScript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 Kiedy wywołujesz konstruktora Circle, podajesz wartości dla środka okręgu i promienia. Otrzymujesz obiekt Circle, który ma trzy właściwości. Oto jak można utworzyć obiekt Circle.  
  
```JavaScript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 Wszystkie obiekty utworzone za pomocą konstruktora niestandardowy jest `object`. Istnieje tylko sześć typów w języku JavaScript: `object`, `function`, `string`, `number`, `boolean`, i `undefined`. Aby uzyskać więcej informacji, zobacz [typeof — Operator](../../javascript/reference/typeof-operator-decrementjavascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie metody bind](../../javascript/advanced/using-the-bind-method-javascript.md)