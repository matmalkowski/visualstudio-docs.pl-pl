---
title: Praca z kodem Visual C++ (Projektant klas)
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 0850fed22caf4b34fcb74aa11eb63f9338b0d5e5
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="work-with-visual-c-code-class-designer"></a>Praca z kodem Visual C++ (Projektant klas)

**Projektant klas** Wyświetla powierzchni wizualnego projektu o nazwie *diagramu klas* zapewnia wizualną reprezentację elementy kodu w projekcie. Diagramy klas służy do projektowania i wizualizacji klasami i innymi typami w projekcie.

**Projektant klas** obsługuje następujące elementy kodu C++:

-   Klasy (podobny kształt zarządzanej klasy, z wyjątkiem tego, że może mieć wiele relacji dziedziczenia)

-   Klasa anonimowego (wyświetla nazwy wygenerowanej klasy widoku dla typu anonimowego)

-   Klasy szablonów

-   Struct

-   Wyliczenie

-   Makra (Wyświetla widok po przetworzonych makra)

-   Element TypeDef

> [!NOTE]
> Nie jest taka sama jak diagram klas UML, które można utworzyć w projekcie modelowania. Aby uzyskać więcej informacji, zobacz [diagramów klas UML: odwołanie](../../modeling/uml-class-diagrams-reference.md).

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Rozwiązywanie problemów z rozpoznawania typu i Wyświetl problemy

### <a name="location-of-source-files"></a>Lokalizację plików źródłowych

**Projektant klas** nie zachować informacje o lokalizacji plików źródłowych. W związku z tym, jeśli Twoje zmiany struktury projektu lub Przenieś pliki źródłowe w projekcie, **Projektant klas** może spowodować utratę Śledź typu (szczególnie typ źródła jako element typedef, klas podstawowych lub typów skojarzenia). Błąd może pojawić się takie jak **Projektant klas nie może wyświetlić tego typu**. Jeśli to zrobisz, przeciągnij kod źródłowy zmodyfikowany lub przeniesiono do diagramu klas, aby ją wyświetlić go ponownie.

### <a name="update-and-performance-issues"></a>Problemy z aktualizacji i wydajności

Dla projektów Visual C++ może potrwać 30 – 60 sekund na zmiany w pliku źródłowym do jego wyświetlenia na diagramie klas. To opóźnienie może również spowodować **Projektant klas** ma zostać zgłoszony błąd **w zaznaczenia nie znaleziono żadnych typów**. Jeśli zostanie wyświetlony błąd, takich jak ta, kliknij przycisk **anulować** komunikat o błędzie i poczekaj element kodu w wynikach **widoku klasy**. Po wykonaniu tej czynności **Projektant klas** powinno być możliwe do wyświetlania typu.

Diagram klas nie zaktualizować zmiany wprowadzone w kodzie, konieczne może być zamknij diagram i otwórz go ponownie.

### <a name="type-resolution-issues"></a>Problemy z rozpoznawaniem typu

**Projektant klas** nie może mieć możliwość rozpoznania typy z następujących powodów:

-   Typ jest w projekcie lub zestawu, który nie odwołuje się projekt, który zawiera diagramu klas. Aby rozwiązać ten problem, Dodaj odwołanie do projektu lub zestawu zawierającego typ. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../managing-references-in-a-project.md).

-   Typ nie jest w niewłaściwym zakresie, więc **Projektant klas** nie można go zlokalizować. Upewnij się, że kod nie jest Brak `using`, `imports`, lub `#include` instrukcji. Upewnij się, że nie zostały przeniesione typ (lub powiązanego typu) z przestrzeni nazw, w którym został on pierwotnie znajduje się również.

-   Typ nie istnieje lub została ujęta w komentarz. Aby rozwiązać ten problem, upewnij się, że nie oznaczone jako komentarz lub usunąć typu.

-   Typ znajduje się w bibliotece dyrektywa #import odwołuje się. Możliwym obejściem jest aby ręcznie dodać wygenerowanego kodu (plik .tlh —) # dyrektywy include w pliku nagłówka.

-   Upewnij się, że **Projektant klas** obsługuje typ, który został wprowadzony. Zobacz [ograniczenia dotyczące elementy kodu C++](#limitations-for-c-code-elements).

Błąd najprawdopodobniej wyświetlić problemu rozpoznawania typu jest **nie można odnaleźć kodu dla jednego lub więcej kształtów na diagramie klas '\<elementu > "**. Ten komunikat o błędzie nie musi oznaczać, że kod jest błędny. Oznacza ona, że projektant klas nie może wyświetlić kodu. Spróbuj wykonać następujące działania:

-   Upewnij się, że typ istnieje. Upewnij się, że nie przypadkowo oznaczone jako komentarz lub usunąć kod źródłowy.

-   Spróbuj rozwiązać typu. Typ może być w projekcie lub zestawu, który nie odwołuje się projekt, który zawiera diagramu klas. Aby rozwiązać ten problem, Dodaj odwołanie do projektu lub zestawu zawierającego typ. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../managing-references-in-a-project.md).

-   Upewnij się, że typ jest w niewłaściwym zakresie, dzięki czemu mogą ją odnaleźć Projektant klas. Upewnij się, że kod nie jest Brak `using`, `imports`, lub `#include` instrukcji. Upewnij się, że nie zostały przeniesione typ (lub powiązanego typu) z przestrzeni nazw, w którym został on pierwotnie znajduje się również.

### <a name="troubleshoot-other-error-messages"></a>Rozwiązywanie problemów z inne komunikaty o błędach

Pomoc w rozwiązywaniu problemów błędy i ostrzeżenia można znaleźć na forach publicznego Microsoft Developer Network (MSDN). Zobacz [Forum projektanta klas programu Visual Studio](http://go.microsoft.com/fwlink/?linkid=160754).

## <a name="limitations-for-c-code-elements"></a>Ograniczenia dotyczące elementy kodu C++

-   Po załadowaniu projektu Visual C++ **Projektant klas** funkcje w sposób tylko do odczytu. Można zmienić na diagramie klas, ale nie można zapisać zmian z diagramu klas do kodu źródłowego.

-   **Projektant klas** obsługuje tylko natywny semantykę języka C++. Dla projektów Visual C++, które są kompilowane do kodu zarządzanego **Projektant klas** tylko będzie wizualizacji elementy kodu, które są natywnych typów. W związku z tym można dodać diagram klas do projektu, ale **Projektant klas** nie umożliwia wizualizowanie elementów, w którym `IsManaged` właściwość jest ustawiona na `true` (tzn. typy wartości i typy referencyjne).

-   Dla projektów Visual C++ **Projektant klas** odczytuje tylko definicji typu. Załóżmy na przykład, możesz zdefiniować typu w pliku nagłówków (.h) i definiowanie jej elementów członkowskich w pliku z implementacją (.cpp). Jeśli wywołanie "Widok diagramu klas" w pliku implementacji (.cpp), **Projektant klas** nie wyświetla żadnego obrazu. Innym przykładem, jeśli wywołanie "Widok diagramu klas" w pliku .cpp, który używa `#include` instrukcji, aby uwzględnić inne pliki, ale nie zawiera żadnych definicji klasy rzeczywiste **Projektant klas** ponownie nie wyświetla żadnego obrazu.

-   Pliki języka IDL (.idl), które zdefiniuj interfejsy modelu COM i biblioteki typów, nie są wyświetlane w diagramy, chyba że są one kompilowane do kodu natywnego języka C++.

-   **Projektant klas** nie obsługuje funkcje globalne i zmienne.

-   **Projektant klas** nie obsługuje Unii. Jest to specjalny typ klasy, w którym pamięć przydzielona jest niezbędne dla elementu Członkowskiego Unii największy danych wielkość.

-   **Projektant klas** nie wyświetla danych podstawowych takich jak `int` i `char`.

-   **Projektant klas** nie wyświetla typy, które są zdefiniowane poza bieżącego projektu, jeśli projekt nie ma poprawne odwołania do tych typów.

-   **Projektant klas** można wyświetlić typy zagnieżdżone lecz nie relacje między typem zagnieżdżonym i innych typów.

-   **Projektant klas** nie może wyświetlić typy, które są nieważne lub który pochodzi od typu void.

## <a name="see-also"></a>Zobacz także

- [Projektowanie i wyświetlanie klas i typów](designing-and-viewing-classes-and-types.md)
- [Praca z diagramami klas](working-with-class-diagrams.md)
- [Projektowanie i wyświetlanie klas i typów](designing-and-viewing-classes-and-types.md)
- [Dodatkowe informacje na temat błędów Projektanta klas](additional-information-about-errors.md)
- [Klasy Visual C++ w Projektancie klas](visual-cpp-classes.md)
- [Struktury Visual C++ w Projektancie klas](visual-cpp-structures.md)
- [Wyliczenia Visual C++ w Projektancie klas](visual-cpp-enumerations.md)
- [Definicje typów języka Visual C++ w Projektancie klas](visual-cpp-typedefs.md)
