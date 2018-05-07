---
title: Tworzenie i konfigurowanie typów członków (Projektant klas)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce62e2d2723c38d933c9efc4c8d910ac418dcb4f
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="creating-and-configuring-type-members-class-designer"></a>Tworzenie i konfigurowanie typów członków (Projektant klas)
Możesz dodać tych członków do typów w klasie diagram i skonfigurować te elementy członkowskie **szczegółów klasy** okno:

|**Typ**|**Elementy członkowskie, które może zawierać**|
|--------------|--------------------------------|
|Class|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|
|Wyliczenie|członek|
|Interface|metoda, właściwość, zdarzenie (w języku C# i Visual Basic)|
|Klasa abstrakcyjna|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|
|Struktura (konstrukcja Struct w języku C#)|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), stała|
|Delegate|parametr|
|Moduł (tylko w języku VB)|metoda, właściwość, pole, zdarzenie, konstruktor, stała|

> [!NOTE]
> Utwórz bardziej zwartą deklarację właściwości, gdy akcesory właściwości get i set nie potrzebują dodatkowej logiki, za pomocą automatycznie wdrożonych właściwości (tylko C#). Aby wyświetlić pełną podpisu z **diagramu klas** menu wybierz **Zmień Format członków** > **podpisu pełny ekran**. Aby uzyskać więcej informacji na temat właściwości zaimplementowane automatycznie, zobacz [Auto-Implemented właściwości](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Obsługuje zawartości|
|----------|------------------------|
|**Wprowadzenie:** Aby utworzyć i skonfigurować elementy członkowskie typu, należy otworzyć **szczegółów klasy** okna.|-   [Otwórz okno Szczegóły klasy](creating-and-configuring-type-members.md#open-the-class-details-window)<br />-   [Uwagi dotyczące użycia szczegóły klasy](creating-and-configuring-type-members.md#class-details-usage-notes)<br />-   [Wyświetl informacje tylko do odczytu](creating-and-configuring-type-members.md#display-of-read-only-information)<br />-   [Skróty klawiatury i myszy w oknie Diagram klas i szczegóły klasy](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Tworzenie i modyfikowanie elementów członkowskich typu:** tworzenia nowych elementów członkowskich, zmodyfikować elementów członkowskich i dodać parametry do metody przy użyciu **szczegółów klasy** okna.|-   [Tworzenie elementów członkowskich](creating-and-configuring-type-members.md#create-members)<br />-   [Zmodyfikuj elementy członkowskie typu](creating-and-configuring-type-members.md#modify-type-members)<br />-   [Dodawanie parametrów do metod](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Otwórz okno Szczegóły klasy
Domyślnie **szczegółów klasy** zostanie wyświetlone okno automatycznie po otwarciu nowego diagramu klas (zobacz [porady: Dodawanie diagramów klasy do projektów](how-to-add-class-diagrams-to-projects.md)). Można również otworzyć **szczegółów klasy** okna jawnie, w następujący sposób.

#### <a name="to-open-the-class-details-window"></a>Aby otworzyć okno Szczegóły klasy

1.  Kliknij prawym przyciskiem myszy na dowolnej klasy na diagramie, aby wyświetlić menu kontekstowe.

2.  W menu kontekstowym kliknij **szczegółów klasy**.

 - lub -

-   Wskaż **inne okna** w menu Widok, a następnie kliknij przycisk **szczegółów klasy**.

## <a name="create-members"></a>Tworzenie elementów członkowskich
Można utworzyć element członkowski, używając dowolnego z następujących narzędzi:

-   **Projektant klas**

-   **Klasa szczegóły** okna narzędzi

-   **Klasa szczegóły** okna

> [!NOTE]
> Można również utworzyć konstruktory i destruktory przy użyciu procedur opisanych w tej sekcji. Należy pamiętać, że konstruktory i destruktory są specjalnymi rodzajami metod i jako takie pojawią się one w **metody** przedział w kształty diagram klas, a w **metody** sekcji  **Klasa szczegóły** okna siatki.

> [!NOTE]
> Jedyna jednostka, jaką można dodać do obiektu delegowanego, to parametr. Należy pamiętać, że procedura uprawniony "Aby utworzyć członka za pomocą **szczegółów klasy** pasek narzędzi okna" jest nieprawidłowa dla tej akcji.

#### <a name="to-create-a-member-using-class-designer"></a>Aby utworzyć składową za pomocą Projektanta klas

1.  Kliknij prawym przyciskiem myszy typ, do której chcesz dodać członka, wskaż pozycję **Dodaj**, a następnie wybierz typ elementu członkowskiego, które chcesz dodać.

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Uzyskuje nazwę domyślną, które można zmienić w **Projektant klas**, **szczegółów klasy** oknie lub w **właściwości** okna.

2.  Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

#### <a name="to-create-a-member-using-the-class-details-window-toolbar"></a>Aby utworzyć członka za pomocą narzędzi okno Szczegóły klasy

1.  Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.

     Typ uzyskuje fokus i jego zawartość jest wyświetlana w **szczegółów klasy** okna.

2.  W **szczegółów klasy** pasek narzędzi okna, kliknij ikonę górnej i wybierz **nowy \<elementu członkowskiego >** z listy rozwijanej.

     Przesuwa kursor do **nazwa** pól w wierszu dla rodzaju elementu członkowskiego, które chcesz dodać. Na przykład, jeśli kliknięto **nową właściwość**, kursor zostanie umieszczony w nowym wierszu w **właściwości** sekcji **szczegółów klasy** okna.

3.  Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, i naciśnij klawisz Enter (lub przenieś fokus w inny sposób, np. za pomocą klawisza Tab).

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Element członkowski teraz istnieje w kodzie i jest wyświetlany w **Projektant klas**, **szczegółów klasy** okna i w oknie właściwości.

4.  Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

#### <a name="to-create-a-member-using-the-class-details-window"></a>Aby utworzyć członka za pomocą okno Szczegóły klasy

1.  Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.

     Typ uzyskuje fokus i jego zawartość jest wyświetlana w **szczegółów klasy** okna.

2.  W **szczegółów klasy** okna w sekcji, którą zawiera typ elementu członkowskiego, które chcesz dodać, kliknij przycisk  **\<dodać członka >**. Na przykład, jeśli chcesz dodać pole, kliknij przycisk  **\<Dodaj pole >**.

3.  Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, a następnie naciśnij klawisz Enter.

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Element członkowski teraz istnieje w kodzie i jest wyświetlany w **Projektant klas**, **szczegółów klasy** okna i w oknie właściwości.

4.  Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

     **Uwaga:** umożliwia także skróty klawiaturowe do tworzenia elementów członkowskich. Aby uzyskać więcej informacji, zobacz [skróty klawiaturowe i myszy w oknie Diagram klas i szczegóły klasy](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Zmodyfikuj elementy członkowskie typu
Projektant klas umożliwia modyfikowanie składowych typów, które są wyświetlane na diagramie. Można modyfikować składowe dowolnego typu wyświetlane na diagramie klasy, które nie są tylko do odczytu. Zmodyfikuj elementy członkowskie typu za pomocą edycji w miejscu na powierzchni projektu okna właściwości oraz **szczegółów klasy** okna.

Wszystkie elementy członkowskie wyświetlane **szczegółów klasy** okna reprezentują członkami typów na diagramie klas. Istnieją cztery rodzaje elementów członkowskich: metody, właściwości, pola i zdarzenia.

Wszystkie wiersze elementów członkowskich pojawiają się pod nagłówkami, które grupują elementy członkowskie według rodzaju. Na przykład wszystkie właściwości są wyświetlane pod nagłówkiem **właściwości**, które jako węzeł w siatce, zwijania i rozwijania.

Każdy wiersz elementu członkowskiego zawiera następujące elementy:

-   **Ikona elementu członkowskiego**

     Każdy rodzaj elementu członkowskiego jest reprezentowany przez własną ikonę. Wskaż myszą ikony elementu członkowskiego do wyświetlania podpisu elementu członkowskiego. Kliknij ikonę elementu członkowskiego lub przestrzeń z lewej strony ikony elementu członkowskiego, aby zaznaczyć wiersz.

-   **Nazwa elementu członkowskiego**

     **Nazwa** kolumny w wierszu elementu członkowskiego Wyświetla nazwę elementu członkowskiego. Ta nazwa jest wyświetlany również w **nazwa** właściwości w oknie właściwości. Ta komórka służy do zmiany nazwy któregokolwiek elementu członkowskiego, który ma uprawnienia odczytu i zapisu.

     Jeśli **nazwa** jest zbyt ograniczone, aby wyświetlić całą nazwę wskazanie myszą na nazwę elementu członkowskiego Wyświetla całą nazwę kolumny.

-   **Typ elementu członkowskiego**

     **MemberType** komórki używa funkcji IntelliSense, pozwalającej wybierz z listy wszystkich typów w bieżącym projekcie lub przywoływane projekty.

-   **Modyfikator elementu członkowskiego**

     Zmień widoczność modyfikator elementu członkowskiego albo `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`), lub `Default`.

-   **\<Dodaj element członkowski >**

     Ostatni wiersz w **szczegółów klasy** okna zawiera tekst  **\<dodać członka >** w **nazwa** komórki. Po kliknięciu tej komórki, można utworzyć nowy element członkowski. Aby uzyskać więcej informacji, zobacz [tworzenia elementów członkowskich](creating-and-configuring-type-members.md#create-members).

-   **Właściwości elementów członkowskich w oknie właściwości**

     **Szczegółów klasy** okno wyświetla podzbiór właściwości elementów członkowskich, które są wyświetlane w oknie właściwości. Zmiana właściwości w jednej lokalizacji zaktualizuje globalnie wartość właściwości. Obejmuje to wyświetlanie jej wartości w innej lokalizacji.

-   **Podsumowanie**

     **Podsumowania** komórki przedstawia podsumowanie informacji na temat elementu członkowskiego. Kliknij przycisk wielokropka w **Podsumowanie** komórki, aby wyświetlić lub edytować informacje o **Podsumowanie**, **typu zwracanego**, i **uwagi** dla elementu członkowskiego .

-   **Ukryj**

     Gdy **Ukryj** pole wyboru jest zaznaczone, element członkowski nie jest wyświetlany w typie.

#### <a name="to-modify-a-type-member"></a>Aby zmodyfikować element członkowski typu

1.  Za pomocą Projektanta klas, wybierz typ.

2.  Jeśli **szczegółów klasy** okno nie jest wyświetlana, kliknij przycisk **szczegółów klasy** okna na pasku narzędzi projektanta klas.

3.  Edytowanie wartości w polach **szczegółów klasy** okna siatki. Po każdej modyfikacji naciśnij klawisz ENTER lub w inny sposób przenieś fokus kursora z edytowanego pola, na przykład, naciskając klawisz TAB. Zmiany odzwierciedlają się bezpośrednio w kodzie.

    > [!NOTE]
    >  Jeśli chcesz zmodyfikować jedynie nazwę elementu członkowskiego, możesz to zrobić za pomocą edycji w miejscu.

## <a name="add-parameters-to-methods"></a>Dodawanie parametrów do metod
Dodawanie parametrów do metod za pomocą **szczegółów klasy** okna. Parametry mogą być skonfigurowane jako wymagane lub opcjonalne. Wartość dla **opcjonalne domyślne** parametru instruuje projektanta, aby wygenerować kod jako parametr opcjonalny.

Wiersze parametrów zawierają następujące elementy:

-   **Nazwa**

     **Nazwa** kolumny w wierszu parametru wyświetla nazwę parametru. Ta nazwa jest wyświetlany również w **nazwa** właściwości w oknie właściwości. Ta komórka służy do zmiany nazwy któregokolwiek parametru, który ma uprawnienia odczytu i zapisu.

     Wskazując nazwę parametru wyświetla nazwę parametru, jeśli **nazwa** kolumna jest zbyt ograniczone, aby wyświetlić całą nazwę.

-   **Typ**

     **Typ parametru** komórki używa funkcji IntelliSense, które pozwala wybrać z listy wszystkich typów w bieżącym projekcie lub przywoływane projekty.

-   **Modyfikator**

     **Modyfikator** komórki w wierszu parametr akceptuje i wyświetla nowy modyfikator parametru. Aby wprowadzić nowy modyfikator parametrów, użyj pola listy rozwijanej można wybierać **Brak**, **ref**, **limit**, lub **params** w języku C# i **ByVal**, **ByRef**, lub **ParamArray** w języku Visual Basic

-   **Podsumowanie**

     **Podsumowanie** komórki w wierszu parametr umożliwia wprowadzanie komentarze w kodzie, które są widoczne w IntelliSense podczas wprowadzania parametru w edytorze kodu.

-   **\<Dodaj parametr >**

     Ostatni wiersz parametru elementu członkowskiego zawiera tekst **<add parameter>** w **nazwa** komórki. Kliknięcie tej komórki pozwala utworzyć nowy parametr. Aby uzyskać więcej informacji, zobacz [Aby dodać parametr do metody](creating-and-configuring-type-members.md#add-parameters-to-methods).

**Właściwości parametru w oknie właściwości**

Okno właściwości zawiera te same właściwości parametru wyświetlane w **szczegółów klasy** okna: **nazwa**, **typu**, **modyfikator** , **Podsumowanie**, jak również **opcjonalne domyślne** właściwości. Zmiana właściwości w jednej lokalizacji aktualizuje globalnie wartość właściwości, włącznie z wyświetlaniem jej wartości w innej lokalizacji.

> [!NOTE]
> Aby dodać parametr do delegata, zobacz [tworzenia elementów członkowskich](creating-and-configuring-type-members.md#create-members).


> [!NOTE]
> Chociaż destruktor jest metodą, to nie może mieć parametrów.


### <a name="to-add-a-parameter-to-a-method"></a>Aby dodać parametr do metody

1.  Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać parametr.

     Typ uzyskuje fokus i jego zawartość będzie wyświetlany na **szczegółów klasy** okna.

2.  W **szczegółów klasy** okna, rozwinąć wiersz, do której chcesz dodać parametr metody.

     Zostanie wyświetlone wiersza wcięta parametru zawierające tylko parę nawiasów i słowa  **\<Dodaj parametr >.**

3.  Kliknij przycisk  **\<Dodaj parametr >**, wpisz nazwę nowego parametru, a następnie naciśnij klawisz **Enter**.

     Nowy parametr jest dodawany do metody i kod metody. Wyświetla w **szczegółów klasy** okna i właściwości.

4.  Opcjonalnie określ inne szczegóły dotyczące parametru, takie jak jego typ.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Aby dodać opcjonalny parametr do metody

1.  Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać opcjonalny parametr.

     Typ uzyskuje fokus i jego zawartość będzie wyświetlany na **szczegółów klasy** okna.

2.  W **szczegółów klasy** okna, rozwinąć wiersz metody, do której chcesz dodać parametr opcjonalny.

     Zostanie wyświetlone wiersza wcięta parametru zawierające tylko parę nawiasów i słowa  **\<Dodaj parametr >.**

3.  Kliknij przycisk  **\<Dodaj parametr >**, wpisz nazwę nowego parametru, a następnie naciśnij klawisz **Enter**.

     Nowy parametr jest dodawany do metody i kod metody. Wyświetla w **szczegółów klasy** okna i właściwości.

4.  W oknie właściwości, wpisz wartość **opcjonalne domyślne** właściwości. Ustawienie właściwości Opcjonalny domyślny parametru powoduje, że ten parametr staje się opcjonalny.

    > [!NOTE]
    >  Opcjonalne parametry muszą być ostatnimi parametrami na liście parametrów.

## <a name="class-details-usage-notes"></a>Uwagi dotyczące użycia szczegóły klasy
Należy pamiętać, następujące porady dotyczące używania **szczegółów klasy** okna.

**Można edytować i nie można edytować komórki**

Wszystkie komórki w **szczegółów klasy** okna są edytowalne kilka wyjątków:

-   Typ całej jest tylko do odczytu, gdy, na przykład znajdują się w zestawie. Po wybraniu kształtu w Projektancie klas **szczegółów klasy** okna powoduje wyświetlenie jej szczegółów w stanie tylko do odczytu.

-   Dla indeksatorów nazwa jest tylko do odczytu, a pozostałe (typ, modyfikator, podsumowanie) są edytowalne.

-   Wszystkie typy ogólne w znajduje się tylko do odczytu parametrów **szczegółów klasy** okna. Aby zmienić parametr rodzajowy, wyedytuj jego kod źródłowy.

-   Nazwa parametru typu, który jest zdefiniowany w typie rodzajowym, jest tylko do odczytu.

-   Gdy kod typu jest dzielony (Błędny) **szczegółów klasy** okno wyświetla zawartość typu jako tylko do odczytu.

**Szczegóły klasy okna i kod źródłowy**

-   Kod źródłowy można wyświetlić, klikając prawym przyciskiem myszy kształtu **szczegółów klasy** okna (lub Projektant klas), a następnie klikając pozycję Wyświetl kod. Plik źródłowy kodu otwiera się i przewija do wybranego elementu.

-   Zmiana kodu źródłowego jest natychmiast odzwierciedlone w wyświetlania informacji podpisu w Projektancie klas i **szczegółów klasy** okna. Jeśli **szczegółów klasy** zamknięciu okna w czasie, nowe informacje są widoczne, przy następnym otwarciu.

-   Gdy kod typu jest dzielony (Błędny) **szczegółów klasy** okno wyświetla zawartość typu jako tylko do odczytu.

**Funkcje Schowka w okno Szczegóły klasy**

 Można skopiować lub wyciąć pól lub wiersze z **szczegółów klasy** okna i wklej je do innego typu. Wiersz można wyciąć tylko wtedy, gdy nie jest tylko do odczytu. Po wklejeniu wiersza, **szczegółów klasy** okna przypisuje nową nazwę (pochodzące z nazwą skopiowanego wiersza), aby uniknąć konfliktu.

## <a name="display-of-read-only-information"></a>Wyświetl informacje tylko do odczytu
Projektant klas i **szczegółów klasy** można wyświetlić w oknie dla następujących typów (i elementów członkowskich typów):

-   projekt, który zawiera diagram klas

-   projekt stanowiący odwołanie z projektu, który zawiera diagram klas

-   zestaw stanowiący odwołanie z projektu, który zawiera diagram klas

W dwóch ostatnich przypadkach, jednostka, do której istnieje odwołanie (typ lub składowa), jest tylko do odczytu na diagramie klasy, który ją reprezentuje.

Cały projekt lub jego części, takie jak pojedyncze pliki, mogą być tylko do odczytu. Najbardziej typowe przypadki, w których projekt lub jeden z jego plików jest tylko do odczytu, występują wtedy, gdy projekt jest pod kontrolą kodu źródłowego (i nie jest wyewidencjonowany), istnieje w zestawie zewnętrznym, lub gdy system operacyjny uzna, że pliki są tylko do odczytu.

**Kontroli kodu źródłowego**

Ponieważ diagram klas jest zapisywany jako plik w projekcie, musisz wyewidencjonować projektu, aby zapisać wszystkie zmiany wprowadzone w Projektancie klas lub **szczegółów klasy** okna.

**Projekty tylko do odczytu**

Projekt może być tylko do odczytu z przyczyn innych niż kontrola kodu źródłowego. Zamykanie projektu wyświetla okno dialogowe z pytaniem, czy zastąpić plik projektu, odrzucić zmiany (nie zapisuj) lub anulować operację zamknięcia. Jeśli wybierzesz zastąpienie, pliki projektu są zastępowane i udostępnione do odczytu i zapisu. Dodawany jest nowy plik diagramu klasy.

**Typy tylko do odczytu**

Jeśli użytkownik próbuje zapisać projekt zawierający typ, którego kod źródłowy plik jest tylko do odczytu, **Zapisz z uprawnieniami tylko do odczytu pliku** zostanie wyświetlone okno dialogowe, które zapewnia opcje, aby zapisać plik pod nową nazwą lub nowej lokalizacji lub zastąpić plik przeznaczony tylko do odczytu do . Jeśli plik zostanie zastąpiony, nowa kopia nie będzie już tylko do odczytu.

Jeśli plik kodu zawiera błąd składni, kształty wyświetlające kod w tym pliku zostaną tymczasowo ustawione tylko do odczytu, dopóki błąd składni nie zostanie poprawiony. Kształty w tym stanie wyświetlają czerwony tekst i czerwoną ikonę, która wyświetla etykietkę z napisem „plik kodu źródłowego zawiera błąd analizy składni”.

Odwołanie typu (np. typ .NET Framework), które występuje w obszarze innego węzła projektu lub węzła odwołania do zestawu, jest wskazany na powierzchni projektowej Projektanta klas jako tylko do odczytu. Typ lokalny, który istnieje w otwartym projekcie, jest do odczytu i zapisu, a jego kształt na powierzchni projektowej Projektanta klas jest odpowiednio opisany.

Indeksatory są odczytu i zapisu w kodzie i **szczegółów klasy** okna, ale nazwa indeksatora jest tylko do odczytu.

Metody częściowe nie można edytować za pomocą projektanta klas lub **szczegółów klasy** okna; musisz użyć edytora kodu do ich edycji.

Natywny kod w języku C++ nie można edytować za pomocą projektanta klas lub **szczegółów klasy** okna; musisz użyć edytora kodu do edycji kodu natywnego języka C++.

## <a name="see-also"></a>Zobacz także

- [Wyświetlanie typów i relacji](viewing-types-and-relationships.md)
- [Refaktoryzacja klas i typów](refactoring-classes-and-types.md)