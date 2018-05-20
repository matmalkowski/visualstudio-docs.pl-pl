---
title: Mapy kodu
ms.date: 05/16/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 553e2437abc2d8f498b556300a9266c9e79297f7
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="map-dependencies-with-code-maps"></a>Zależności mapy z mapy kodu

Zależności można zwizualizować w kodzie przez utworzenie mapy kodu. Kod mapy pomocy, zobacz, jak kod dopasowuje razem przed odczytaniem za pośrednictwem plików i wierszy kodu.

![Wyświetlanie zależności w ramach rozwiązań](../modeling/media/codemapsmainintro.png)

Aby użyć mapy kodu, potrzebujesz programu Visual Studio Enterprise lub Professional edition. Funkcje mapy kodu w wersji Professional wynosi wymaga nieco więcej niż w wersji Enterprise.

> [!NOTE]
> Przed udostępnieniem mapy utworzone w programie Visual Studio Enterprise z innymi korzystający z programu Visual Studio Professional, upewnij się, że wszystkie elementy na mapie (takie jak ukryte elementy, rozwinięte grupy i linki międzygrupowe) są widoczne.

Możesz mapować zależności dla kodu w tych językach:

- Visual C# lub Visual Basic w rozwiązaniu lub zestawów (*.dll* lub *.exe*)

- Natywnego lub zarządzanego kodu C lub C++ w projektach Visual C++, pliki nagłówkowe (*.h* lub `#include`), lub plików binarnych

- X ++, projekty i zestawy wprowadzone z modułów .NET dla programu Microsoft Dynamics AX

> [!NOTE]
> Dla innych projektów C# lub Visual Basic dostępne są mniej opcje uruchamiania mapę kodu lub dodawanie elementów do istniejącej mapy kodu. Nie można na przykład, kliknij prawym przyciskiem myszy obiekt w edytorze tekstu projektu C++ i dodaj go do mapy kodu. Jednak możesz przeciągać i upuszczać elementy poszczególnych kodu lub pliki z **Eksploratora rozwiązań**, **widoku klasy**, i **przeglądarki obiektów**.

## <a name="install-code-map-and-live-dependency-validation"></a>Mapy kodu instalacja i weryfikacja zależności na żywo

Aby utworzyć mapę kodu w programie Visual Studio 2017, należy najpierw zainstalować **mapy kodu** i **Live walidacji zależności** składniki:

1. Otwórz **Instalator Visual Studio**. Możesz otworzyć go w menu Start systemu Windows lub w programie Visual Studio, wybierając **narzędzia** > **Pobierz narzędzia i funkcje**.

1. Wybierz **pojedynczych składników** kartę.

1. Przewiń w dół do **kodu narzędzia** a następnie wybierz opcję **mapy kodu** i **Live walidacji zależności**.

   ![Składniki mapy kodu i na żywo walidacji zależności w Instalator programu Visual Studio](media/modeling-components.png)

1. Wybierz **zmodyfikować**.

   **Mapy kodu** i **Live walidacji zależności** składniki rozpoczęcie instalacji. Może być monit Zamknij program Visual Studio.

## <a name="add-a-code-map"></a>Dodaj mapę kodu

Można utworzyć mapę kodu pusty i przeciągnij elementy on odwołania do zestawów, pliki i foldery, w tym lub można wygenerować mapę kodu dla wszystkich lub część rozwiązania.

Aby dodać mapy kodu pusta:

1. W **Eksploratora rozwiązań**, otwórz menu skrótów węzeł rozwiązania najwyższego poziomu. Wybierz **dodać** > **nowy element**.

2. W **Dodaj nowy element** okna dialogowego, w obszarze **zainstalowana**, wybierz **ogólne** kategorii.

3. Wybierz **kierowany Graf Document(.dgml)** szablonu, a następnie wybierz **Dodaj**.

   > [!TIP]
   > Ten szablon nie może występować alfabetycznie, dlatego przewiń w dół listy szablonu, jeśli nie widzisz.

   Mapy puste, zostanie wyświetlony w rozwiązania **elementy rozwiązania** folderu.

Podobnie można utworzyć nowego pliku mapy kodu bez dodanie go do rozwiązania, wybierając **architektura** > **nowej mapy kodu** lub **pliku**  >  **Nowe** > **pliku**.

## <a name="generate-a-code-map-for-your-solution"></a>Generuj mapę kodu dla rozwiązania

Aby wyświetlić wszystkie zależności w rozwiązaniu:

1. Na pasku menu wybierz **architektura** > **Generuj mapę kodu dla rozwiązania**. Jeśli kod nie zmieniła się od czasu ostatniego utworzono go, możesz wybrać **architektura** > **Generuj mapę kodu dla rozwiązania bez tworzenia** zamiast tego.

   ![Generowanie polecenia mapy kodu](../modeling/media/codemapsarchitecturemenu.png)

   Mapy jest generowany, który pokazuje zagregowane łącza między nimi i zestawy najwyższego poziomu. Szersze łącze zagregowane, więcej zależności reprezentuje.

2. Użyj **legendy** przycisk na pasku narzędzi mapy kodu, aby pokazać lub ukryć listy ikony typu projektu (na przykład testu sieci Web i projektu telefonu), kod elementy (takie jak klas, metod i właściwości) i typy relacji (takich jak dziedziczy z Implementuje oraz wywołań).

   ![Wykres zależności najwyższego poziomu zestawów](../modeling/media/dependencygraph_toplevelassemblies.png)

   To rozwiązanie przykład zawiera foldery rozwiązania (**testy** i **składniki**), projekty testowe, projekty sieci Web i zestawów. Domyślnie wszystkie relacje zawierania są wyświetlane jako *grup*, które można zwijać i rozwijać. **Externals** grupa zawiera niczego poza rozwiązania, wraz z zależnościami platformy. Zestawy zewnętrzne pokazują tylko te elementy, które są używane. Domyślnie system typów podstawowych są ukryte na mapie, aby zwiększyć czytelność.

3. Aby przejść do mapy, rozwiń węzeł grupy, które reprezentują projektów i zespołów. Można rozwinąć wszystko, naciskając klawisz **klawisze CTRL + A** zaznacz wszystkie węzły i następnie wybranie **grupy**, **rozwiń** z menu skrótów.

   ![Rozwijanie wszystkich grup w mapie kodu](../modeling/media/codemapsexpandallgroups.png)

4. Jednak może to nie być przydatne w przypadku dużych rozwiązań. W rzeczywistości złożonych rozwiązań ograniczenia pamięci może uniemożliwić rozszerzania wszystkich grup. Zamiast tego aby wyświetlić wewnątrz jednego węzła, rozwiń go. Umieść wskaźnik myszy na węźle, a następnie kliknij cudzysłów ostrokątny (strzałkę) po wyświetleniu.

   ![Rozwinięcie węzła w mapie kodu](../modeling/media/dependencygraph_containment.png)

   Lub za pomocą klawiatury przez zaznaczenie go, a następnie naciśnięcie klawisza plus (**+**). Aby zapoznać się z bardziej poziomów kodu, wykonaj te same obszary nazw, typy i elementy członkowskie.

   > [!TIP]
   > Aby uzyskać więcej informacji na temat pracy z kodem mapy, przy użyciu myszy, klawiatury i touch, zobacz [przeglądania i zmieniać code map](../modeling/browse-and-rearrange-code-maps.md).

5. Aby uprościć mapy i skoncentrować się na poszczególnych części, wybierz **filtry** na pasku narzędzi mapy kodu i wybierz tylko typy węzłów i linków Cię interesuje. Na przykład można ukryć kontenerów Folder rozwiązania i zestawu.

   ![Uproszczenia mapy filtrując kontenerów](../modeling/media/codemapsfilterfoldersassemblies.png)

   Można również uprościć mapy ukrywanie lub usuwając poszczególnych grup i elementów z mapy, bez wywierania wpływu na podstawowe kodu rozwiązania.

6. Aby wyświetlić relacji między elementami, wybierz je w planie. Kolory łącza wskazują typy relacji, jak pokazano w **legendy** okienka.

   ![Wyświetlanie zależności w ramach rozwiązań](../modeling/media/codemapsmainintro.png)

   W tym przykładzie purpurowa łącza są wywołaniami kropkowanej łącza są odwołania i światła niebieski łącza są dostępu do pola. Zielony łącza może być dziedziczenia lub mogą być *agregacji łącza* wskazujących na więcej niż jeden typ relacji (lub *kategorii*).

   > [!TIP]
   > Jeśli zostanie wyświetlony zielony łącza, nie może oznaczać, że tylko na relację dziedziczenia. Mogą również istnieć wywołania metody, ale są one ukryte przez relację dziedziczenia. Aby wyświetlić określone typy łączy, użyj pola wyboru w **filtry** okienko, aby ukryć typów nie chcesz.

7. Aby uzyskać więcej informacji na temat elementu lub łącza, umieść kursor na go, dopóki nie jest wyświetlany w etykietce narzędzia. Wskazuje szczegóły elementu kodu lub kategorie, które reprezentuje łącze.

   ![Pokaż kategorie relacji](../modeling/media/codemapsshowlinkcatgories.png)

8. Badanie elementów i zależności reprezentowany przez łącze zagregowane, najpierw wybierz łącze, a następnie otwórz jego menu skrótów. Wybierz **Pokaż linki** (lub **Pokaż linki na nowej mapie kodu**). Rozwija grupy na obu zakończeniach łącza i pokazuje tylko te elementy i zależności, które uczestniczą w łączu.

9. Aby skoncentrować się na określonej części mapy można usunąć elementy, których nie chcesz. Na przykład, aby przejść do widoku klasy i element członkowski, po prostu filtrować wszystkie węzły przestrzeni nazw w **filtry** okienka.

   ![Przechodzenie do poziomu klasy i element członkowski](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Innym sposobem fokusu w na mapie złożone rozwiązanie polega na generowaniu nowej mapy zawierający wybrane elementy z istniejącej mapy. Przytrzymaj **Ctrl** podczas wybierania elementów chcesz skupić się na, otwórz menu skrótów i wybierz **nowy wykres na podstawie wyboru**.

   ![Pokaż elementy wybrane na nowej mapie kodu](../modeling/media/codemapsshowonnewmap.png)

11. Kontekst zawierający są przenoszone do nowej mapy. Ukryj foldery rozwiązania i inne kontenery nie chcesz, aby wyświetlić przy użyciu **filtry** okienka.

   ![Filtruj kontener, aby uprościć widoku](../modeling/media/codemapsexpandnewgroups.png)

12. Rozwiń grupy, a następnie wybierz elementy na mapie, aby wyświetlić relacji.

   ![Wybierz elementy, aby wyświetlić relacji](../modeling/media/codemapsviewnewrelationships.png)

Zobacz też:

- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Wyszukiwanie potencjalnych problemów w kodzie przez [uruchamiania analizatora](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-specific-dependencies-in-a-code-map"></a>Wyświetlanie określonych zależności w mapie kodu

Załóżmy, że masz przeglądu kodu do wykonania w niektóre pliki z oczekujących zmian. Aby wyświetlić zależności w tych zmian, można utworzyć mapę kodu z tych plików.

   ![Pokaż zależności określone w mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png)

1. W **Eksploratora rozwiązań**, wybierz projekty, odwołania do zestawów, folderów, plików, typów lub elementów członkowskich, które ma być mapowany.

   ![Wybierz elementy, które chcesz mapy](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Na **Eksploratora rozwiązań** narzędzi wybierz **pokazywanie w mapie kodu** ![Utwórz nowy wykres z wybrane węzły przycisk](../modeling/media/createnewgraphfromselectedbutton.gif). Lub, otwórz menu skrótów dla co najmniej grupę elementów i wybierz polecenie **pokazywanie w mapie kodu**.

   Możesz także przeciągnąć elementy z **Eksploratora rozwiązań**, **widoku klasy**, lub **przeglądarki obiektów**, do [nowe](#add-a-code-map) lub istniejącego kodu mapy. Aby uwzględnić hierarchii nadrzędnej dla elementów, naciśnij i przytrzymaj klawisz **Ctrl** klucza podczas przeciągnij elementy, lub użyj **obejmują nadrzędnych** przycisk na pasku narzędzi mapy kodu, aby określić domyślną akcję. Możesz także przeciągnąć pliki zestawu z zewnętrznego programu Visual Studio, takich jak, z **Eksploratora Windows**.

   > [!NOTE]
   > Po dodaniu elementów z projektu, który jest współużytkowany przez wiele aplikacji, takich jak Windows Phone lub Microsoft Store te elementy są widoczne na mapie z projektu aplikacji obecnie aktywne. Po zmianie kontekstu do innego projektu aplikacji i dodaniu większej liczby elementów z udostępnionego projektu pojawiają się elementy z projektem nowych aktywnych aplikacji. Operacje wykonywane za pomocą elementu na mapie dotyczą tylko tych elementów, które współużytkują ten sam kontekst.

3. Mapa pokazuje wybrane elementy w ich zawierającego zestawy.

   ![Wybrane elementy wyświetlane jako grupy na mapie](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Aby zapoznać się z elementów, rozwiń je. Umieść kursor myszy na element, a następnie kliknij ikonę cudzysłów ostrokątny (strzałkę), gdy pojawi się on.

   ![Rozwiń węzeł w mapie kodu](../modeling/media/dependencygraph_containment.png)

   Aby rozszerzyć wszystkie elementy, zaznacz je przy użyciu **Ctrl**+**A**, otwórz menu skrótów mapy i wybierz **grupy**  >   **Rozwiń węzeł**. Jednak ta opcja jest niedostępna, jeśli rozszerzania wszystkich grup tworzy mapę bezużyteczne lub problemy z pamięcią.

5. Nadal rozwijanie elementów, które planuje się, z dokładnością do poziomu klasy i element członkowski w razie potrzeby.

   ![Rozwiń węzeł grupy na poziomie klasy i element członkowski](../modeling/media/codemapsexpandtoclassandmember.png)

   Aby wyświetlić elementy członkowskie, które znajdują się w kodzie, ale nie są widoczne na mapie, kliknij **Refetch dzieci** ikona ![Refetch ikony elementów podrzędnych](../modeling/media/dependencygraph_deletednodesicon.png) w lewym górnym rogu grupy.

6. Aby zobaczyć więcej elementów związanych z tymi na mapie, wybierz jedną i wybierz polecenie **Pokaż powiązane** na pasku narzędzi mapy kodu, a następnie wybierz typ powiązane elementy do dodania do mapy. Możesz też wybrać jeden lub więcej elementów, otwórz menu skrótów, a następnie wybierz **Pokaż** opcję dla typu elementów pokrewnych, aby dodać do mapy. Na przykład:

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

    ![Pokaż metody wywoływane przez ten element członkowski](../modeling/media/codemapsshowrelatedmethods.png)

7. Mapy przedstawiono relacje. W tym przykładzie mapy zawiera metody wywoływane przez `Find` — metoda i ich lokalizacji w rozwiązaniu lub zewnętrznie.

   ![Pokaż zależności określone w mapie kodu](../modeling/media/codemapsspecificdependenciesintro.png)

8. Aby uprościć mapy i skoncentrować się na poszczególnych części, wybierz **filtry** na pasku narzędzi mapy kodu i wybierz tylko typy węzłów i linków Cię interesuje. Na przykład Wyłącz wyświetlanie foldery rozwiązania, zestawy i przestrzenie nazw.

   ![Upraszczanie wyświetlania przy użyciu okienka filtru](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Zobacz także

- [Wideo: zrozumienie projektu z kodu przy użyciu map kodu programu Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)]
- [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)
- [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)
- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
