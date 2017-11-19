---
title: IntelliSense Visual C# | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [J#]
- Visual C#, IntelliSense
- IntelliSense [C#]
ms.assetid: 79ca304d-dc1e-4dc9-a2a6-7808df2e588e
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b19e53d5c82c6c6a3abeda72a6b321dd630d586a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="visual-c-intellisense"></a>Visual C# IntelliSense
Visual C# IntelliSense jest dostępna podczas kodowania w edytorze i podczas debugowania w [trybie natychmiastowym](../ide/reference/immediate-window.md) okna poleceń.  
  
## <a name="completion-lists"></a>Listy uzupełniania  
 Listy uzupełniania IntelliSense języka Visual C# zawierają tokenów z listy elementów członkowskich, całe słowo i inne. Zapewnia szybki dostęp do:  
  
-   Elementy członkowskie typu lub przestrzeni nazw  
  
-   Nazwy funkcji, poleceń i zmienne  
  
-   Wstawki kodu  
  
-   Słowa kluczowe języka  
  
-   Metody rozszerzeń  
  
Listy uzupełniania w C# jest również inteligentne odfiltrować istotny tokenów i wybierz wstępnie tokenu na podstawie kontekstu. Aby uzyskać więcej informacji, zobacz [filtrowane listy uzupełniania](#filtered-completion-lists).  
  
### <a name="code-snippets-in-completion-lists"></a>Wstawki kodu na listach uzupełniania  
 W środowisku Visual C#, listy uzupełniania obejmuje wstawki kodu, aby łatwo Wstawianie wstępnie zdefiniowanych treści kodu do programu. Wstawki kodu są wyświetlane na liście uzupełniania jako fragment [skrót](../ide/code-snippets-schema-reference.md#shortcut).  Aby uzyskać więcej informacji na temat wstawki kodu, które domyślnie są dostępne w programie Visual C#, zobacz [Visual C# — wstawki](../ide/visual-csharp-code-snippets.md).  
  
### <a name="language-keywords-in-completion-lists"></a>Słowa kluczowe języka na listach uzupełniania  
 W środowisku Visual C#, na liście uzupełniania także słowa kluczowe języka. Aby uzyskać więcej informacji na temat słów kluczowych języka C#, zobacz [słowa kluczowe języka C#](/dotnet/csharp/language-reference/keywords/index).  
  
### <a name="extension-methods-in-completion-lists"></a>Metody rozszerzenia na listach uzupełniania  
 W środowisku Visual C#, lista uzupełniania zawiera metody rozszerzenia, które znajdują się w zakresie.  
  
> [!NOTE]
>  Listy uzupełniania nie są wyświetlane wszystkie metody rozszerzenia dla <xref:System.String> obiektów.  
  
 Metody rozszerzenia użyj ikony innego niż metody wystąpienia. Lista ikony na liście, zobacz [Widok klas i przeglądarka obiektów ― ikony](../ide/class-view-and-object-browser-icons.md). Gdy metody wystąpienia i metodę rozszerzenia o tej samej nazwie znajdują się w zakresie, na liście uzupełniania Wyświetla ikonę — metoda rozszerzenia.  
  
### <a name="filtered-completion-lists"></a>Filtrowane listy uzupełniania  
IntelliSense usuwa niepotrzebne elementy członkowskie na liście uzupełniania za pomocą filtrów. Visual C# filtruje listy uzupełniania, które są wyświetlane dla tych elementów:  
  
-   **Podstawowe klasy i interfejsy**: IntelliSense automatycznie usuwa elementy z interfejsu base klasy uzupełniania list i, w deklaracji klasy podstawowe i interfejs listy i ograniczenie list. Na przykład wyliczenia nie są wyświetlane na liście uzupełniania dla klas podstawowych, ponieważ wyliczenia nie można używać dla klas podstawowych. Uzupełnianie lista klas bazowych zawiera tylko interfejsów i przestrzenie nazw. Wybierz element na liście, wpisz przecinek IntelliSense usuwa klasy podstawowe z listy uzupełniania ponieważ Visual C# nie obsługuje wielu dziedziczenia. Takie samo zachowanie występuje także klauzule ograniczenia.  
  
-   **Atrybuty**: podczas stosowania atrybut do typu, na liście uzupełniania jest filtrowana tak, że lista zawiera tylko te typy, które elementem podrzędnym elementu przestrzenie nazw, które zawierają te typy, takich jak <xref:System.Attribute>.  
  
-   **Klauzule catch**  
  
-   **Inicjatory obiektów**: tylko elementy członkowskie, które mogą być inicjowane pojawi się na liście uzupełniania.  
  
-   **New — słowo kluczowe**: podczas wpisywania `new` , a następnie naciśnij klawisz spacji, zostanie wyświetlona lista uzupełniania. Element jest automatycznie wybierany na liście, na podstawie kontekstu w kodzie. Na przykład automatycznie zaznaczono elementów na liście uzupełniania dla deklaracji i instrukcjach return w metodach.  
  
-   **Enum — słowo kluczowe**: po naciśnięciu spację po znaku równości przydziału wyliczenia, zostanie wyświetlona lista uzupełniania. Element jest automatycznie wybierany na liście, na podstawie kontekstu w kodzie. Na przykład automatycznie zaznaczono elementów na liście uzupełniania po słowie kluczowym return i po wprowadzeniu deklaracji.  
  
-   **jako i operatory**: filtrowane zakończeniu zostanie wyświetlona lista automatycznie po naciśnięciu spację po wpisaniu `as` lub `is` — słowo kluczowe.  
  
-   **Zdarzenia**: podczas wpisywania słowa kluczowego `event`, na liście uzupełniania zawiera tylko typy delegatów.  
  
-   **Parametr pomocy** automatycznie sortuje do pierwszego przeciążenia metody zgodny z parametrami podczas ich wprowadzania. Jeśli wiele przeciążenia metody są dostępne, można górę i w dół strzałki, aby przejść do następnego możliwe przeciążenie na liście.  
  
## <a name="most-recently-used-members"></a>Ostatnio używane elementy członkowskie  
 Elementy członkowskie zaznaczone ostatnio w oknie podręcznym pamięta IntelliSense [członków listy](../ide/using-intellisense.md) pole dla obiekt automatyczne uzupełnianie nazw. Przy następnym Użyj listy członków ostatnio używanych elementów członkowskich są wyświetlane u góry. Historia ostatnio używanych elementów członkowskich jest wyczyszczone między każdej sesji w IDE.  
  
## <a name="override"></a>override  
 Podczas wpisywania [zastąpienia](/dotnet/csharp/language-reference/keywords/override) , a następnie naciśnij klawisz spacji, IntelliSense wyświetla wszystkie elementy członkowskie prawidłową klasę podstawową, które można zmienić w oknie Lista rozwijana. Wpisywanie zwracany typ metody po `override` wyświetli monit o IntelliSense w celu wyświetlenia tylko metody, które zwracają tego samego typu. Gdy IntelliSense nie można odnaleźć dopasowań, wyświetla wszystkich elementów członkowskich klasy podstawowej.  
  
## <a name="automatic-code-generation"></a>Automatyczne generowanie kodu  
  
### <a name="add-using"></a>Dodawanie using  
 **Dodawanie using** operację funkcji IntelliSense automatycznie dodaje wymaganych `using` dyrektywy w pliku kodu. Ta funkcja pozwala utrzymać fokus na kod użytkownik zapisu, a nie wymaga przejścia do innej części kodu.  
  
 Aby zainicjować przy użyciu operacji dodawania, umieść kursor na odwołanie do typu nie można rozpoznać. Na przykład podczas tworzenia aplikacji konsoli i przy dodawaniu `XmlTextReader` do treści `Main` metody czerwona falista pojawia się w tym wierszu kodu, ponieważ nie można rozpoznać odwołania do typu. Następnie można wywoływać, Dodaj przy użyciu za pośrednictwem szybkich akcji. Szybkie działanie jest widoczna tylko w przypadku, gdy kursor znajduje się na typu niezwiązanego.  
  
 ![Dodaj obraz rozwinięte akcji przy użyciu, szybkie](../ide/media/addusing-quickaction.png "AddUsing QuickAction")  

 Kliknij ikonę żarówki, a następnie wybierz pozycję **przy użyciu zestawów System.Xml;** automatyczne dodawanie za pomocą dyrektywy.  
  
### <a name="organize-usings"></a>Organizacja deklaracji Using  
 **Organizowania użyć** opcje sortowania i Usuń `using` i `extern` deklaracje bez zmiany zachowania kodu źródłowego. W czasie, może stać się pliki źródłowe, w przeglądarek i trudne do odczytu z powodu niepotrzebnych i unorganized `using` dyrektywy. **Organizowania użyć** opcje compact kod źródłowy przez usunięcie nieużywanych `using` dyrektywy i poprawia czytelność, sortując ich.  
  
 Aby wyświetlić opcje dostępne w programie Visual Studio IDE na **Edytuj** menu wskaż **IntelliSense**i wskaż polecenie **organizowania użyć**. IDE udostępnia następujące opcje do organizowania i Usuń `usings` dyrektywy:  
  
### <a name="implement-interface"></a>Implementowanie interfejsu  
 IntelliSense udostępnia opcję, aby zaimplementować [interfejsu](/dotnet/csharp/language-reference/keywords/interface) podczas pracy w edytorze kodu. Zwykle aby prawidłowo zaimplementować interfejs, należy utworzyć deklaracji metody dla każdego członka interfejsu w klasie. Za pomocą funkcji IntelliSense, po wpisaniu nazwy interfejsu w deklaracji klasy, szybkie akcje żarówka jest wyświetlany. Żarówki zapewnia opcję automatycznie, zaimplementuj interfejs przy użyciu jawnych ani niejawnych nazewnictwa. W obszarze nazw jawne deklaracje metody przenoszenia Nazwa interfejsu; w obszarze nazw niejawne deklaracje metody nie wskazują interfejsu, do którego należą. Metody interfejsu jawnie nazwanej można uzyskać tylko za pośrednictwem interfejsu wystąpienia, a nie przez wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [jawnej implementacji interfejsu](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).  
  
 Implementowanie interfejsu wygeneruje minimalną liczbę wycinków kodu metody wymaganych do spełnienia interfejsu. Jeśli klasą podstawową implementuje części interfejsu, tych klas zastępczych nie są generowane.  
  
### <a name="implement-abstract-base-class"></a>Implementowanie abstrakcyjnych klas podstawowych  
 IntelliSense udostępnia opcję ułatwiają zaimplementowanie członkami abstrakcyjna klasa podstawowa automatycznie podczas pracy w edytorze kodu. Zazwyczaj do zaimplementowania abstrakcyjne elementy członkowskie klasy podstawowej wymaga tworzenia nowej definicji metody dla każdej metody abstrakcyjnej klasy podstawowej w klasie pochodnej. Za pomocą funkcji IntelliSense, po wpisaniu nazwy abstrakcyjnej klasy podstawowej w deklaracji klasy, szybkie akcje żarówka jest wyświetlany. Żarówki udostępnia opcję, aby automatycznie wdrożyć metod klasy podstawowej.  
  
 Klas zastępczych — metoda, które są generowane przez funkcję abstrakcyjna klasa podstawowa implementacja jest formowana przez fragment kodu zdefiniowane w pliku MethodStub.snippet. Wstawki kodu są można modyfikować. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie wstawek kodu](../ide/walkthrough-creating-a-code-snippet.md).  
  
### <a name="generate-from-usage"></a>Generowanie na podstawie użycia  
 **Generowanie z użycia** pozwala używać klas i członków przed definiowania ich. Można wygenerować klasy zastępczej dla dowolnej klasy, konstruktora, metoda, właściwość, pole lub wyliczenia, który chcesz używać, ale nie zostały jeszcze zdefiniowane. Nowe typy i elementy członkowskie można generować bez opuszczania bieżącej lokalizacji w kodzie. Pozwala to zmniejszyć przerwania do przepływu pracy.  
  
 Gramatyczne jest wyświetlana pod każdym Niezdefiniowany identyfikator. Gdy wskaźnik myszy na podstawie identyfikatora, komunikat o błędzie jest wyświetlany w etykietce narzędzia. Aby wyświetlić odpowiednie opcje, użyj jednej z następujących procedur:    
  
-   Kliknij przycisk Niezdefiniowany identyfikator. Szybkie akcje żarówka jest wyświetlany w obszarze identyfikator. Kliknij żarówkę.  
  
-   Kliknij Niezdefiniowany identyfikator, a następnie naciśnij klawisz **Ctrl +.** (Ctrl + kropka).  
  
-   Kliknij prawym przyciskiem myszy Niezdefiniowany identyfikator, a następnie kliknij przycisk **szybkie akcje i Refaktoryzacje**.  
  
Wyświetlane opcje mogą być następujące:  
  
-   **Generowanie właściwości**  
  
-   **Generuj pole**  
  
-   **Generate — metoda**  
  
-   **Generowanie klas**  
  
-   **Generowanie nowego typu...**  (dla klasy, struktury, interfejsu lub wyliczenia)  
  
## <a name="generate-event-handlers"></a>Generowanie obsługi zdarzeń  
 W edytorze kodu IntelliSense może pomóc dołączenie do pól zdarzenia metod (procedury obsługi zdarzeń).  
  
 Podczas wpisywania `+=` po pole zdarzenia w pliku CS IntelliSense operator monit z opcją naciśnij klawisz TAB. Wstawia nowe wystąpienie klasy delegata, który wskazuje metodę obsługi zdarzenia.  
  
 ![Przycisk Automatyczny punktu zaczepienia się](../ide/media/vxautohookup.gif "vxAutoHookUp")  
  
 Po naciśnięciu klawisza TAB, IntelliSense automatycznie zakończeniu instrukcji i wyświetla odwołanie do programu obsługi zdarzeń jako zaznaczonego tekstu w edytorze kodu. Aby ukończyć podłączenie zdarzenia automatyczne, IntelliSense monituje o naciśnij klawisz TAB, aby ponownie utworzyć pusty klasy zastępczej dla programu obsługi zdarzeń.  
  
 ![Generowanie obsługi zdarzeń](../ide/media/vxgenerateeventhandler.gif "vxGenerateEventHandler")  
  
> [!NOTE]
>  Jeśli nowe delegowanie, który jest tworzony przez funkcję IntelliSense odwołuje się do istniejącego programu obsługi zdarzeń, IntelliSense komunikuje się tych informacji w etykietce narzędzia. Następnie można zmodyfikować tego odwołania; tekst jest już zaznaczone w edytorze kodu. W przeciwnym razie podłączenie zdarzenia automatyczne zakończeniu w tym momencie.  
  
 Po naciśnięciu klawisza TAB, IntelliSense zastępcze metodę o prawidłowej sygnaturze i umieszcza kursor w treści procedury obsługi zdarzenia.  
  
> [!NOTE]
>  Użyj **Przejdź wstecz** na **widoku** menu (CTRL +-) aby powrócić do instrukcji podłączenie zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio IDE](../ide/visual-studio-ide.md)