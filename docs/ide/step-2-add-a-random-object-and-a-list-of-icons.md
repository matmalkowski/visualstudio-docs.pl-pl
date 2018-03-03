---
title: 'Krok 2: Dodawanie obiektu losowego i listy ikon | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
caps.latest.revision: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c54c94c27b21e120d2e3fe187a6598e0115d737f
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2018
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Krok 2. Dodawanie obiektu losowego i listy ikon
W tym kroku utworzysz zestaw pasujących symboli dla gry. Każdy symbol jest dodawany do dwóch losowych komórek w TableLayoutPanel na formularzu. Aby to zrobić, użyj dwóch `new` instrukcje, aby utworzyć dwa obiekty. Pierwsza to `Random` obiektów, takich jak używana w grze kwizu matematycznych. Jest używany w tym kodzie, aby losowo wybierać komórki w TableLayoutPanel. Drugi obiekt, który może być nowe dla Ciebie, jest `List` obiektu, który jest używany do przechowywania losowo wybranych symboli.

### <a name="to-add-a-random-object-and-a-list-of-icons"></a>Aby dodać obiekt losowy (Random) i listę ikon

1.  W **Eksploratora rozwiązań**, wybierz **pliku Form1.cs** Jeśli używasz programu Visual C# lub **Form1.vb** Jeśli używasz programu Visual Basic, a następnie na pasku menu wybierz **widoku** , **Kod**. Alternatywnie, można wybrać **F7** klucza, lub kliknij dwukrotnie **Form1** w **Eksploratora rozwiązań**.

     Spowoduje to wyświetlenie modułu kodu formularza Form1.

2.  W istniejącym kodzie dodaj następujący kod.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

     Jeśli używasz programu Visual C#, można się, że możesz umieścić kod po otwierającym nawiasie klamrowym i zaraz po deklaracji klasy (`public partial class Form1 : Form`). Jeśli używasz programu Visual Basic, umieść kod bezpośrednio po deklaracji klasy (`Public Class Form1`).

3.  Podczas dodawania `List` obiektów, zwróć uwagę, **IntelliSense** otwartym oknie. Poniżej przedstawiono przykład Visual C#, ale podobny tekst jest wyświetlany po dodaniu listy w Visual Basic.

     ![Okno właściwości przedstawiający kliknij zdarzenie](../ide/media/express_listintellisense.png "Express_ListIntellisense") okna IntelliSense

    > [!NOTE]
    >  Tylko wtedy, gdy ręcznie wprowadzić kod, wyświetlane jest okno IntelliSense. Nie pojawia się, jeśli kopiujesz i wklejasz kod.

     Jeśli spojrzysz na kod (i uwagi) w krótkich sekcjach, jest bardziej zrozumiały. Programy można użyć `List` obiekty do śledzenia wielu różnych typów elementów. Lista może zawierać liczby, wartości true/false, tekst lub inne obiekty. Można także ustawić `List` obiekt przechowujący innych `List` obiektów. Elementy na liście są nazywane *elementy*, a każda lista zawiera tylko jeden typ elementu. Tak więc, lista liczb może zawierać tylko liczby — nie można dodać tekstu do tej listy. Podobnie nie można dodać liczb do listy wartości true/false.

     Po utworzeniu `List` przy użyciu `new` instrukcji, należy określić rodzaj danych, które mają być przechowywane w nim. Dlatego etykietki narzędzia w górnej części **IntelliSense** okno zawiera typy elementów na liście. Ponadto co to jest `List<string>` (języka Visual C#) i `List(Of String)` (w języku Visual Basic) oznacza: jest `List` obiektu, który zawiera elementy `string` — typ danych. Ciąg jest program używa do przechowywania tekstu, czyli jakie etykietki narzędzia w prawo z **IntelliSense** okna jest informacją.

4.  Zastanów się, dlaczego w Visual Basic należy najpierw utworzyć tablicę tymczasową, a w Visual C# lista może być utworzona za pomocą jednej instrukcji. W języku Visual C# ma *inicjatory kolekcji*, które przygotowują na liście, aby zaakceptować wartości. W Visual Basic można używać inicjatora kolekcji. Jednak ze względu na zgodność z poprzednią wersją Visual Basic, zalecamy używanie poprzedniego kodu.

     Jeśli korzystasz z inicjatora kolekcji `new` instrukcji po nowe `List` obiekt jest tworzony, wprowadzany jest on dane dostarczone wewnątrz nawiasów klamrowych. W takim przypadku zostanie wyświetlona lista ciągów o nazwie **ikony**, a tej liście zostanie zainicjowana tak, aby zawierał szesnastu ciągów. Każdy z tych ciągów jest pojedynczą literą, a odpowiadają one wszystkim ikonom, które będą w etykietach. Tak więc gra będzie miała parę wykrzykników, parę wielkich liter N, parę przecinków itd. (Kiedy te znaki są ustawione na czcionkę Webdings, będą one występować jako symbole, takie jak autobus, rower, pająk i tak dalej). Twoje `List` obiekt będzie miał szesnastu ciągi we wszystkich, jeden dla każdej komórki w panelu TableLayoutPanel.

    > [!NOTE]
    >  W języku Visual Basic uzyskania tego samego rezultatu, ale najpierw ciągi są wprowadzane do tablicy, która jest następnie konwertowana do `List` obiektu. Tablica jest podobna do listy, z tym wyjątkiem, że np. tablice są tworzone z ustalonym rozmiarem. Listy można zmniejszać i zwiększać stosownie do potrzeb, co jest istotne w tym programie.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 3: przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 1: utworzenie projektu i Dodawanie tabeli do formularza Your](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).