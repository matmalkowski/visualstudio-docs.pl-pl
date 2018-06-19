---
title: Obiekty i tablice (JavaScript) | Dokumentacja firmy Microsoft
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
helpviewer_keywords:
- arrays [JavaScript]
- arrays [JavaScript], objects
ms.assetid: f5106284-1240-4f47-8c3b-5a45e227e5e1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6776701ba108ae0ecefc2331c2b12272e0c1be19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789133"
---
# <a name="objects-and-arrays-javascript"></a>Obiekty i tablice (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)]obiekty są kolekcjami właściwości i metod. Metoda to funkcja, która jest elementem członkowskim obiektu. Właściwość jest wartość lub zbiór wartości (w postaci tablicy lub obiektu), który jest elementem członkowskim obiektu. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]obsługuje cztery typy obiektów:  
  
-   Obiekty wewnętrznych, takich jak `Array` i `String`.  
  
-   Obiekty utworzone samodzielnie.  
  
-   Host obiekty, takie jak `window` i `document`.  
  
-   Obiektów ActiveX.  
  
## <a name="expando-properties-and-methods"></a>Właściwości i metody Expando  
 Wszystkie obiekty w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] obsługuje expando właściwości i metody, które mogą być dodawane lub usuwane w czasie wykonywania. Te właściwości i metody może mieć dowolną nazwę i mogą zostać zidentyfikowane na podstawie liczby. Jeśli nazwa właściwości lub metody jest prostym identyfikatorem, jego mogą być zapisywane po nazwie obiektu kropką, takich jak `myObj.name`, `myObj.age`, i `myObj.getAge` w następującym kodzie:  
  
```JavaScript  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.age = 42;  
  
myObj.getAge =   
    function () {  
        return this.age;  
    };  
  
document.write(myObj.name);  
document.write("<br/>");  
document.write(myObj.age);  
document.write("<br/>");  
document.write(myObj.getAge());  
  
// Output:  
// Fred  
// 42  
// 42  
  
```  
  
 Jeśli nazwa właściwości lub metody nie jest identyfikatorem prostego lub jest nieznany w momencie pisania skryptu, można wyrażenia w nawiasach kwadratowych indeksu właściwości. Nazwy wszystkich właściwości expando w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] są konwertowane na ciągi przed dodaniem go do obiektu.  
  
```JavaScript  
var myObj = new Object();  
  
// Add two expando properties that cannot be written in the  
// object.property syntax.  
// The first contains invalid characters (spaces), so must be  
// written inside square brackets.  
myObj["not a valid identifier"] = "This is the property value";  
  
// The second expando name is a number, so it also must  
// be placed inside square brackets  
myObj[100] = "100";  
```  
  
 Informacji o tworzeniu obiektu z definicji, zobacz [Tworzenie obiektów](../javascript/creating-objects-javascript.md).  
  
## <a name="arrays-as-objects"></a>Użycie tablic jako obiektów  
 W [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], obiekty i tablice obsługiwane są niemal identyczne, ponieważ tablic są jedynie specjalny rodzaj obiektu. Zarówno obiekty i tablice mogą mieć właściwości i metody.  
  
 Tablice mają `length` właściwość obiektów, ale nie chcesz. Po przypisaniu wartość do elementu tablicy której indeksu jest większa niż długość (na przykład `myArray[100] = "hello"`), `length` właściwości automatycznie zostaje zwiększona do nowego długości. Podobnie jeśli wprowadzisz `length` właściwości mniejszych dowolny element, którego indeks wykracza poza długość tablicy jest usuwany.  
  
```JavaScript  
// An array with three elements  
var myArray = new Array(3);  
  
// Add some data  
myArray[0] = "Hello";  
myArray[1] = 42;  
myArray[2] = new Date(2000, 1, 1);  
  
document.write("original length is: " + myArray.length);  
document.write("<br/>");  
// Add some expando properties  
myArray.expando = "JavaScript!";  
myArray["another Expando"] = "Windows";  
  
// This will still display 3, since the two expando properties  
// don't affect the length.  
document.write("new length is : " + myArray.length);  
  
// Output:  
// original length is: 3  
// new length is : 3  
  
```  
  
 Tablice udostępniają metody iteracyjne i manipulowania elementów członkowskich. Poniższy przykład pokazuje, jak uzyskać właściwości obiekty przechowywane w tablicy.  
  
```JavaScript  
var myArray = new Array(3);  
  
// Add some data  
for(var i = 1; i <= 3; i++) {  
    myArray[i] = new Date(2000 + i, 1, 1);  
}  
  
myArray.forEach(function (item) {  
    document.write(item.getFullYear());  
});  
  
// Output:  
// 2001  
// 2002  
// 2003  
```  
  
## <a name="multi-dimensional-arrays"></a>Wielowymiarowe tablice  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]jest bezpośrednio tablic wielowymiarowych pomocy technicznej, ale można uzyskać zachowanie tablic wielowymiarowych przechowywanie tablic w elementach innej tablicy. (Można przechowywać dowolny rodzaj danych wewnątrz elementów tablicy, w tym tablic). Na przykład poniższy kod tworzy tabelę mnożenia dla cyfr liczącą do 5.  
  
```JavaScript  
// The size of the table.  
var iMaxNum = 5;  
// Loop counters.  
var i, j;  
  
// Set the length of the array to iMaxNum + 1.   
// The first array index is zero, not 1.  
var MultiplicationTable = new Array(iMaxNum + 1);  
  
// Loop for each major number (each row in the table)  
for (i = 1; i <= iMaxNum; i++)  
{  
    // Create the columns in the table  
    MultiplicationTable[i] = new Array(iMaxNum + 1);  
  
    // Fill the row with the results of the multiplication  
    for (j = 1; j <= iMaxNum; j++)  
    {  
        MultiplicationTable[i][j] = i * j;  
    }  
}  
  
document.write(MultiplicationTable[3][4]);  
document.write("<br/>");   
document.write(MultiplicationTable[5][2]);  
document.write("<br/>");  
document.write(MultiplicationTable[1][4]);  
  
// Output:  
// 12  
// 10  
// 4  
  
```