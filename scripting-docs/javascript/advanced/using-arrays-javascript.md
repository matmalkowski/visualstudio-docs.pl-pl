---
title: Używanie tablic (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c5218a8353a796128d8b672ecc781665c6bde20
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788788"
---
# <a name="using-arrays-javascript"></a>Używanie tablic (JavaScript)
Stałych w [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] są *rozrzedzonych*. Oznacza to jeśli tablica nie zawierająca trzy elementy, które są numerowane 0, 1 i 2, nie martwiąc się o elementach 3 – 49 można utworzyć elementu 50. Jeśli tablica zmiennej długości automatyczne (zobacz [obiekty wewnętrzne](../../javascript/intrinsic-objects-javascript.md) wyjaśnienie automatyczne monitorowanie długość tablicy), zmiennej długości jest ustawiony na 51, a nie do 4. Można utworzyć tablic, w których są nie przerw w numeracji elementów, ale nie jest wymagane, aby to zrobić.  
  
 W [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], obiekty i tablice są niemal identyczne ze sobą. Dwie najważniejsze różnice są z systemem innym niż Tablica obiektów nie ma właściwości długość automatyczne, czy tablice nie mają właściwości i metod obiektu.  
  
## <a name="addressing-arrays"></a>Adresowanie tablic  
 Tablice adresu przy użyciu nawiasy kwadratowe ([]), jak pokazano w poniższym przykładzie. Wartość liczbowa lub wyrażenie obliczane do liczby całkowitej ująć w nawiasach.  
  
```JavaScript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## <a name="objects-as-associative-arrays"></a>Obiekty jako asocjacyjnych  
 Zwykle używany operator kropki "." Aby uzyskać dostęp do właściwości obiektu. Na przykład  
  
```JavaScript  
myObject.aProperty  
```  
  
 W takim przypadku nazwa właściwości jest identyfikatorem. Właściwości obiektu można także przejść za pomocą operatora indeksu ([]). W takim przypadku obiekt są traktowanie jako *asocjacyjnej* danych wartości są skojarzone z ciągami. Na przykład  
  
```JavaScript  
myObject["aProperty"] // Same as above.  
```  
  
 Operator indeksu jest zazwyczaj skojarzony z uzyskiwania dostępu do elementów tablicy. Gdy jest używany z obiektami, indeksu jest ciągiem literału, która reprezentuje nazwę właściwości.  
  
 Zwróć uwagę, istotnych różnic między dwa sposoby uzyskania dostępu do właściwości obiektu.  
  
1.  Nazwa właściwości jest traktowane jak identyfikator (składni z kropkami (.)) nie może operować, takich jak dane.  
  
2.  Nazwa właściwości jest traktowane jak indeksu (składnia nawiasy klamrowe ([])) może operować, takich jak dane.  
  
 Ta różnica staje się przydatne, jeśli nie wiesz, jakie będą nazw właściwości do środowiska wykonawczego (na przykład, gdy są konstruowanie obiektów, w oparciu o dane wejściowe użytkownika). Aby wyodrębnić wszystkie właściwości z asocjacyjną, należy użyć `for...in` pętli.