---
title: Debugowanie LINQ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52b4c9eb74207e966c17a212b9a9181293581297
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-linq"></a>Debugowanie LINQ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] obsługuje debugowania języka zintegrowane zapytania (LINQ) kodu, z pewnymi ograniczeniami. Najbardziej debugowania funkcje działają w instrukcjach LINQ, w tym wykonywanie krok po kroku, ustawianie punktów przerwania i wyświetlania wyników w oknach debugera. W tym temacie opisano głównych ograniczenia debugowanie LINQ.  
  
##  <a name="BKMK_ViewingLINQResults"></a> Wyświetlanie wyników LINQ  
 Wyniki instrukcji LINQ można wyświetlać przy użyciu etykietek danych, okno czujki i QuickWatch — okno dialogowe. Korzystając z okna źródła, w przypadku wstrzymania wskaźnik myszy na zapytania w oknie źródła i pojawi się etykietki danych. Można skopiować zmienną LINQ i wklej go do okna czujki lub QuickWatch — okno dialogowe.  
  
 W składniku LINQ zapytania nie jest oceniany, podczas tworzenia lub zadeklarowana, ale tylko wtedy, gdy jest używany w zapytaniu. Zapytanie nie ma w związku z tym wartość, dopóki nie będzie oceniana. Pełny opis tworzenia zapytań i oceny, zobacz [wprowadzenie do kwerend LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) lub [Your pierwszego zapytania LINQ zapisu](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).  
  
 Aby wyświetlić wyniki zapytania, debuger musi być go. Tej oceny niejawne, która występuje podczas wyświetlania wyniku zapytania LINQ w debugerze, ma pewne efekty, które należy wziąć pod uwagę:  
  
-   Każdej oceny zapytania jest czasochłonne. Rozwinięcie węzła wyników jest czasochłonne. Dla niektórych kwerend powtarzane oceny może spowodować zmniejszenie wydajności zauważalne.  
  
-   Obliczenia zapytanie może powodować efekty uboczne, które zmian do wartości danych lub stan programu. Nie wszystkie zapytania ma efekty uboczne. Aby ustalić, czy zapytanie może być bezpiecznie oceniana bez efekty uboczne, trzeba poznać kod, który implementuje zapytania.  
  
##  <a name="BKMK_SteppingAndLinq"></a> Wykonywanie krok po kroku i LINQ  
 Podczas debugowania kodu LINQ krokowe wykonywanie ma pewne różnice funkcjonalne, których należy wiedzieć o.  
  
### <a name="linq-to-sql"></a>LINQ do SQL  
 W składniku LINQ to SQL zapytań predykatu kod jest poza kontrolą debugera. W związku z tym nie można wykonać kroku do predykatu kodu. Wszelkie zapytania, który kompiluje się na drzewo wyrażenia generuje kod, który jest kontrolowany przez debuger.  
  
### <a name="stepping-in-visual-basic"></a>Wykonywanie krok po kroku w języku Visual Basic  
 Gdy są przechodzeniu przez program Visual Basic i debuger napotkał deklaracji zapytania, nie wkroczyć do deklaracji, ale wyróżnia całego deklaracji za pomocą jednej instrukcji. Dzieje się tak, ponieważ zapytanie nie jest oceniany, dopóki nie jest ona wywoływana. Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).  
  
 Jeśli krokowo Poniższy przykładowy kod, debuger prezentuje deklaracji zapytania lub tworzenie zapytań, za pomocą jednej instrukcji.  
  
```  
Function MyFunction(ByVal x As Char)  
    Return True  
End Function  
  
Sub Main()  
    'Query creation  
    Dim x = From it In "faoaoeua" _  
            Where MyFunction(it) _  
            Select New With {.a = it}  
  
    ' Query execution  
    For Each cur In x  
        Console.WriteLine(cur.ToString())  
    Next  
End Sub  
```  
  
 Podczas wykonywania kroków ponownie, debuger wyróżnia `For Each cur In x`. W następnym kroku kroki do funkcji `MyFunction`. Po krokowe `MyFunction`, jego Przechodzi wstecz do `Console.WriteLine(cur.ToSting())`. W żadnym punkcie ona kroków opisanych w predykatu kodu w deklaracji zapytania, mimo że debuger oceny kodu.  
  
### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Zastępowanie predykat funkcji, aby włączyć wykonywania krokowego (Visual Basic)  
 Jeśli do wykonania kroków opisanych predykatu kodu na potrzeby debugowania, można zastąpić predykatu wywołania funkcji, które zawiera oryginalny kod predykatu. Załóżmy na przykład, ten kod:  
  
```  
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Można przenieść kod predykatu nową funkcję o nazwie `IsEven`:  
  
```  
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
...   
Function IsEven(item As =Integer) as Boolean  
      Return item Mod 2 = 0  
End Function  
```  
  
 Poprawione zapytania wywołuje funkcję `IsEven` w każdym przebiegu za pośrednictwem `items`. Można czy każdy element spełnia określony warunek, i można przejrzeć kod w oknach debugera `IsEven`. Predykat w tym przykładzie jest dość proste. Jednak jeśli predykat trudniejsze, z którym masz debugowania, ta metoda może być bardzo przydatne.  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Edytuj i Kontynuuj nie są obsługiwane dla LINQ  
 Edytuj i Kontynuuj obsługuje zmiany do kwerend LINQ z ograniczeniami. Aby uzyskać więcej informacji, zobacz [zmiany obsługiwane EnC](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie SQL](http://msdn.microsoft.com/en-us/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)    
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)   
 [Wprowadzenie do kwerend LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)   
 [Wprowadzenie do LINQ w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)