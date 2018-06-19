---
title: Pisanie kodu JavaScript | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.htmldesigner.html
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- code, JavaScript syntax
- comments, JavaScript code
- JavaScript code
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e50bc25f818724b59d9adda51f97d76ae14de2b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792199"
---
# <a name="writing-javascript-code"></a>Pisanie kodu JavaScript
Jak wiele innych języków programowania, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] są zorganizowane w instrukcji, bloków składające się z zestawów powiązanych instrukcje i komentarze. W instrukcji można użyć zmiennych, ciągów, liczb i wyrażenia.  
  
## <a name="statements"></a>Instrukcje  
 A [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] programu jest to zbiór instrukcji. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]Instrukcje wyrażeń w taki sposób, że przeprowadzać ukończenia zadania.  
  
 Instrukcję składa się z co najmniej jednego wyrażenia, słowa kluczowe lub operatory (symboli). Zazwyczaj instrukcji są zapisywane w jednym wierszu, mimo że instrukcja mogą być zapisywane w dwóch lub więcej wierszy. Ponadto co najmniej dwie instrukcje mogą być zapisywane w tym samym wierszu, oddzielając je średnikami. Ogólnie rzecz biorąc każdy nowy wiersz rozpoczyna się nowy raport. Należy dobrze jest jawnie przerwanie oficjalnych dokumentów. Aby to zrobić z średnika (;), który jest [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] znaków przerwanie instrukcji.  
  
 Poniżej przedstawiono dwa przykłady [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] instrukcje. Zdania po / / znaki są *komentarze*, które są uwagi wyjaśniające w programie.  
  
```JavaScript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Grupa [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] instrukcje ujęte w nawiasy klamrowe ({}) jest nazywany *bloku*. Instrukcje zgrupowane w bloku ogólnie może być traktowana jako pojedynczej instrukcji. Oznacza to, mogą używać bloków w większości umieszcza [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] oczekuje jednej instrukcji. Godnymi uwagi wyjątkami obejmują nagłówki **dla** i `while` pętli. Zwróć uwagę, pojedynczy instrukcje w bloku kończyć się średnikami, że nie ma tego samego bloku.  
  
 Ogólnie rzecz biorąc bloki są używane w funkcjach i korzystania z tej możliwości. Zwróć uwagę, że w przeciwieństwie do języka C++ i innych języków [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ma należy traktować jako nowy zakres bloku; tylko funkcje, Utwórz nowy zakres.  
  
 W poniższym przykładzie `else` klauzula zawiera blok instrukcji dwóch ujęte w nawiasy klamrowe. Blok jest traktowany jako pojedynczej instrukcji. Ponadto ta funkcja składa się z blok instrukcji ujęte w nawiasy klamrowe. Instrukcje poniżej funkcja są poza blokiem i dlatego nie są częścią definicji funkcji.  
  
```JavaScript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## <a name="comments"></a>Komentarze  
 Jeden wiersz [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] komentarz, który rozpoczyna się od dwa ukośniki (/ /). Oto przykład jednowierszowego komentarza.  
  
```JavaScript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Wielowierszowym formancie [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] komentarz, który rozpoczyna się od ukośnika i gwiazdki (/\*) i kończy odwrotnej (\*/).  
  
```JavaScript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  Przy próbie osadzić jeden komentarz wielowierszowy w innym [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interpretuje wynikowy komentarz wielowierszowy w nieoczekiwany sposób. * / Który oznacza koniec osadzonego komentarz wielowierszowy jest interpretowana jako końca komentarza całego wielowierszowy. Oznacza to, że tekst następujący osadzonych komentarz wielowierszowy nie zostaną oznaczone jako komentarz; Zamiast tego będzie interpretowana jako [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] kodu i będzie generować błędy składni.  
  
 Zaleca się zapisać swoje komentarze jako bloki jednowierszowego komentarza. Dzięki temu można przekształcić w komentarz dużych segmentów kodu z komentarz wielowierszowy później.  
  
```JavaScript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## <a name="assignments-and-equality"></a>Przydziały i równości  
 Znak równości (=) jest używany w [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] instrukcji można przypisać wartości do zmiennych: jest operator przypisania. Argument operacji po lewej stronie = — operator jest zawsze l-wartością. Lvalues należą:  
  
-   zmienne,  
  
-   elementy tablicy  
  
-   właściwości obiektu.  
  
 Prawy argument operacji = — operator jest zawsze r-wartości. Rvalues może być dowolną wartość dowolnego typu, łącznie z wartości wyrażenia. Oto przykład [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] instrukcji przypisania.  
  
```JavaScript  
var anInteger = 3;  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Kompilatora interpretuje tej instrukcji jako znaczenie: "przypisać wartość 3 zmiennej **anInteger**," lub "**anInteger** przyjmuje wartość 3."  
  
 Można niektórych zrozumieć różnicę między = — operator (przypisanie) i == — operator (równości). Do porównania dwóch wartości, aby sprawdzić, czy są równe, należy użyć dwóch znaków równości (==). To jest omówiona szczegółowo w [sterowanie przepływem programu](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="expressions"></a>Wyrażenia  
 A [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] wartość wyrażenia może być żadnych poprawnych [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] type - liczbą, ciąg obiektu i tak dalej. Najprostsza wyrażenia są literały. Poniżej przedstawiono kilka przykładów [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] wyrażeń literałów.  
  
```JavaScript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Bardziej złożonych może zawierać zmiennych, wywołania funkcji i inne wyrażenia. Możesz łączyć wyrażenia do tworzenia złożonych wyrażeń przy użyciu operatorów. Przykłady operatory: `+` (Dodawanie) `-` (odejmowanie) `*` (mnożenie) i `/` (dział).  
  
 Poniżej przedstawiono kilka przykładów [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] złożonych wyrażeń.  
  
```JavaScript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```