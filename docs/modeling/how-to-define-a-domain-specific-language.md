---
title: 'Porady: definiowanie języka właściwego dla domeny'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4aea2750e3900beb0aaa62156c215376ff16d1ea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-define-a-domain-specific-language"></a>Porady: definiowanie języka właściwego dla domeny
Aby zdefiniować języka specyficznego dla domeny (DSL), należy utworzyć rozwiązanie Visual Studio z szablonu. Część klucza rozwiązania jest diagram definicji DSL, który jest przechowywany w DslDefinition.dsl. Definicja DSL definiuje klasy i kształty DSL. Po zmodyfikowaniu i dodanie do tych elementów, można dodać kod program, aby dostosować DSL bardziej szczegółowo.

Jeśli jesteś nowym użytkownikiem DSLs, zaleca się pracę za pośrednictwem **laboratorium narzędzia DSL**, która znajduje się w tej witrynie: [Visualizaton i modelowanie zestawu SDK](http://go.microsoft.com/fwlink/?LinkID=186128)

##  <a name="templates"></a> Wybieranie rozwiązania szablonu
 Aby zdefiniować DSL, należy zainstalować następujące składniki:

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio wizualizacji i modelowania zestawu SDK||


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


 Aby utworzyć nowego języka specyficznego dla domeny, trzeba utworzyć nowe rozwiązanie Visual Studio za pomocą szablonu projektu języka specyficznego dla domeny.

#### <a name="to-create-a-dsl-solution"></a>Tworzenie rozwiązań DSL

1.  Tworzenie rozwiązania z **języka specyficznego dla domeny** szablonu, który znajduje się w obszarze **inne typy/rozszerzalność projektu** w **nowy projekt** okno dialogowe.

     ![Okno dialogowe DSL tworzenie](../modeling/media/create_dsldialog.png "Create_DSLDialog")

     Po kliknięciu **OK**, **kreatora języka specyficznego dla domeny** otwiera i wyświetla listę rozwiązań DSL szablonu.

2.  Kliknij, aby wyświetlić opis każdego szablonu. Wybierz rozwiązanie najlepiej odpowiadający ma zostać utworzony.

     Każdy szablon DSL definiuje podstawowych pracy DSL. Trzeba edytować ten DSL do własnych wymagań.

     Kliknij każdy przykład, aby uzyskać więcej informacji.

    -   Wybierz **przepływ zadań** utworzyć DSL, który ma ścieżek. Ścieżek są pionowych lub poziomych partycji diagramu.

    -   Wybierz **modeli składnika** można utworzyć DSL, która ma porty. Porty są małe kształty na krawędzi większy kształt.

    -   Wybierz **diagramy klas** do definiowania DSL, zawierający przedział kształtów. Kształty przedział zawierają listy elementów.

    -   Wybierz **minimalnego języka** w innych przypadkach, lub jeśli wiadomo.

    -   Wybierz **minimalnego projektanta formularza systemu Windows** lub **minimalnego projektanta WPF** utworzyć DSL, wyświetlany na powierzchni formularzy systemu Windows lub programu WPF. Należy napisać kod, aby zdefiniować edytora. Więcej informacji znajduje się w następujących tematach:

         [Tworzenie języka specyficznego dla domeny opartego na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

         [Tworzenie języka specyficznego dla domeny opartego na podsystemie WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

3.  Wprowadź rozszerzenia nazwy pliku z DSL w odpowiedniej strony w kreatorze. To rozszerzenie, które pliki zawierające wystąpień programu DSL będzie używany.

    -   Wybierz rozszerzenie nazwy pliku, który nie jest skojarzony z dowolnej aplikacji w komputerze lub w dowolnym komputerze, na którym chcesz zainstalować DSL. Na przykład **docx** i **htm** będzie można zaakceptować pliku rozszerzeń nazw.

    -   Kreator wyświetli ostrzeżenie, jeśli rozszerzenia plików, które zostały wprowadzone, jest on używany jako DSL. Należy rozważyć użycie różnych rozszerzenie. Można również zresetować Wyczyszczenie starych projektantów eksperymentalne wystąpienie programu Visual Studio SDK eksperymentalne. Kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, **zestawu SDK programu Microsoft Visual Studio 2010**, **narzędzia**, a następnie **zresetować firmy Microsoft Visual Studio 2010 eksperymentalne wystąpienie**.

4.  Można dostosować ustawienia w innych stron lub pozostaw wartości domyślne.

5.  Kliknij przycisk **Zakończ**.

     Kreator tworzy rozwiązanie, które zawiera dwie lub trzy projekty i generuje kod z definicji DSL.

 Interfejs użytkownika jest teraz podobny poniższej ilustracji.

 ![Projektant DSL](../modeling/media/dsl_designer.png "dsl_designer")

 To rozwiązanie definiuje domeny określonego języka. Aby uzyskać więcej informacji, zobacz [Przegląd interfejsu użytkownika narzędzia języka specyficznego dla domeny](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Testowanie rozwiązania
 Rozwiązanie szablonu zapewnia pracy DSL, które można zmodyfikować lub użyć, ponieważ jest on.

 Aby przetestować rozwiązania, naciśnij klawisz F5 lub CTRL + F5. Otwiera nowe wystąpienie programu Visual Studio w trybie eksperymentalne.

 W nowym wystąpieniu programu Visual Studio w Eksploratorze rozwiązań Otwórz przykładowy plik. Spowoduje to otwarcie jako diagram, z przybornika.

 Jeśli uruchomienia rozwiązania, które zostały utworzone z **minimalnego języka** szablonu, eksperymentalne Visual Studio będzie podobne do następujących:

 ![](../modeling/media/dsl_min.png "DSL_min")

 Poeksperymentuj z narzędzia. Tworzenie elementów, a następnie łącząc je.

 Zamknij eksperymentalne wystąpienie programu Visual Studio.

> [!NOTE]
>  Nie można wyświetlić kształty na przykład przetestować plik, modyfikacji DSL. Jednak można utworzyć nowych elementów.

### <a name="modifying-the-template-dsl"></a>Modyfikacja szablonu DSL
 Zmień nazwę i zachować niektóre lub wszystkie klasy i klasy kształtów w szablonie definicji DSL. Twoje nowe nazwy klasy powinny być prawidłowe nazwy CLR, bez spacji i znaków interpunkcyjnych.

 Jest to szczególnie przydatne zachować te klasy:

-   Klasy głównym, znajduje się w lewym górnym diagramu DSL definicji w obszarze **klasy i relacje**. Zmień jego nazwę na inny niż DSL. Na przykład DSL, o nazwie **MusicLibrary** może mieć klasy głównym o nazwie **utworów muzycznych**.

-   Diagram klas, znajduje się w prawej dolnej części diagramu DSL definicji w **elementów diagramu** kolumny. Może być konieczne przewiń w prawo, aby go wyświetlić. Zazwyczaj nosi * YourDsl ***Diagram**.

-   Jeśli używasz **przepływ zadań** szablonu i chcesz tworzenie diagramów z ścieżek, przechowywać i Zmień nazwę klasy domeny aktora i ActorSwimlane kształtu.

 Usuń lub zmień innych klas ze swoimi potrzebami.

##  <a name="patterns"></a> Wzorce definiowania DSL
 Zaleca się tworzenie DSL przez dodanie lub dostosowanie funkcji jeden lub dwa jednocześnie. Dodawanie funkcji, uruchamiania DSL i przetestować go, a następnie dodaj jeden lub dwa więcej funkcji. Typowa funkcja Twoje DSL może wyglądać następująco:

-   Klasa domeny, relacja osadzania łączący element modelu kształtu wymagane do wyświetlania elementów klas na diagram i narzędzia elementu, który pozwala użytkownikom na tworzenie elementów.

-   Właściwości domeny klasą domeny i dekoratory, zawierające je na kształcie.

-   Relacja odwołania i łącznik, który wyświetla go w diagram i narzędzie łącznik, który pozwala użytkownikom tworzyć łącza.

-   Możliwość dostosowania wymagającego kodu programu, takich jak polecenia menu lub ograniczenia sprawdzania poprawności.

 W poniższych sekcjach opisano sposób tworzenia rodzaje najbardziej przydatne funkcje DSL. Istnieje wiele innych wzorcach, z którymi można skonstruować DSL, ale najczęściej są one używane.

> [!NOTE]
>  Po dodaniu funkcji, nie zapomnij kliknij **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań przed tworzenia i uruchamiania programu DSL.

 Na poniższej ilustracji przedstawiono klasy i relacje część DSL, który jest używany jako przykład w tym temacie.

 ![Dokumentacja i osadzanie relacje](../modeling/media/music_classes.png "Music_Classes")

 Następny rysunek jest przykładowy model ten DSL:

 ![Wystąpienie modelu DSL wygenerowanego](../modeling/media/music_instance.png "Music_Instance")

> [!NOTE]
>  "Modelu" odwołuje się do wystąpienia programu DSL użytkownikom tworzenie i zwykle wyświetlane jako diagram. W tym temacie omówiono diagramu definicji DSL i diagramy modelu, które są wyświetlane, gdy jest używany z DSL.

##  <a name="classes"></a> Definiowanie klas domeny
 Klasy domeny reprezentują koncepcji sieci DSL. Wystąpienia są *elementy modelu*. Na przykład w **MusicLibrary** DSL może mieć klasy domeny o nazwie **albumu** i **utworu**.

 Aby utworzyć klasę domeny, możesz przeciągnąć z **klasy o nazwie domeny** narzędzia do diagramu, a następnie zmienić nazwę klasy.

 Aby uzyskać więcej informacji, zobacz [właściwości klasy domeny](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Utwórz relację osadzania dla każdej klasy domeny
 Każda klasa domeny, z wyjątkiem klasy głównym musi być elementem docelowym co najmniej jedna relacja osadzania lub musi dziedziczyć z klasy, która jest elementem docelowym relacji osadzania.

 W modelu co element modelu jest węzłem w jednym drzewie osadzenia relacji. Źródłowe i docelowe relacja osadzania są często nazywane nadrzędnych i podrzędnych.

 Zaznaczenie elementu nadrzędnego dla klasy domeny zależy od tego, jak ma okresy istnienia jej elementy do zależą od innych elementów. Jeśli węzeł drzewa zostanie usunięty, jego poddrzewa zwykle jest również usunięte. Klasa elementu, która ma niezależny istnienia są osadzone w związku z tym bezpośrednio pod klasy głównym.

 Zwykle po wyświetleniu elementu w innym elemencie chcesz wskazać relacji właściciela. W takim przypadku najbardziej odpowiednia klasa nadrzędna jest klasa kontenera. Wyjątek stanowi po elemencie Zobacz wewnątrz kontenera rzeczywista właśnie łącze odwołania do elementu niezależne. W takim przypadku usunięcie kontenera usuwa odwołania, ale nie elementem docelowym.

 W strukturach definicji DSL opisanych w tym temacie firma Microsoft przyjmie założenie, że elementy wyświetlane w elemencie kontenera zostanie usunięta po usunięciu kontenera. Bardziej złożone schematy są możliwe i można osiągnąć, definiując reguły.

|Sposób wyświetlania elementu|Klasy nadrzędnej (osadzanie)|Przykład DSL szablon rozwiązania|
|------------------------------|--------------------------------|--------------------------------------|
|Kształt na diagramie.<br /><br /> Swimlane.|Klasy głównym DSL.|Minimalny języka.<br /><br /> Przepływ zadań: Klasa aktora.|
|Kształt w tor.|Klasa domeny elementów, które są wyświetlane jako ścieżek.|Przepływ zadań: Klasa zadań.|
|Element na liście kształtu, gdy element zostanie usunięty po usunięciu kontenera.<br /><br /> Port na krawędzi kształtu.|Klasa domeny, która jest mapowany na kształt kontenera.|Diagram klas: atrybut klasy.<br /><br /> Diagram składnika: Port klasy.|
|Element na liście, nie zostanie usunięta po usunięciu kontenera.|Klasy głównym DSL.<br /><br /> Na liście zostaną wyświetlone linki odwołań.||
|Nie bezpośrednio wyświetlane.|Klasa, która stanowi część.||

 W przykładzie biblioteki utworów muzycznych albumów są wyświetlane jako prostokąty, w których są wyświetlane tytuły utworów. W związku z tym nadrzędnego albumu jest klasy głównym muzyki, a element nadrzędny utworu jest albumu.

 Aby utworzyć klasę domeny i osadzanie w tym samym czasie, kliknij przycisk **relacja osadzania** narzędzia, a następnie kliknij przycisk klasy nadrzędnej, a następnie kliknij na pustą część diagramu.

 Nie jest zwykle należy skorygować nazwę relacja osadzania i jego role, ponieważ nazwy klas zostanie automatycznie śledzą.

 Aby uzyskać więcej informacji, zobacz [właściwości relacji domeny](../modeling/properties-of-domain-relationships.md) i [właściwości role domeny](../modeling/properties-of-domain-roles.md).

> [!NOTE]
>  Osadzanie nie jest taka sama jak dziedziczenia. Elementy podrzędne w relacja osadzania dziedziczy funkcji z obiektów nadrzędnych.

### <a name="add-domain-properties-to-each-domain-class"></a>Dodaj właściwości domeny do każdej klasy domeny
 Właściwości domeny przechowywanie wartości. Przykłady: nazwa, nazwa, Data publikacji.

 Kliknij przycisk **właściwości domeny** w klasie, naciśnij klawisz ENTER, a następnie wpisz nazwę właściwości. Domyślny typ właściwości domeny jest ciągiem. Jeśli chcesz zmienić typ, wybierz właściwość domeny i ustawić **typu** w **właściwości** okna. Jeśli żądanego typu nie jest na liście rozwijanej, zobacz [Dodawanie typy właściwości](#addTypes).

 **Ustaw właściwość nazwy elementu.** Wybierz właściwość domeny, który może służyć do identyfikowania elementy w Eksploratorze języka. Na przykład w klasie utworu domeny, że można wybrać właściwość domeny tytułu. W **właściwości** ustaw **jest nazwa elementu** do `true`.

### <a name="create-derived-domain-classes"></a>Tworzenie klasy pochodnej domeny
 Klasa domeny ma wariantów, które dziedziczą jego właściwości i relacje, utworzyć klasy, które dziedziczą z niego. Na przykład albumu może mieć klas pochodnych WMA i MP3.

 Tworzenie przy użyciu klasy pochodnej **klasy domeny** narzędzia.

 Kliknij przycisk **dziedziczenia** narzędzia, kliknij przycisk klasy pochodnej, a następnie kliknij klasy podstawowej.

 Rozważ ustawienie **modyfikator dziedziczenia** klasy podstawowej, aby **abstrakcyjny**. Jeśli uważasz, że może być konieczne wystąpień klasy podstawowej, należy wziąć pod uwagę zamiast tworzenia oddzielnego pochodnych klasy dla nich.

 Klasy pochodne dziedziczą właściwości i ról z ich klasami podstawowymi.

### <a name="tidy-the-dsl-definition-diagram"></a>Porządek Diagram definicji DSL
 Po dodaniu relacje niektórych klas pojawi się w więcej niż jednym miejscu. Aby zmniejszyć liczbę wystąpień i szersze diagramu, kliknij prawym przyciskiem myszy klasy docelowej relacji, a następnie kliknij **Przełącz drzewa tutaj**. Dla odwrotny efekt, kliknij prawym przyciskiem myszy klasy docelowej relacji i kliknij przycisk **podziału drzewa**. Jeśli nie ma tych poleceń menu, upewnij się, że wybrano tylko klasy domeny.

 Użyj klawiszy CTRL + Strzałka w górę i CTRL + Strzałka w dół, aby przenieść klasy domeny i klasy kształtu.

### <a name="test-the-domain-classes"></a>Testowanie klasy domeny

##### <a name="to-test-the-new-domain-classes"></a>Aby przetestować nowe klasy domeny

1.  **Kliknij przycisk Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań do generowania kodu DSL projektanta. Ten krok można zautomatyzować. Aby uzyskać więcej informacji, zobacz [jak zautomatyzować Przekształć wszystkie szablony](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

2.  **Tworzenie i uruchamianie DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie programu Visual Studio w trybie eksperymentalne. W eksperymentalnym wystąpieniu programu Visual Studio otwarcia lub utworzenia pliku, który ma rozszerzenie nazwy pliku z DSL.

3.  **Otwórz Eksploratora.** Na stronie diagramu jest okno Eksploratora język, jest zazwyczaj o nazwie *YourLanguage* Explorer. Jeśli nie ma tego okna, może być na karcie poniżej Eksploratora rozwiązań. Jeśli nie możesz znaleźć, na **widoku** menu wskaż **inne okna**, a następnie kliknij przycisk *YourLanguage* **Explorer**.

     Twoje explorer przedstawia widok drzewa modelu.

4.  **Utwórz nowe elementy.** Kliknij prawym przyciskiem myszy węzeł główny na początku, a następnie kliknij przycisk **Dodaj nowy *** YourClass*.

     Nowe wystąpienie klasy zostanie wyświetlona w języku Explorer.

5.  Sprawdź, czy każde wystąpienie ma inną nazwę, podczas tworzenia nowych wystąpień. Będzie to miało miejsce tylko, jeśli ustawiono **jest nazwa elementu** flagi we właściwości domeny.

6.  **Sprawdź właściwości domeny. Przy użyciu wystąpienia klasy zaznaczone** Sprawdź okno właściwości. Powinny mieć właściwości domeny, które zdefiniowano w tej klasie domeny.

7.  **Zapisz plik, zamknij go i otwórz go ponownie**. Wszystkie wystąpienia utworzone powinny być widoczne w Eksploratorze po rozwiń węzły.

##  <a name="shapes"></a> Definiowanie kształtów na diagramie
 Możesz zdefiniować klasy elementów, które są wyświetlane na diagramie ikon prostokąty lub wielokropków.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Aby zdefiniować klasę elementów, które są wyświetlane jako kształtów na diagramie

1.  **Definiowanie i testowania klasą domeny, zgodnie z opisem w**[Definiowanie klas domeny](#classes) **.** 

    -   Element nadrzędny klasy powinny być klasy głównym. Oznacza to powinna być osadzania relacji między klasy głównym i Nowa klasa domeny.

    -   Jeśli diagramu ścieżek, element nadrzędny może być klasy domeny, który jest zamapowany na tor. Przed kontynuowaniem tej procedury, zobacz [Definiowanie DSL, który ma ścieżek](#swimlanes).

2.  **Dodaj klasę kształtu** do reprezentowania elementów diagramu modelu. Przeciąganie z jednego z następujących narzędzi na diagramie DSL definicji:

    -   **Kształt geometrii** zapewnia prostokąta lub elipsy.

    -   **Obraz kształtu** Wyświetla obraz, który podasz.

    -   **Przedziału kształtu** jest prostokąt, która zawiera jedną lub więcej list elementów.

     Zmień nazwę klasy kształtu, który pojawi się po prawej stronie diagramu definicji DSL, w obszarze łączników i kształtów.

3.  **Zdefiniuj obraz, jeśli utworzono kształtu obrazu**.

    1.  Utwórz plik obrazu o dowolnym rozmiarze. Formaty BMP, JPEG, GIF i EMF są obsługiwane.

    2.  W Eksploratorze rozwiązań Dodaj go do rozwiązania, w obszarze Dsl\Resources.

    3.  Wróć do diagramu definicji DSL i wybierz nową klasę kształtu obrazu.

    4.  Kliknij w oknie właściwości **obrazu** właściwości.

    5.  W **wybierz obraz** okna dialogowego kliknij menu rozwijane w obszarze **nazwę pliku**i wybierz obraz.

4.  **Dodawanie elementów decorator tekstu kształtu, aby wyświetlić właściwości domeny.**

     Aby wyświetlić nazwę lub tytuł elementu modelu, niezbędny będzie co najmniej jeden dekoratora tekstu.

     Kliknij prawym przyciskiem myszy nagłówka klasy kształtu, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **Dekoratora tekstu**. Ustaw nazwę dekoratora, a w zestawie okna właściwości jego **pozycji**.

5.  **Uzyskuj każdego kształtu Mapa elementów diagramu klasy domeny, który powinien być wyświetlany**.

     Kliknij przycisk **mapy Element diagramu** narzędzia, a następnie kliknij klasy domeny, a następnie klasy kształtu.

6.  **Mapowania właściwości elementów decorator tekstu.**

    1.  Wybierz szara linia między klasą domeny i Klasa kształtu, która reprezentuje mapę element diagramu.

    2.  W **szczegóły DSL** okna, kliknij przycisk **mapy Dekoratora** kartę. Jeśli nie widzisz **szczegóły DSL** okna na **widoku** menu wskaż **inne okna** , a następnie kliknij przycisk **szczegóły DSL**. Często należy podnieść na początku tego okna, aby wyświetlić całą jego zawartość.

    3.  Wybierz nazwę dekoratora. W obszarze **Właściwość wyświetlania**, wybierz nazwę właściwości klasy domeny. Powtórz ten krok dla każdego dekoratora.

         Jeśli chcesz wyświetlić właściwości elementu powiązane, kliknij przycisk Nawigatora drzewa listy rozwijanej w obszarze **ścieżkę, aby wyświetlić właściwości**.

    4.  Upewnij się, że wyświetlany znacznik wyboru obok każdej dekoratora nazwy.

     ![Okno mapowania kształt i szczegóły DSL](../modeling/media/dsldetailswindow.png "DslDetailsWindow")

7.  **Wprowadź element przybornika służący do tworzenia elementów klasy domeny.**

    1.  W **DSL Explorer**, rozwiń węzeł **edytor** węzła i jego węzły podrzędne.

    2.  Kliknij prawym przyciskiem myszy węzeł w węźle **kart z przybornika** mający taką samą nazwę jak Twoje DSL, na przykład MusicLibrary. Kliknij przycisk **Dodaj narzędzie do elementu**.

        > [!NOTE]
        >  Kliknięcie prawym przyciskiem myszy **narzędzia** węzła, nie będzie mógł przeglądać **narzędzia Dodaj Element**. Zamiast tego kliknij węzeł powyżej.

    3.  W oknie właściwości za pomocą narzędzia elementu wybrane ustawić **klasy** do klasy domeny, który został ostatnio dodany.

    4.  Ustaw **podpis** i **Tooltip**.

    5.  Ustaw **ikonę przybornika** ikonę, która będzie wyświetlana w przyborniku. Możesz ustawić nową ikonę lub ikony już używana dla innego narzędzia.

         Aby utworzyć nową ikonę, otwórz Dsl\Resources w **Eksploratora rozwiązań**. Skopiuj i Wklej jeden z istniejących plików BMP narzędzia elementu. Zmień nazwę kopii wklejonych, a następnie kliknij dwukrotnie, aby go edytować.

         Powrócić do diagramu DSL definicji, wybierz narzędzie, a w oknie dialogowym właściwości kliknij **[...]**  w **ikonę przybornika**. W **wybierz mapy bitowej** okno dialogowe, wybierz użytkownika. Plik BMP z menu rozwijanego.

 Aby uzyskać więcej informacji, zobacz [właściwości geometrii kształtów](../modeling/properties-of-geometry-shapes.md) i [właściwości obrazu kształtów](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>Aby przetestować kształtów

1.  **Kliknij przycisk Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań do generowania kodu DSL projektanta.

2.  **Tworzenie i uruchamianie DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie programu Visual Studio w trybie eksperymentalne. W eksperymentalnym wystąpieniu programu Visual Studio otwarcia lub utworzenia pliku, który ma rozszerzenie nazwy pliku z DSL.

3.  **Sprawdź, czy element narzędzia są wyświetlane w przyborniku.**

4.  **Tworzenie kształtów** przeciągając je z narzędziem na diagramu modelu.

5.  **Sprawdź, czy jest wyświetlany każdego dekoratora tekstu,** oraz że:

    1.  Można edytować, jeśli nie ustawiono **jest interfejs użytkownika tylko do odczytu** flagi na wartość właściwości.

    2.  Podczas edytowania właściwości w oknie właściwości lub w dekorator innych widok jest aktualizowany.

 Po przetestowaniu najpierw kształtu, można dopasować niektóre jego właściwości i dodać niektórych bardziej zaawansowanych funkcji. Aby uzyskać więcej informacji, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

##  <a name="references"></a> Definiowanie relacji odwołania
 Można zdefiniować relacji między dowolnej klasy domeny źródłowej i wszystkie klasy domeny docelowej. Relacje odwołania są zwykle wyświetlane na diagramie łączników, które są linie między kształtami.

 Na przykład albumów muzycznych i artystów są wyświetlane jako kształtów na diagramie, można zdefiniować relacji o nazwie ArtistsAppearedOnAlbums zawierającego łącze do albumów, na których pracowali artystów. Zobacz przykład pokazany na rysunku.

 ![Wystąpienie modelu DSL wygenerowanego](../modeling/media/music_instance.png "Music_Instance")

 Relacje odwołania także połączyć elementy tego samego typu. Na przykład w DSL, reprezentujący drzewa rodziny, relacja między elementów nadrzędnych i ich elementy podrzędne jest relacji z osób.

### <a name="define-a-reference-relationship"></a>Definiowanie relacji
 Kliknij narzędzie relacja odwołania, a następnie kliknij klasy domeny źródła relacji, a następnie kliknij klasy domeny docelowej. Klasa docelowa może być taka sama jak klasa źródłowa.

 Każda relacja ma dwie role reprezentowanego przez linię na każdej stronie pola relacji. Można wybrać poszczególnych ról i ustawienia swoich właściwości w oknie właściwości.

 **Rozważ zmianę nazwy ról**. Na przykład w relacji między osoby i osoby, możesz zmienić domyślne nazwy elementów nadrzędnych i podrzędnych, Menedżer i podwładnych, nauczyciel i uczniów i tak dalej.

 **Dostosuj liczebnościami powodującymi każdej roli**, jeśli jest to konieczne. Jeśli chcesz, aby każda osoba, aby mieć co najwyżej jednego menedżera, ustaw liczebność, która pojawia się poniżej Menedżer etykiety na diagramie, aby od 0 do 1.

 **Dodaj właściwości domeny do relacji.** Na rysunku relacji Wykonawca Album ma właściwość roli.

 **Ustaw właściwość umożliwia zduplikowanych relacji,** Jeśli między tej samej pary elementy modelu może istnieć więcej niż jedno łącze do tej samej klasy. Na przykład mogą umożliwić nauczyciel więcej niż jeden może ulec sam uczniów nauczysz się.

 ![Kształt mapy dla łączników](../modeling/media/music_connector.png "Music_Connector")

 Aby uzyskać więcej informacji, zobacz [właściwości relacji domeny](../modeling/properties-of-domain-relationships.md) i [właściwości role domeny](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Zdefiniuj łącznika, aby wyświetlić relacji
 Łącznik wyświetla wiersz między dwoma kształtów na diagramie modelu.

 Przeciągnij **łącznik** narzędzia na diagramie definicji DSL.

 Dodaj elementy decorator tekstu, jeśli mają być wyświetlane etykiety w łączniku. Ustaw ich pozycji. Aby umożliwić użytkownikowi, Przenieś dekoratora tekstu, ustaw jej **jest ruchoma** właściwości.

 Użyj **mapy Element diagramu** narzędzia, aby połączyć relacji odwołanie łącznika.

 Wybrana mapa element diagramu Otwórz **szczegóły DSL** okna, a następnie otwórz **mapy Dekoratora** kartę.

 Wybierz poszczególne **Dekoratora** i ustaw **Właściwość wyświetlania** z właściwością domeny.

 Upewnij się, że znacznik wyboru obok każdego elementu w **Dekoratory** listy.

### <a name="define-a-connection-builder-tool"></a>Zdefiniuj narzędzia konstruktora połączenia
 W **DSL Explorer** okna, rozwiń węzeł **edytor** węzła i jego węzły podrzędne.

 Kliknij prawym przyciskiem myszy węzeł, który ma taką samą nazwę jak Twoje DSL, a następnie kliknij przycisk **Dodaj nowe narzędzie połączenia**.

 Gdy nowe narzędzie jest zaznaczony, w oknie właściwości:

-   Ustaw **podpis** i **Tooltip**.

-   Kliknij przycisk **Konstruktor połączeń** i wybierz odpowiedniego konstruktora dla nowych relacji.

-   Ustaw **ikonę przybornika** ikonę, która ma być wyświetlany w przyborniku. Możesz ustawić nową ikonę lub ikony już używana dla innego narzędzia.

     Aby utworzyć nową ikonę, otwórz Dsl\Resources w **Eksploratora rozwiązań**. Skopiuj i Wklej jeden z istniejących plików BMP narzędzia elementu. Zmień nazwę kopii wklejonych, a następnie kliknij dwukrotnie, aby go edytować.

     Powrócić do diagramu DSL definicji, wybierz narzędzie, a w oknie dialogowym właściwości kliknij **[...]**  w **ikonę przybornika**. W **wybierz mapy bitowej** okno dialogowe, wybierz użytkownika. Plik BMP z menu rozwijanego.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Relacja odwołania i łącznika

1.  **Kliknij przycisk Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań do generowania kodu DSL projektanta.

2.  **Tworzenie i uruchamianie DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie programu Visual Studio w trybie eksperymentalne. W eksperymentalnym wystąpieniu programu Visual Studio otwarcia lub utworzenia pliku, który ma rozszerzenie nazwy pliku z DSL.

3.  **Sprawdź, czy narzędzie połączenia jest wyświetlany w przyborniku.**

4.  **Tworzenie kształtów** przeciągając je z narzędziem na diagramu modelu.

5.  **Utwórz połączenia** między kształtami. Kliknij narzędzie łącznik, kliknij kształt, a następnie kliknij przycisk innego kształtu.

6.  **Upewnij się, że nie można utworzyć połączenia między klasami nieodpowiednie.** Na przykład w przypadku sieci relacji między albumów i artystów, sprawdź, że nie można połączyć artystów artystów.

7.  **Sprawdź, czy liczebnościami powodującymi są poprawne. Na przykład sprawdzić, czy nie można nawiązać połączenia osoby więcej niż jednego menedżera.**

8.  **Sprawdź, czy jest wyświetlany każdego dekoratora tekstu,** oraz że:

    1.  Można edytować, jeśli nie ustawiono **jest interfejs użytkownika tylko do odczytu** flagi na wartość właściwości.

    2.  Podczas edytowania właściwości w oknie właściwości lub w dekorator innych widok jest aktualizowany.

 Po przetestowaniu najpierw łącznika, można dopasować niektóre jego właściwości i dodać niektórych bardziej zaawansowanych funkcji. Aby uzyskać więcej informacji, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

##  <a name="compartments"></a> Definiowanie kształtów, które zawierają listy: przedziału kształtów
 Kształt Przedział zawiera jedną lub więcej list elementów. Na przykład w DSL biblioteki utworów muzycznych, można użyć kształtów przedziału do reprezentowania utworów muzycznych albumów. W przypadku każdego albumu znajduje się lista utworów.

 ![Przedziału kształtu](../modeling/media/compartmentshape.png "CompartmentShape")

 Najprostsza metoda realizacji w tym celu w definicji DSL służy do definiowania jedną klasę domeny dla kontenera i jedną klasę domeny dla każdej listy. Klasa jest mapowana na kształt Przedział.

 ![Mapa kształtu](../modeling/media/music_mapcomp.png "Music_MapComp")

 Aby uzyskać więcej informacji, zobacz [właściwości przedziału kształtów](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>Aby zdefiniować kształtu Przedział

1.  **Tworzenie kontenera klasy domeny**. Kliknij przycisk **relacja osadzania** narzędzia, kliknij przycisk klasy głównym modelu, a następnie kliknij pustą część diagramu definicji DSL. Spowoduje to utworzenie klasy domeny o nazwie albumu na przykład rysunku.

     Możesz też zamiast osadzania ich klasy głównym, można osadzić kontenera w klasie domeny, który jest zamapowany na tor.

     Dodaj właściwość domeny, takie jak nazwa klasy i ustawić jej **jest nazwa elementu** flagi w oknie właściwości.

2.  **Tworzenie klasy domeny elementu listy**. Kliknij przycisk **relacja osadzania** narzędzia, kliknij odpowiednią klasę kontenera (albumu), a następnie kliknij przycisk pustą część diagramu. Spowoduje to utworzenie klasy domeny o nazwie utworu na przykład rysunku.

     Dodaj właściwość domeny, takie jak tytuł do klasy i ustaw jej **jest nazwa elementu** flagi.

     Dodawanie innych właściwości domeny.

     Dodaj kolejną klasę domeny elementu listy dla każdej listy, który chcesz wyświetlić.

3.  **Aby utworzyć kilka rodzajów element na liście**, tworzenia klas, które dziedziczą z klasy list. Nadać list — klasa abstrakcyjna przez ustawienie jej **modyfikator dziedziczenia**.

     Na przykład chcesz muzyki ma zostać posortowana według composer zamiast wykonawcy można utworzyć dwa podklasy utworu, ClassicalSong i NonClassicalSong.

4.  **Utwórz kształt Przedział**. Przeciągnij z **kształtu Przedział** narzędzia na diagramie definicji DSL.

     Dodaj dekoratora tekstu i ustaw jego nazwy.

     Dodaj przedziału i ustaw jego nazwy.

5.  Umożliwiają użytkownikowi ukryć przedziałów listy, kliknij prawym przyciskiem myszy klasę kształtu przedział, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **Dekoratora Rozwiń/Zwiń**. W oknie właściwości ustaw pozycję dekorator.

6.  Kliknij przycisk **mapy Element diagramu** narzędzia, kliknij przycisk kontenera klasy domeny, a następnie kliknij kształt Przedział.

7.  Wybierz łącze diagram element mapy między klasą domeny i kształtu. W **szczegóły DSL** okno:

    1.  Kliknij przycisk **Dekoratory** kartę. Kliknij nazwę dekorator, a następnie wybierz odpowiedni element w obszarze **wyświetlania właściwości**. Upewnij się, że znajdujące się obok nazwy dekorator pojawia się znacznik wyboru.

    2.  Kliknij przycisk **mapy przedział** kartę.

         Kliknij nazwę przedziału.

         W obszarze **ścieżka kolekcji elementy wyświetlane**, przejdź do listy element klasy (utworu). Kliknij strzałkę listy rozwijanej, aby użyć narzędzia nawigatora.

         W obszarze **wyświetlania właściwości**, wybierz właściwość, która powinna być wyświetlana na liście. W tym przykładzie jest to tytuł.

> [!NOTE]
>  Przy użyciu pól ścieżek w mapie Dekoratora i przedziału Mapuj pola, można tworzyć bardziej złożone relacje między klasy domeny i kształtu Przedział.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Aby zdefiniować narzędzie do tworzenia kształtu

1.  **Wprowadź element przybornika służący do tworzenia elementów klasy domeny.**

2.  W **DSL Explorer**, rozwiń węzeł **edytor** węzła i jego węzły podrzędne.

3.  Kliknij prawym przyciskiem myszy węzeł w węźle **kart z przybornika** mający taką samą nazwę jak Twoje DSL, na przykład MusicLibrary. Kliknij przycisk **Dodaj narzędzie do elementu**.

    > [!NOTE]
    >  Kliknięcie prawym przyciskiem myszy **narzędzia** węzła, nie będzie mógł przeglądać **narzędzia Dodaj Element**. Zamiast tego kliknij węzeł powyżej.

4.  W oknie właściwości za pomocą narzędzia elementu wybrane ustawić **klasy** do klasy domeny, który został ostatnio dodany.

5.  Ustaw **podpis** i **Tooltip**.

6.  Ustaw **ikonę przybornika** ikonę, która będzie wyświetlana w przyborniku. Możesz ustawić nową ikonę lub ikony już używana dla innego narzędzia.

     Aby utworzyć nową ikonę, otwórz Dsl\Resources w **Eksploratora rozwiązań**. Skopiuj i Wklej jeden z istniejących narzędzia elementu. Pliki BMP. Zmień nazwę kopii wklejonych, a następnie kliknij dwukrotnie, aby go edytować.

     Powrócić do diagramu DSL definicji, wybierz narzędzie, a w oknie dialogowym właściwości kliknij **[...]**  w **ikonę przybornika**. W **wybierz mapy bitowej** oknie dialogowym Wybierz plik BMP z menu rozwijanego.

#### <a name="to-test-a-compartment-shape"></a>Aby przetestować kształtu Przedział

1.  **Kliknij przycisk Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań do generowania kodu DSL projektanta.

2.  **Tworzenie i uruchamianie DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie programu Visual Studio w trybie eksperymentalne. W eksperymentalnym wystąpieniu programu Visual Studio otwarcia lub utworzenia pliku, który ma rozszerzenie nazwy pliku z DSL.

3.  **Sprawdź, czy narzędzie znajduje się w przyborniku.**

4.  Przeciągnij narzędzie na diagramu modelu. Kształt jest tworzony.

     Sprawdź, czy nazwa elementu jest wyświetlany i automatycznie ma ustawioną wartość domyślną.

5.  Kliknij prawym przyciskiem myszy nagłówek nowy kształt, a następnie kliknij przycisk Dodaj *Your elementu listy.* W tym przykładzie polecenie jest dodać utworu.

     Sprawdź, czy element jest widoczny na liście i czy jej nazwa została zmieniona.

6.  Kliknij jeden z elementów listy, a następnie sprawdź okno właściwości. Powinny pojawić się właściwości elementów listy.

7.  Otwórz Eksploratora języka. Upewnij się, widzą węzły kontenerów z węzłami elementu listy wewnątrz.

 ![Eksploratorze generowane DSL](../modeling/media/music_explorer.png "Music_Explorer")

 Po przetestowaniu najpierw kształtu przedział, można dopasować niektóre jego właściwości i dodać niektórych bardziej zaawansowanych funkcji. Aby uzyskać więcej informacji, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Wyświetlanie w przedziale łącza
 Zazwyczaj element, który można wyświetlić w przedziale jest elementem podrzędnym elementu reprezentowanego przez kształt Przedział. Jednak czasami chcesz wyświetlić element, który jest z nim połączony z relacji.

 Na przykład możemy dodać drugi przedziału, do AlbumShape, który wyświetla listę artystów, które są połączone z Album.

 W takim przypadku powinien być wyświetlany przedział łącza, zamiast elementu, do którego istnieje odwołanie. Wynika to z faktu, gdy użytkownik wybiera element w przedziale i naciska klawisz DELETE, ma łącze do usunięcia, element do którego istnieje odwołanie.

 Niemniej jednak może mieć nazwy elementu, do którego istnieje odwołanie pojawiają się w przedziale.

 W poniższej procedurze przyjęto, że utworzono już klasy domeny, relacja odwołania kształtu Przedział i mapy elementów diagramu, jak opisano wcześniej w tej sekcji.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Aby wyświetlić łącza w przedziale

1.  **Dodaj przedziału do kształtu Przedział**. Na diagramie definicji DSL, kliknij prawym przyciskiem myszy klasę kształtu przedział, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **przedział**.

2.  Ustaw **ścieżka kolekcji elementy wyświetlane** można przejść do łącza, a nie jej elementu docelowego. Kliknij menu rozwijane i użyj widoku drzewa, aby wybrać zamiast elementem docelowym relacji odwołania. W tym przykładzie jest relacja **ArtistAppearedOnAlbums**.

3.  Ustaw **ścieżki do wyświetlania właściwości** można przejść z linku do elementu docelowego. W tym przykładzie jest to **wykonawcy**.

4.  Ustaw **wyświetlania właściwości** do odpowiedniej właściwości elementu docelowego, na przykład **nazwa**.

5.  **Przekształć wszystkie szablony**, tworzenia i uruchamiania DSL i otworzyć modelu testu.

6.  Diagramu modelu utworzyć odpowiednie klasy kształtu, ustaw ich nazwy i Utwórz łącze między nimi. W kształcie Przedział nazw połączonych elementów powinny być wyświetlane.

7.  Wybierz łącze lub element w kształcie Przedział. Zarówno łącza, a element powinien zniknąć.

##  <a name="ports"></a> Definiowanie porty na granicy innego kształtu
 Port jest kształtu, który znajduje się na granicy innego kształtu.

 Porty mogą również służyć do zapewnienia punktu połączenia środka innego kształtu, do którego użytkownik może wykonywać rysowanie łączników. W takim przypadku należy przezroczystego kształtu portu.

 Aby zapoznać się przykładem, który używa portów, wybierz **Diagram składnika** szablonu podczas tworzenia nowego rozwiązania DSL. Ten przykład przedstawia główne punkty, które można wziąć pod uwagę podczas definiowania porty:

-   Brak klasy domeny, która reprezentuje kontener portów, `Component`.

-   Brak klasy domeny, który reprezentuje portów. W tym przykładzie jest to `ComponentPort`.

-   Brak osadzania relacji z klasy domeny kontenera do portu klasy domeny. Aby uzyskać więcej informacji, zobacz [Definiowanie klas domeny](#classes).

-   Różnego rodzaju port można łączyć w tym samym kontenerze, można utworzyć podklasami klasy domeny portu. W tym przykładzie `InPort` i `OutPort` dziedziczyć `ComponentPort`.

-   Klasa domeny mogą być mapowane do dowolnego rodzaju kształtu. W tym przykładzie jest `ComponentShape`. Aby uzyskać więcej informacji, zobacz [Definiowanie kształtów](#shapes).

-   Klasy domeny portu są mapowane do portu kształtów. Można mapować klas pochodnych do rozdzielania klas kształtu portu lub mapowania klasy podstawowej na jeden port kształtu klasy.

 Pod innymi względami kształtów portu działać zgodnie z opisem w [Definiowanie kształtów](#shapes).

 Aby uzyskać więcej informacji, zobacz [kształtów właściwości portu](../modeling/properties-of-port-shapes.md).

##  <a name="swimlanes"></a> Definiowanie DSL, który ma ścieżek
 Ścieżek są poziomej lub pionowej partycji diagramu. Każdy tor odnosi się do elementu modelu. Definicja DSL wymaga jednej klasy domeny dla elementów tor.

 Najlepszym sposobem tworzenia DSL ze ścieżek jest do tworzenia nowego rozwiązania DSL i wybierz szablon rozwiązania przepływ zadań. W definicji DSL klasy aktora jest mapowany na tor klasy domeny. Zmień nazwę tego i innych klas do projektu.

 Aby dodać klasy, który będzie wyświetlany jako kształt wewnątrz tor, Utwórz osadzanie relację między klasą tor i nowej klasy. Użytkownicy będą mogli przeciągnij elementy z jednego tor, ale każdy element będzie zawsze równa w szczególności tor. W szablonie rozwiązania przepływ zadań FlowElement jest elementem podrzędnym klasy tor.

 Aby dodać klasy, który będzie wyświetlany jako kształt niezależnie od ścieżek, utworzyć osadzanie relację klasy głównym nowej klasy. Użytkownicy będą mogli umieścić te kształtów na diagramie, łącznie z przekraczaniem granic ścieżek i poza ścieżek w dowolnym miejscu. W szablonie rozwiązania przepływ zadań komentarz jest elementem podrzędnym klasy głównym.

 Aby uzyskać więcej informacji, zobacz [właściwości ścieżek](../modeling/properties-of-swimlanes.md).

##  <a name="addTypes"></a> Dodawanie typów właściwości

### <a name="domain-enumerations-and-literals"></a>Literały i wyliczenia domeny
 Wyliczenia domena jest typem z kilku wartości literału.

 Aby dodać wyliczenia domena, kliknij prawym przyciskiem myszy katalogu głównego modelu w **DSL Explorer** , a następnie kliknij przycisk **Dodaj nowe wyliczenia domena**. Element pojawi się w **DSL Explorer** w obszarze **typów domeny** węzła. Ten element nie jest wyświetlana na diagramie.

 Aby dodać wyliczenia literałów do wyliczenia domena, kliknij prawym przyciskiem myszy wyliczenia domena w **DSL Explorer** , a następnie kliknij przycisk **Dodaj nowe wyliczenie literału**.

 Domyślnie można ustawić właściwości, która ma typ wyliczeniowy do tylko jednej wartości wyliczenia naraz. Użytkownicy i programiści, aby można było ustawić dowolną kombinację wartości - "pola bitowego —" Ustaw **IsFlags** właściwości wyliczenia.

### <a name="external-types"></a>Typów zewnętrznych
 W przypadku ustawienia typu właściwości domeny, jeśli nie zostanie znaleziony typ ma **typu** listy rozwijanej można dodać typu zewnętrznego. Na przykład można dodać **System.Drawing.Color** typu do listy.

 Aby dodać typ, kliknij prawym przyciskiem myszy katalogu głównego modelu w Eksploratorze DSL, a następnie kliknij przycisk **dodać nowy typ zewnętrznej**. W oknie właściwości ustaw nazwę **kolor** oraz przestrzeń nazw **System.Drawing**. Ten typ jest teraz wyświetlany w Eksploratorze DSL w obszarze **typów domeny**. Można go, gdy ustawiony typ właściwości domeny.

##  <a name="custom"></a> Dostosowywanie DSL
 Za pomocą metod opisanych w tym temacie, można szybko utworzyć DSL podającą notacji, czytelnej postaci XML i podstawowe narzędzia, które są wymagane do generowania kodu i pozostałych artefaktów.

 Istnieją dwie metody rozszerzania definicji DSL:

1.  Dostosowywanie DSL za pomocą funkcji więcej definicji DSL. Na przykład możesz wprowadzić narzędzia pojedynczy łącznik, który można utworzyć kilka rodzajów łącznika i można kontrolować reguł, które usuwając jeden element spowoduje również usunięcie powiązanych elementów. Te techniki najczęściej są osiągane przez ustawienie wartości w definicji DSL, a niektóre wymagają zaledwie kilku wierszach kodu programu.

     Aby uzyskać więcej informacji, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

2.  Rozszerzanie narzędzia do modelowania przy użyciu kodu programu, aby uzyskać więcej informacji o zaawansowanych efekty. Na przykład można utworzyć polecenia menu, które można zmienić modelu na model i narzędzia integrujące DSLs dwóch lub więcej. VMSDK jest zaprojektowany specjalnie w celu ułatwiają integrowanie rozszerzeń z kodem, które są generowane na podstawie definicji DSL.  Aby uzyskać więcej informacji, zobacz [pisanie kodu, aby dostosować języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Zmiana definicji DSL
 Po utworzeniu dowolny element w definicji DSL wiele wartości domyślne są ustawiane automatycznie. Po ustawieniu, trzeba je zmienić. Upraszcza to rozwoju DSL, umożliwiając zaawansowane dostosowania.

 Na przykład podczas mapowania kształtu do elementu, ścieżka elementu nadrzędnego mapowania jest automatycznie ustawiony odpowiednio do atrybutów relacja osadzania klasy domeny. Jednak jeśli użytkownik zmieni relacja osadzania ścieżka elementu nadrzędnego pozostają niezmienione automatycznie.

 Dlatego należy pamiętać, że jeśli zmienisz niektóre relacje w definicji DSL, nie jest rzadko błędy podczas zapisywania definicji lub gdy Przekształć wszystkie szablony do. Większość tych błędów jest łatwe rozwiązać problem. Kliknij dwukrotnie pozycję raportu o błędach, aby zobaczyć lokalizację błędu.

 Zobacz też [porady: Zmienianie Namespace języka specyficznego dla domeny](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

##  <a name="trouble"></a> Rozwiązywanie problemów
 W poniższej tabeli wymieniono niektóre z najczęściej występujących problemów występujących podczas projektowania DSL, oraz sugestie dotyczące ich rozwiązania. Więcej porad jest dostępna w [Extensibililty Forum narzędzi wizualizacji](http://go.microsoft.com/fwlink/?LinkId=186074).

|Problem|Sugestia|
|-------------|----------------|
|Zmiany wprowadzone w pliku definicji DSL nie obowiązują.|Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi nad Eksploratorze rozwiązań, a następnie Odbuduj rozwiązania.|
|Kształty widoczna nazwa dekoratora zamiast wartości właściwości.|Konfigurowanie dekoratora mapowania. Na diagramie definicji DSL kliknij mapę element diagramu jest szara linia między klasą domeny i Klasa kształtu.<br /><br /> Otwórz **szczegóły DSL** okna. Jeśli nie widzisz, w menu Widok, wskaż polecenie **inne okna**, a następnie kliknij przycisk **szczegóły DSL**.<br /><br /> Kliknij przycisk **mapy Dekoratora** kartę. Wybierz nazwę dekorator. Upewnij się, że zaznaczono pole wyboru obok tej pozycji. W obszarze **Właściwość wyświetlania**, wybierz nazwę właściwości domeny.<br /><br /> Aby uzyskać więcej informacji, zobacz [kształtów na diagramie](#shapes).|
|W Eksploratorze DSL nie można dodać do kolekcji. Na przykład po I prawym przyciskiem myszy narzędzia nie jest żadne "Dodaj narzędzie" polecenie w menu.<br /><br /> W Eksploratorze dla moich DSL nie można dodać elementu do listy.|Kliknij prawym przyciskiem myszy element powyżej węzła, który próbujesz. Jeśli chcesz dodać do listy polecenia Dodaj jest nie znajduje się w węźle listy, ale w jego właściciela.|
|Po utworzeniu klasy domeny, ale nie można utworzyć wystąpienia w Eksploratorze języka.|Każda klasa domeny, z wyjątkiem głównego musi być elementem docelowym relacji osadzania.|
|W Eksploratorze dla moich DSL elementy są wyświetlane tylko w przypadku ich nazwy typu.|W definicji DSL, wybierz właściwość domeny klasy i w oknie właściwości ustaw **jest nazwa elementu** na wartość true.|
|Moje DSL zawsze zostanie otwarty w edytorze XML.|Może to nastąpić z powodu błędu podczas odczytu pliku. Jednak nawet po rozwiązaniu tego błędu, należy jawnie zresetować można z projektantem DSL w edytorze.<br /><br /> Kliknij prawym przyciskiem myszy element projektu, kliknij przycisk **Otwórz za pomocą** i wybierz * YourLanguage ***Designer (ustawienie domyślne)**.|
|Przybornika Moje DSL nie jest wyświetlany po zmianie nazwy zestawu.|Przejrzyj i zaktualizuj **DslPackage\GeneratedCode\Package.tt** uzyskać więcej informacji, zobacz [porady: zmiana Namespace języka specyficznego dla domeny](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).|
|Nie ma przybornika Moje DSL, ale nie uległy zmianie nazwy zestawu.<br /><br /> Lub pojawi się komunikat raportowania nie można załadować rozszerzenia.|Zresetuj eksperymentalne wystąpienie i skompiluj ponownie rozwiązanie.<br /><br /> 1.  W oknie menu Start, w obszarze **wszystkie programy**, rozwiń węzeł [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)], następnie **narzędzia**, a następnie kliknij przycisk **Zresetuj Microsoft Visual Studio eksperymentalne wystąpienie programu**.<br />2.  W programie Visual Studio**kompilacji** menu, kliknij przycisk **Kompiluj ponownie rozwiązanie**.|

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do języków specyficznych dla domeny](../modeling/getting-started-with-domain-specific-languages.md)
- [Tworzenie języka specyficznego dla domeny opartego na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)
- [Tworzenie języka specyficznego dla domeny opartego na podsystemie WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)