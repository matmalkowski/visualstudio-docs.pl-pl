---
title: Zależności mapy w ramach rozwiązań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8ce84bfc59782a27e517ae1813f3ee43d6cb3718
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="map-dependencies-across-your-solutions"></a>Zależności mapy w ramach rozwiązań

Jeśli chcesz poznać zależności w kodzie wizualizacji je przez utworzenie mapy kodu. Dzięki temu można zobaczyć, jak kod dopasowuje razem przed odczytaniem za pośrednictwem plików i wierszy kodu.

![Służy do wyświetlania zależności w ramach rozwiązań](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")

**Poniżej przedstawiono niektóre pliki wideo**:

- [Poznanie zależności w kodzie za pomocą wizualizacji](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understand-your-code-dependencies-through-visualization)

- [Wizualizacja skutków wprowadzenia zmian](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Visualize-the-impact-of-a-change)

- [Poznawanie złożonego kodu przy użyciu map kodu](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understanding-complex-code-with-Code-Map-ENU)

## <a name="GetStarted"></a> Wprowadzenie do mapy kodu

**Aby użyć mapy kodu, albo**:

-   Visual Studio Enterprise: Tworzenie map kodu w edytorze kodu, w Eksploratorze rozwiązań, widoku klasy lub przeglądarki obiektów.  

-   Program Visual Studio Professional: Otwórz mapy kodu, dokonaj edycji ograniczona, a następnie przejdź kodu.  

> [!WARNING]
>  Przed udostępnieniem mapy utworzone w programie Visual Studio Enterprise z innymi użytkownikami, którzy Użyj Visual Studio Professional, upewnij się, że wszystkie elementy na mapie (takie jak ukryte elementy, rozwinięte grupy i linki międzygrupowe) są widoczne.  

 **Możesz mapować zależności dla kodu w tych językach**:  

-   Visual C# lub Visual Basic w rozwiązaniu lub zestawów (.dll lub .exe)  

-   Natywnego lub zarządzanego kodu C lub C++ w projektach Visual C++, pliki nagłówków (.h lub `#include`), lub plików binarnych  

-   X ++, projekty i zestawy wprowadzone z modułów .NET dla programu Microsoft Dynamics AX  

 **Uwaga:** dla innych projektów C# lub Visual Basic, są mniej opcji uruchamiania mapę kodu lub dodawanie elementów do istniejącej mapy kodu. Nie można na przykład, kliknij prawym przyciskiem myszy obiekt w edytorze tekstu projektu C++ i dodaj go do mapy kodu. Jednak możesz przeciągać i porzucić elementy poszczególnych kodu lub pliki w Eksploratorze rozwiązań, Widok klas i przeglądarka obiektów.  

#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>Aby wyświetlić ogólne zależności między rozwiązania  

1.  Otwórz **architektura** menu.  

2.  Wybierz, czy po prostu otworzyć rozwiązanie i jeszcze nie zostały skompilowane, czy kod została zmieniona od czasu ostatniego utworzono go **Generuj mapę kodu dla rozwiązania**.  

3.  Jeśli kod nie zmieniła się od czasu ostatniego utworzono go, wybierz **Generuj mapę kodu dla rozwiązania bez tworzenia** uzyskać większą wydajność, podczas tworzenia mapy.  

4.  [Zobacz ogólną zależności](#SeeOverviewSource) zrozumieć sposób korzystania map kodu do wyświetlenia ogólnej zależności między rozwiązania.  

#### <a name="to-see-specific-dependencies-within-your-solution"></a>Aby wyświetlić określone zależności w ramach rozwiązania  

1.  Załadowano rozwiązania, otwórz **Eksploratora rozwiązań**.  

2.  Wybierz wszystkie projekty, odwołania do zestawów, folderów, plików, typów lub elementów członkowskich, które ma być mapowany.  

3.  Na **Eksploratora rozwiązań** narzędzi wybierz **pokazywanie w mapie kodu**![Utwórz nowy wykres z wybrane węzły przycisk](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton "). Lub Otwórz menu skrótów i wybierz polecenie **pokazywanie w mapie kodu**. Możesz także przeciągnąć elementy z widoku klasy lub przeglądarki obiektów do nowej lub istniejącej mapy kodu.  

4.  [Zobacz określonych zależności](#SeeSpecificSource) zrozumieć sposób korzystania map kodu do wyświetlenia określonej zależności w ramach rozwiązania.  

###  <a name="CreateEmptyMap"></a> Aby dodać nowej mapy kodu pusty do rozwiązania  

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów węzeł rozwiązania najwyższego poziomu. Wybierz **Dodaj** wybierz **nowy element**.  

2.  W obszarze **zainstalowana**, wybierz **ogólne**.  

3.  W okienku po prawej stronie wybierz **dokument wykresu bezpośredniego** , a następnie wybierz **Dodaj**.  

     Masz teraz pusta mapa, która pojawia się w rozwiązania **elementy rozwiązania** folderu.  

#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>Aby utworzyć nowej mapy kodu pusty bez dodanie go do rozwiązania  

1.  Otwórz **architektura** menu i wybierz polecenie **nowej mapy kodu**.  

     \- lub -  

2.  Otwórz **pliku** menu i wybierz polecenie **nowy** wybierz **pliku**.  

3.  W obszarze **zainstalowana**, wybierz **ogólne**.  

4.  W okienku po prawej stronie wybierz **dokument wykresu bezpośredniego** , a następnie wybierz **Otwórz**.  

     Pusta mapa, która nie pojawia się w folderach tego rozwiązania jest teraz dostępna.  

##  <a name="SeeOverviewSource"></a> Zobacz ogólną zależności  

###  <a name="OverviewSource"></a> Zobacz zależności między rozwiązania  

1.  Na **architektura** menu, wybierz **Generuj mapę kodu dla rozwiązania**.  

     ![Generowanie polecenia mapy kodu](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")  

     Otrzymasz mapy, który pokazuje zagregowane łącza między nimi i zestawy najwyższego poziomu. Szersze łącze zagregowane, więcej zależności reprezentuje.  

2.  Użyj **legendy** przycisk na pasku narzędzi mapy kodu, aby pokazać lub ukryć listy ikony typu projektu (na przykład testu sieci Web i projektu telefonu), kod elementy (takie jak klas, metod i właściwości) i typy relacji (takich jak dziedziczy z Implementuje oraz wywołań).  

     ![TOP&#45;wykresu zależności poziomu zestawów](../modeling/media/dependencygraph_toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")  

     To rozwiązanie przykład zawiera foldery rozwiązania (**testy** i **składniki**), projekty testowe, projekty sieci Web i zestawów. Domyślnie wszystkie relacje zawierania są wyświetlane jako *grup*, które można zwijać i rozwijać. **Externals** grupa zawiera niczego poza rozwiązania, wraz z zależnościami platformy. Zestawy zewnętrzne pokazują tylko te elementy, które są używane. Domyślnie system typów podstawowych są ukryte na mapie, aby zwiększyć czytelność.  

3.  Aby przejść do mapy, rozwiń węzeł grupy, które reprezentują projektów i zespołów. Można rozwinąć wszystko, naciskając klawisz **klawisze CTRL + A** zaznacz wszystkie węzły i następnie wybranie **grupy**, **rozwiń** z menu skrótów.  

     ![Rozwijanie wszystkich grup w mapie kodu](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")  

4.  Jednak może to nie być przydatne w przypadku dużych rozwiązań. W rzeczywistości złożonych rozwiązań ograniczenia pamięci może uniemożliwić rozszerzania wszystkich grup. Zamiast tego aby wyświetlić wewnątrz jednego węzła, rozwiń go. Umieść wskaźnik myszy na węźle, a następnie kliknij cudzysłów ostrokątny (strzałkę) po wyświetleniu.  

     ![Rozwinięcie węzła w mapie kodu](../modeling/media/dependencygraph_containment.png "DependencyGraph_Containment")  

     Lub za pomocą klawiatury przez zaznaczenie go, a następnie naciśnięcie klawisza plus (**+**). Aby zapoznać się z bardziej poziomów kodu, wykonaj te same obszary nazw, typy i elementy członkowskie.  

    > [!TIP]
    >  Aby uzyskać więcej informacji o pracy z kodem mapy, przy użyciu myszy, klawiatury i touch, zobacz [przeglądania i zmieniać code map](../modeling/browse-and-rearrange-code-maps.md).  

5.  Aby uprościć mapy i skoncentrować się na poszczególnych części, wybierz **filtry** na pasku narzędzi mapy kodu i wybierz tylko typy węzłów i linków Cię interesuje. Na przykład można ukryć kontenerów Folder rozwiązania i zestawu.  

     ![Uproszczenia mapy filtrując kontenery](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")  

     Można również uprościć mapy ukrywanie lub usuwając poszczególnych grup i elementów z mapy, bez wywierania wpływu na podstawowe kodu rozwiązania.  

6.  Aby wyświetlić relacji między elementami, wybierz je w planie. Kolory łącza wskazują typy relacji, jak pokazano w **legendy** okienka.  

     ![Służy do wyświetlania zależności w ramach rozwiązań](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  

     W tym przykładzie purpurowa łącza są wywołaniami kropkowanej łącza są odwołania i światła niebieski łącza są dostępu do pola. Zielony łącza może być dziedziczenia lub mogą być *agregacji łącza* wskazujących na więcej niż jeden typ relacji (lub *kategorii*).  

    > [!TIP]
    >  Jeśli zostanie wyświetlony zielony łącza, nie może oznaczać, że tylko na relację dziedziczenia. Mogą również istnieć wywołania metody, ale są one ukryte przez relację dziedziczenia. Aby wyświetlić określone typy łączy, użyj pola wyboru w **filtry** okienko, aby ukryć typów nie chcesz.  

7.  Aby uzyskać więcej informacji na temat elementu lub łącza, umieść kursor na go, dopóki nie jest wyświetlany w etykietce narzędzia. Wskazuje szczegóły elementu kodu lub kategorie, które reprezentuje łącze.  

     ![Pokaż kategorie relacji](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")  

8.  Badanie elementów i zależności reprezentowany przez łącze zagregowane, najpierw wybierz łącze, a następnie otwórz jego menu skrótów. Wybierz **Pokaż linki** (lub **Pokaż linki na nowej mapie kodu**). Rozwija grupy na obu zakończeniach łącza i pokazuje tylko te elementy i zależności, które uczestniczą w łączu.  

9. Aby skoncentrować się na określonej części mapy można usunąć elementy, których nie chcesz. Na przykład, aby przejść do widoku klasy i element członkowski, po prostu filtrować wszystkie węzły przestrzeni nazw w **filtry** okienka.  

     ![Przechodzenie do klasy i element członkowski poziomu](../modeling/media/dependencygraph_expandedselectedgroups_2012.png "DependencyGraph_ExpandedSelectedGroups_2012")  

10. Innym sposobem fokusu w na mapie złożone rozwiązanie polega na generowaniu nowej mapy zawierający wybrane elementy z istniejącej mapy. Przytrzymaj **CTRL** podczas wybierania elementów chcesz skupić się na, otwórz menu skrótów i wybierz **nowy wykres na podstawie wyboru**.  

     ![Pokaż elementy wybrane na nowej mapie kodu](../modeling/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")  

11. Kontekst zawierający są przenoszone do nowej mapy. Ukryj foldery rozwiązania i inne kontenery nie chcesz, aby wyświetlić przy użyciu **filtry** okienka.  

     ![Filtruj kontener, aby uprościć widok](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")  

12. Rozwiń grupy, a następnie wybierz elementy na mapie, aby wyświetlić relacji.  

     ![Wybierz elementy, aby wyświetlić relacje](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")  

 Zobacz też:  

-   [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)  

-   [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)  

-   Wyszukiwanie potencjalnych problemów w kodzie przez [uruchamiania analizatora](../modeling/find-potential-problems-using-code-map-analyzers.md).  

###  <a name="OverviewCompiled"></a> Zobacz zależności między zestawów lub plików binarnych  

1.  [Utwórz mapę kodu pusty](#GetStarted), lub Otwórz istniejący mapę kodu (plik .dgml).  

2.  Przeciągnij zestawy lub dane binarne do mapowania z zewnętrznego programu Visual Studio na mapę. Na przykład przeciągnij zestawy lub plików binarnych z Eksploratora Windows lub Eksploratora plików.  

> [!NOTE]
>  Tylko wtedy, gdy są uruchomione na tym samym poziomie uprawnień kontroli dostępu użytkownika (UAC) i Visual Studio można przeciągnąć z zestawów lub plików binarnych z Eksploratora Windows lub Eksploratora plików. Na przykład jeśli jest włączona funkcja Kontrola konta użytkownika i używasz programu Visual Studio jako Administrator, Eksploratora Windows lub Eksploratora plików będzie blokował operację przeciągania. Aby obejść ten problem, upewnij się, że obydwa są uruchomione na tym samym poziomie uprawnień lub wyłączanie funkcji Kontrola konta użytkownika.  

##  <a name="SeeSpecificSource"></a> Zobacz określonych zależności  
 Na przykład załóżmy, że masz przeglądu kodu do wykonania w niektóre pliki z oczekujących zmian. Aby wyświetlić zależności w tych zmian, można utworzyć mapę kodu z tych plików.  

 ![Pokaż zależności określone w mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  

### <a name="see-specific-dependencies-in-your-solution"></a>Zobacz określonych zależności w rozwiązaniu  

1.  Otwórz **Eksploratora rozwiązań**. Wybierz projekty, odwołania do zestawów, folderów, plików, typy i elementy członkowskie, które są potrzebne. Aby znaleźć elementy, które są zależne od typów albo elementów członkowskich, otworzyć tego typu lub elementu członkowskiego menu skrótów z **Eksploratora rozwiązań**. Wybierz typ, a następnie wybierz wyniki.  

2.  Mapy elementów i ich elementy członkowskie. Na **Eksploratora rozwiązań** narzędzi kliknij przycisk **pokazywanie w mapie kodu**![Utwórz nowy wykres z wybrane węzły przycisk](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").  

     ![Wybierz elementy do mapowania](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")  

3.  Mapa pokazuje wybrane elementy w ich zawierającego zestawy.  

     ![Wybrane elementy wyświetlane jako grupy na mapie](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")  

     Możesz także przeciągnąć elementy z Eksploratora rozwiązań, Widok klas lub przeglądarki obiektów na pusty lub istniejącej mapy kodu. Aby utworzyć pusty mapy, zobacz [utworzyć mapę kodu pusty](#GetStarted). Aby uwzględnić hierarchii nadrzędnej dla elementów, naciśnij i przytrzymaj klawisz **CTRL** klucza podczas przeciągnij elementy, lub użyj **obejmują nadrzędnych** przycisk na pasku narzędzi mapy kodu, aby określić domyślną akcję.  

    > [!NOTE]
    >  Po dodaniu elementów z projektu, który jest współużytkowany przez wiele aplikacji, takich jak Windows Phone lub Sklep Windows, elementy te są widoczne na mapie z projektem aktualnie aktywnych aplikacji. Po zmianie kontekstu do innego projektu aplikacji i dodaniu większej liczby elementów z udostępnionego projektu pojawiają się elementy z projektem nowych aktywnych aplikacji. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.  

4.  Aby zapoznać się z elementów, rozwiń je. Umieść kursor myszy na element, a następnie kliknij ikonę cudzysłów ostrokątny (strzałkę), gdy pojawi się on.  

     ![Rozwinięcie węzła w mapie kodu](../modeling/media/dependencygraph_containment.png "DependencyGraph_Containment")  

     Aby rozszerzyć wszystkie elementy, zaznacz je przy użyciu **klawisze CTRL + A**, otwórz menu skrótów mapy i wybierz **grupy**, **rozwiń**. Jednak ta opcja jest niedostępna, jeśli rozszerzania wszystkich grup tworzy mapę bezużyteczne lub problemy z pamięcią.  

5.  Nadal rozwijanie elementów, które planuje się, z dokładnością do poziomu klasy i element członkowski w razie potrzeby.  

     ![Rozwiń węzeł grupy na poziomie klasy i element członkowski](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")  

     Aby wyświetlić elementy członkowskie, które znajdują się w kodzie, ale nie są widoczne na mapie, kliknij **Refetch dzieci** ikona ![Refetch ikony elementów podrzędnych](../modeling/media/dependencygraph_deletednodesicon.png "DependencyGraph_DeletedNodesIcon") w górnym lewego rogu grupy.  

6.  Aby zobaczyć więcej elementów związanych z tymi na mapie, wybierz jedną i wybierz polecenie **Pokaż powiązane** na pasku narzędzi mapy kodu, a następnie wybierz typ powiązane elementy do dodania do mapy. Możesz też wybrać jeden lub więcej elementów, otwórz menu skrótów, a następnie wybierz **Pokaż...**  opcję dla typu elementów pokrewnych, aby dodać do mapy. Na przykład:  

     Aby uzyskać **zestawu**, wybierz:  

    |||  
    |-|-|  
    |**Pokaż zestawy przywoływane przez ten element**|Dodaj zestawy, do których odwołuje się ten zestaw. Zestawy zewnętrzne są wyświetlane w **Externals** grupy.|  
    |**Pokaż zestawy PRZYWOŁUJĄCE ten element**|Dodaj zestawy w rozwiązaniu odwołującym się do tego zestawu.|  

     Dla **przestrzeni nazw**, wybierz **Pokaż zestawu zawierającego**, jeśli nie jest widoczna.  

     Aby uzyskać **klasy** lub **interfejsu**, wybierz:  

    |||  
    |-|-|  
    |**Pokaż typy podstawowe**|Dla klasy dodaj klasę bazową i implementowane interfejsy.<br /><br /> Dla interfejsu dodaj interfejsy podstawowe.|  
    |**Pokaż typy pochodne**|Dla klasy dodaj klasy pochodne.<br /><br /> Dla interfejsu dodaj interfejsy pochodne i implementujące klasy lub struktury.|  
    |**Pokaż typy przywoływane przez ten element**|Dodaj wszystkie klasy i używane przez nie składowe.|  
    |**Pokaż typy PRZYWOŁUJĄCE ten element**|Dodaj wszystkie klasy oraz ich składowe, które używają tej klasy.|  
    |**Pokaż zawierający Namespace**|Dodaj nadrzędną przestrzeń nazw.|  
    |**Pokaż zawierający Namespace i zestawu**|Dodaj hierarchię kontenera nadrzędnego.|  
    |**Pokaż wszystkie typy podstawowe**|Dodaj cyklicznie klasę bazową lub hierarchię interfejsu.|  
    |**Pokaż wszystkie typy pochodne**|Dla klasy dodaj wszystkie klasy pochodne cyklicznie.<br /><br /> Dla interfejsu, dodaj wszystkie interfejsy pochodne i cyklicznie implementujące klasy lub struktury.|  

     Aby uzyskać **metody**, wybierz:  

    |||  
    |-|-|  
    |**Pokaż metody wywoływane przez ten element**|Dodaj metody, które wywołuje ta metoda.|  
    |**Pokaż pola przywoływane przez ten element**|Dodaj pola, do których odwołuje się ta metoda.|  
    |**Pokaż zawierający typ**|Dodaj typ nadrzędny.|  
    |**Pokaż zawierający typ, Namespace i zestawu**|Dodaj hierarchię kontenera nadrzędnego.|  
    |**Pokaż przesłoniętej metody**|Dla metody, która zastępuje inne metody lub implementuje metodę interfejsu, należy dodać wszystkie metody abstrakcyjne lub wirtualne w klasach bazowych, które są zastępowane, oraz — jeśli istnieje — implementowaną metodę interfejsu.|  

     Aby uzyskać **pola** lub **właściwości**, wybierz:  

    |||  
    |-|-|  
    |**Pokaż zawierający typ**|Dodaj typ nadrzędny.|  
    |**Pokaż zawierający typ, Namespace i zestawu**|Dodaj hierarchię kontenera nadrzędnego.|  

     ![Pokaż metody wywoływane przez ten element członkowski](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")  

7.  Mapy przedstawiono relacje. W tym przykładzie metody wywoływane przez `Find` — metoda i ich lokalizacji w rozwiązaniu lub zewnętrznie.  

     ![Pokaż zależności określone w mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  

8.  Aby uprościć mapy i skoncentrować się na poszczególnych części, wybierz **filtry** na pasku narzędzi mapy kodu i wybierz tylko typy węzłów i linków Cię interesuje. Na przykład Wyłącz wyświetlanie foldery rozwiązania, zestawy i przestrzenie nazw.  

     ![Okienko filtru umożliwia uproszczenie wyświetlania](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")  

##  <a name="SeeSourceHeader"></a> Zobacz zależności między pliki źródłowe C i C++ i pliki nagłówkowe  
 Jeśli chcesz utworzyć bardziej szczegółowy mapy dla projektów C++, ustaw opcję kompilatora informacji o przeglądaniu (**/FR**) na tych projektów. W przeciwnym razie pojawi się komunikat i monit o ustawienie tej opcji. W przypadku wybrania **OK**, to ustawienie opcji dla bieżącej mapy. Można ukryć w komunikacie wszystkie nowsze mapy. Ukryj tę wiadomość, można wyświetlić ją ponownie. Ustawiono następujący klucz rejestru `0` lub usunąć klucza:  

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\NativeProvider : AutoEnableSbr**  

 Po otwarciu rozwiązania, które zawiera projekty Visual C++, aktualizacja bazy danych w technologii IntelliSense może zająć trochę czasu. W tym czasie nie można utworzyć mapy kodu dla nagłówka (.h lub `#include`) pliki zakończenie bazy danych IntelliSense aktualizacji. Można monitorować postęp uaktualnienia na pasku stanu programu Visual Studio. Aby rozwiązać problemy lub komunikaty wyświetlane, ponieważ niektóre ustawienia IntelliSense są wyłączone, zobacz [Rozwiązywanie problemów z mapy dla kodu C i C++](#Troubleshooting).  

-   Aby wyświetlić zależności między wszystkie pliki źródłowe i pliki nagłówkowe w rozwiązaniu, **architektura** menu, wybierz **Generuj wykres z pliki dołączane**.  

     ![Wykres zależności dla kodu natywnego](../modeling/media/dependencygraphgeneral_nativecode.png "DependencyGraphGeneral_NativeCode")  

-   Aby wyświetlić zależności między aktualnie otwarty plik i pliki źródłowe pokrewne i pliki nagłówkowe, otwórz plik źródłowy lub plik nagłówka. Otwórz menu skrótów pliku dowolne miejsce w pliku. Wybierz **Generowanie grafu plików dołączanych**.  

     ![Pierwszy&#45;wykresu zależności poziomu pliku .h](../modeling/media/dependencygraph_native_firstlevel.png "DependencyGraph_Native_FirstLevel")  

###  <a name="Troubleshooting"></a> Rozwiązywanie problemów z mapy dla kodu C i C++  
 Te elementy nie są obsługiwane dla kodu C i C++:  

-   Typy podstawowe nie pojawiają się w społeczności maps, które obejmują hierarchii nadrzędnej.  

-   Większość **Pokaż** elementy menu są niedostępne dla kodu C i C++.  

 Te problemy może się zdarzyć, gdy tworzenie map kodu dla kodu C i C++:  

|**Problem**|**Możliwa przyczyna**|**Rozdzielczość**|  
|---------------|------------------------|--------------------|  
|Nie można wygenerować mapy kodu.|Żadne projekty w rozwiązaniu nie zostały pomyślnie skompilowane.|Błędy kompilacji, które wystąpiły, a następnie ponownie wygenerować mapy.|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przestaje odpowiadać podczas próby Generuj mapę kodu z **architektura** menu.|Plik bazy danych programu (.pdb) może być uszkodzony.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Kompiluj rozwiązanie ponownie, a następnie spróbuj jeszcze raz.|  
|Niektóre ustawienia dla bazy danych przeglądania IntelliSense są wyłączone.|Niektóre ustawienia IntelliSense może być wyłączone w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **opcje** okno dialogowe.|Włącz te ustawienia.<br /><br /> Zobacz [opcje, Edytor tekstu, C/C++, zaawansowane](../ide/reference/options-text-editor-c-cpp-advanced.md).|  
|Komunikat **nieznanych metod** pojawia się w węźle metody.<br /><br /> Ten problem występuje, ponieważ nie można rozpoznać nazwy metody.|Plik binarny może nie mieć podstawowej tabeli relokacji.|Włącz **/Fixed: No** opcji w konsolidatorze.|  
||Plik bazy danych programu (.pdb) może nie być skompilowany.<br /><br /> Plik .pdb przechowuje informacje debugowania, takie jak typ, metoda i informacje o pliku źródłowym.|Włącz **/DEBUG** opcji w konsolidatorze.|  
||Nie można otworzyć lub znaleźć pliku .pdb w oczekiwanych lokalizacjach.|Upewnij się, że plik .pdb istnieje w oczekiwanych lokalizacjach.|  
||Informacje o debugowaniu pochodzą z pliku .pdb.|Jeśli **/pdbstripped** użyto opcji w konsolidatorze, zamiast tego zawiera cały plik PDB.|  
||Obiekt wywołujący nie jest funkcją i jest albo osadzony w pliku binarnym, albo stanowi wskaźnik w sekcji danych.|Gdy obiekt wywołujący jest sekcją thunk, spróbuj użyć `_declspec(dllimport)` w celu uniknięcia thunk.|  

##  <a name="RenderMoreQuickly"></a> Wprowadź kod, który mapy szybciej renderowania  
 Podczas generowania mapy po raz pierwszy, program Visual Studio indeksuje wszystkie zależności, które znajdzie. Ten proces może trochę potrwać, szczególnie w przypadku dużych rozwiązaniach, ale zwiększa wydajność później. Zmiana kodu programu Visual Studio ponowna indeksacja zaktualizowanego kodu. Aby zminimalizować czas poświęcony na mapie, aby zakończyć renderowania, należy rozważyć następujące kwestie:  

-   [Mapowanie tylko zależności, które są potrzebne.](#SeeSpecificSource)  

-   Aby wygenerować mapy dla całego rozwiązania, należy zawęzić zakres rozwiązania.  

-   Wyłącz automatyczne kompilacji dla rozwiązania z **pominięcia kompilacji** przycisk na pasku narzędzi mapy kodu.  

-   Wyłączanie automatycznego dodawania elementów nadrzędnych z **obejmują nadrzędnych** przycisk na pasku narzędzi mapy kodu.  

-   Przeprowadź edycję pliku mapy kodu bezpośrednio do usuń węzły i łącza, które nie są potrzebne. Zmiana mapy nie wpływa na kod źródłowy. Zobacz [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  

 ![Przyciski pominięcia kompilacji i obejmują nadrzędnych](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")  

 Mimo że program Visual Studio można uruchomić z 1 GB pamięci, zaleca się, że komputer ma co najmniej 2 GB pamięci na uniknięcie długie opóźnienia Visual Studio tworzy indeks kodu i generuje mapy.  

 Może zająć więcej czasu na tworzenie map lub Dodaj elementy do mapy w Eksploratorze rozwiązań, gdy element projektu **Kopiuj do katalogu wyjściowego** właściwość jest ustawiona na **zawsze Kopiuj**. Może to spowodować problemy z kompilacjami przyrostowymi i każdorazowe ponowne kompilowanie projektu przez program Visual Studio. Aby zwiększyć wydajność, należy zmienić tę właściwość, aby **Kopiuj, jeśli nowszy** lub `PreserveNewest`. Zobacz [kompilacji przyrostowej](../msbuild/incremental-builds.md).  

 Ukończono mapy wyświetli zależności tylko w przypadku pomyślnie skompilowany kod. Jeśli występują błędy kompilacji dla niektórych składników, te błędy są wyświetlane na mapie. Upewnij się, że składnik faktycznie tworzy i ma zależności z przed wprowadzeniem architektury decyzje na podstawie na mapie.  

##  <a name="SavingExporting"></a> Udostępnianie mapy kodu  

### <a name="share-the-map-with-other-visual-studio-users"></a>Udostępnij mapy innych użytkowników programu Visual Studio  
 Użyj **pliku** menu, aby zapisać mapy.  

 —lub—  

 Aby zapisać mapy w ramach danego projektu, na pasku narzędzi mapy, wybierz **udziału**, **Przenieś** \< *CodeMapName*>**.dgml do**, a następnie wybierz projekt, gdzie chcesz zapisać mapy.  

 ![Przenieś mapy do innego projektu](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")  

 Visual Studio zapisuje mapy jako plik .dgml, które można udostępniać innym użytkownikom programu Visual Studio Enterprise i Visual Studio Professional.  

> [!NOTE]
>  Przed udostępnieniem mapy osób, które używają programu Visual Studio Professional, upewnij się, że wszystkie grupy rozwiń, Pokaż ukryte węzły i linki międzygrupowe i pobierać żadnych usuniętych węzłów, które mają być widoczne na mapie. W przeciwnym razie inni użytkownicy nie będą mogli zobaczyć tych elementów.  
>   
>  Po zapisaniu mapy, który znajduje się w projekcie modelowania lub został skopiowany z projektem modelowania do innej lokalizacji, może wystąpić następujący błąd:  
>   
>  "Nie można zapisać *fileName* poza katalogiem projektu. Elementy połączone nie są obsługiwane”.  
>   
>  Program Visual Studio pokazuje błąd, ale mimo to tworzy zapisaną wersję. Aby uniknąć tego błędu, należy utworzyć mapy spoza projektu modelowania. Można następnie zapisać go w dowolnej lokalizacji. Skopiowanie pliku do innej lokalizacji w rozwiązaniu, a następnie próba zapisu zakończą się niepowodzeniem.  

### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Eksportuj mapy jako obraz, skopiuj go do innych aplikacji, takich jak Microsoft Word czy PowerPoint  

1.  Na pasku narzędzi mapy kodu, wybierz **udziału**, **poczty E-mail jako obraz** lub **Kopiuj obraz**.  

2.  Wklej obraz do innej aplikacji.  

### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Eksportuj mapy jako plik XPS, tak aby był widoczny w XML lub XAML przeglądarki, takich jak program Internet Explorer  

1.  Na pasku narzędzi mapy kodu, wybierz **udziału**, **poczty E-mail jako przenośne XPS** lub **zapisać przenośnych XPS**.  

2.  Przejdź do której chcesz zapisać plik.  

3.  Nazwa mapy kodu. Upewnij się, że **Zapisz jako typ** pole ma ustawioną wartość **plików XPS (\*XPS)**. Wybierz **zapisać**.  

## <a name="what-else-can-i-do"></a>Co jeszcze można zrobić?  

-   [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)  

-   [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)  

-   [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)  

-   [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)  

-   [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
