---
title: Zmienne (JavaScript) | Dokumentacja firmy Microsoft
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
- coercion
- case sensitivity, JavaScript variable name
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1d09f634bd4901e4015766bf55f272926a0a31c
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="variables-javascript"></a>Zmienne (JavaScript)
W [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], zmienna zawiera wartość, na przykład "hello" lub 5. Użycie zmiennej, możesz odwoływać się do danych go reprezentuje, na przykład `NumberOfDaysLeft = EndDate - TodaysDate`.  
  
 Zmienne umożliwiają przechowywanie, pobieranie i manipulowania wartości, które są wyświetlane w kodzie. Spróbuj podać zmiennych znaczące nazwy, aby ułatwić innym osobom zrozumieć, jaki jest Twój kod.  
  
## <a name="declaring-variables"></a>Deklarowanie zmiennych  
 Zmienna zostanie wyświetlony w skrypcie po raz pierwszy jest jego deklaracji. Pierwszy informację o zmiennej konfiguruje go w pamięci, dlatego można mogą odwoływać się do niego później w skrypcie. Zmienne powinny deklarować przed ich użyciem. Można to zrobić przy użyciu `var` — słowo kluczowe.  
  
```JavaScript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 Jeśli nie zainicjować zmiennej użytkownika w `var` instrukcja on automatycznie przyjmuje wartość `undefined`.  
  
## <a name="naming-variables"></a>Nazwy zmiennych  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] jest rozróżniana wielkość liter języka. Oznacza to, że nazwa zmiennej takich jak **Mójlicznik** różni się od nazwy zmiennej **Mójlicznik**. Nazwy zmiennych mogą być o dowolnej długości. Reguły tworzenia prawne nazwy zmiennych są następujące:  
  
-   Pierwszy znak musi być ASCII litery (wielkie lub małe litery), literą, która jest zgodna z konwencji nazewnictwa zmiennej Unicode lub znaku podkreślenia (_). Należy pamiętać, że wiele nie można użyć jako pierwszy znak.  
  
-   Kolejne znaki muszą być litery, cyfry i znaki podkreślenia (_).  
  
-   Nazwa zmiennej nie może być [słowa zarezerwowanego](../javascript/reference/javascript-reserved-words.md).  
  
 Oto kilka przykładów prawidłowych nazw zmiennych:  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 Poniżej przedstawiono przykłady nieprawidłowych nazw zmiennych:  
  
```JavaScript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 Gdy chcesz zadeklarować zmiennej i zainicjować go, ale nie chcesz nadać mu żadnej określonej wartości, przypisz jej wartość `null`. Oto przykład.  
  
```JavaScript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 Jeśli zmienna jest zadeklarowana bez przypisywanie wartości do niego, ma wartość `undefined`. Oto przykład.  
  
```JavaScript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 `null` Wartość zachowuje się jak liczba 0, podczas gdy `undefined` zachowuje się jak specjalna wartość `NaN` (nie liczba). Jeśli `null` wartość i `undefined` wartości są równe.  
  
 Można zadeklarować zmiennej, bez użycia `var` — słowo kluczowe w deklaracji i przypisz jej wartość. Jest to niejawne deklaracji.  
  
```JavaScript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 Nie można użyć zmiennej, która nigdy nie został zadeklarowany.  
  
```JavaScript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## <a name="coercion"></a>Koercja  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] jest słabo typizowana język, w przeciwieństwie do silnie typizowanego w językach C++. Oznacza to, że zmienne JavaScript ma wstępnie określoną typu. Zamiast tego typu zmienną jest typem wartości. To zachowanie umożliwia wartość jest traktowana tak, jakby była innego typu.  
  
 W [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], można wykonać operacji na wartości różnych typów nie powodując wyjątek. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Interpreter niejawnie konwertuje, lub *przekształca wynik dane*, jeden danych typów do drugiego, a następnie wykonuje operację. Reguły dotyczące koercja ciąg, liczbę i wartościami logicznymi są następujące:  
  
-   Jeśli dodasz numer i ciąg, liczbę jest traktowany jak ciąg.  
  
-   Jeśli dodasz wartość logiczną i ciąg, wartość logiczna jest traktowany jak ciąg.  
  
-   Jeśli dodasz numer i wartość logiczną, wartość logiczna jest traktowany jak liczbą.  
  
 W poniższym przykładzie do dodawany numer wyników ciągu w ciągu.  
  
```JavaScript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 Ciągi automatycznie są konwertowane na równoważne liczby w celu porównania. Aby jawnie przekonwertować ciąg na liczbę całkowitą, należy użyć [funkcja parseInt](../javascript/reference/parseint-function-javascript.md). Aby jawnie przekonwertować ciąg na liczbę, należy użyć [funkcja parseFloat](../javascript/reference/parsefloat-function-javascript.md).