---
title: "Wprowadzenie do korzystania z języków specyficznego dla domeny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: "16"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 4dd9df4832e08d33a8209181e47a38101a5658f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="getting-started-with-domain-specific-languages"></a>Wprowadzenie do języków specyficznych dla domeny
W tym temacie opisano podstawowe pojęcia związane z definiowanie i przy użyciu języka specyficznego dla domeny (DSL) utworzone przy użyciu zestawu SDK modelowania dla programu Visual Studio.  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 Jeśli jesteś nowym użytkownikiem DSLs, zaleca się pracę za pośrednictwem **laboratorium narzędzia DSL**, która znajduje się w tej witrynie: [Visualizaton i modelowanie zestawu SDK](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
## <a name="what-can-you-do-with-a-domain-specific-language"></a>Co należy zrobić z języka specyficznego dla domeny  
 Języka specyficznego dla domeny jest notacji, zwykle graficzny przeznaczony do użycia do określonego celu. Z kolei języków, takich jak UML są ogólnego przeznaczenia. W DSL można zdefiniować rodzaje elementu modelu i ich relacje i jak mają być przedstawiane na ekranie.  
  
 Po zaprojektowaniu DSL można rozpowszechniać go jako część pakietu rozszerzenia integracji programu Visual Studio (VSIX). Użytkownicy pracować z DSL w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
 ![Diagram drzewa rodziny, przybornika i explorer](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
 Jest tylko część DSL. Wraz z notacji pakietu VSIX zawiera narzędzia, które użytkownicy mogą stosować ułatwiające je edytować i generować materiału z ich modeli.  
  
 Jedną z głównych aplikacji DSLs jest do generowania kodu programu, pliki konfiguracji i pozostałych artefaktów. Szczególnie w przypadku dużych projektów i linii produktów, w którym zostanie utworzona kilka wariantów produktu, generowanie wiele aspektów zmiennej DSLs zapewniają duży wzrost niezawodności i bardzo szybkie odpowiedzi na zmiany wymagań.  
  
 Pozostała część tego przeglądu jest Przewodnik wprowadzający podstawowe operacje tworzenia i użyciu języka specyficznego dla domeny w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zdefiniować DSL, należy zainstalować następujące składniki:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Modelowanie zestawu SDK dla programu Visual Studio||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-dsl-solution"></a>Tworzenie rozwiązania DSL  
 Aby utworzyć nowego języka specyficznego dla domeny, należy utworzyć nowy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania za pomocą szablonu projektu języka specyficznego dla domeny.  
  
#### <a name="to-create-a-dsl-solution"></a>Tworzenie rozwiązań DSL  
  
1.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  W obszarze **typy projektów**, rozwiń węzeł **inne typy projektów** węzeł, a następnie kliknij przycisk **rozszerzalności**.  
  
3.  Kliknij przycisk **projektanta języka specyficznego dla domeny**.  
  
     ![Okno dialogowe DSL tworzenie](../modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
4.  W **nazwa** wpisz **FamilyTree**. Kliknij przycisk **OK**.  
  
     **Kreatora języka specyficznego dla domeny** otwiera i wyświetla listę rozwiązań DSL szablonu.  
  
     Kliknij przycisk każdego szablonu, aby wyświetlić opis,  
  
     Szablony są przydatne punkty początkowe. Każde z nich zawiera pełną pracy DSL, który można edytować w zależności od potrzeb. Zazwyczaj należy wybrać szablon najbliższej ma zostać utworzony.  
  
5.  W ramach tego przewodnika, wybierz **minimalnego języka** szablonu.  
  
6.  Wprowadź rozszerzenia nazwy pliku z DSL w odpowiedniej strony w kreatorze. To rozszerzenie, które pliki zawierające wystąpień programu DSL będzie używany.  
  
    -   Wybierz rozszerzenia, które nie jest skojarzony z dowolnej aplikacji w komputerze lub w dowolnym komputerze, na którym chcesz zainstalować DSL. Na przykład **docx** i **htm** będzie można zaakceptować pliku rozszerzeń nazw.  
  
    -   Kreator wyświetli ostrzeżenie, jeśli rozszerzenia plików, które zostały wprowadzone, jest on używany jako DSL. Należy rozważyć użycie różnych rozszerzenie. Można również zresetować Wyczyszczenie starych projektantów eksperymentalne wystąpienie programu Visual Studio SDK eksperymentalne. Kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, **zestawu SDK programu Microsoft Visual Studio 2010**, **narzędzia**, a następnie **zresetować firmy Microsoft Visual Studio 2010 eksperymentalne wystąpienie**.  
  
7.  Sprawdź innych stron, a następnie kliknij przycisk **Zakończ**.  
  
     Rozwiązanie jest generowany, która zawiera dwa projekty. Są one nazywane Dsl i DslPackage. Plik diagramu zostanie otwarty czyli DslDefinition.dsl nazwanego.  
  
    > [!NOTE]
    >  Większość kodu, który można zobaczyć w folderach z dwa projekty są generowane na podstawie DslDefinition.dsl. Z tego powodu większość do Twojej DSL się zmiany w tym pliku.  
  
 Interfejs użytkownika jest teraz podobny poniższej ilustracji.  
  
 ![Projektant DSL](../modeling/media/dsl_designer.png "dsl_designer")  
  
 To rozwiązanie definiuje domeny określonego języka. Aby uzyskać więcej informacji, zobacz [Przegląd interfejsu użytkownika narzędzia języka specyficznego dla domeny](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).  
  
## <a name="the-important-parts-of-the-dsl-solution"></a>Ważne części rozwiązania DSL  
 Zwróć uwagę następujące aspekty nowego rozwiązania.  
  
-   **Dsl\DslDefinition.DSL** to jest plik zostanie wyświetlony po utworzeniu rozwiązania DSL. Prawie wszystkie kodu w rozwiązaniu jest generowany na podstawie tego pliku, a większość wprowadzane do definicji DSL zmiany zostały wprowadzone w tym miejscu. Aby uzyskać więcej informacji, zapoznaj się z praca [Praca z diagramu definicji DSL](../modeling/working-with-the-dsl-definition-diagram.md).  
  
-   **Projekt DSL** ten projekt zawiera kod, który definiuje język specyficznego dla domeny.  
  
-   **Projekt DslPackage** ten projekt zawiera kod, który umożliwia wystąpień DSL otwarty i edytowany w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
##  <a name="Debugging"></a>Uruchomiona DSL  
 Rozwiązanie DSL można uruchomić natychmiast po jej utworzeniu. Później możesz zmodyfikować definicję DSL stopniowo, uruchomiony ponownie po każdej zmianie rozwiązania.  
  
#### <a name="to-experiment-with-the-dsl"></a>Aby wypróbować DSL  
  
1.  Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań. Większość kodu źródłowego z DslDefinition.dsl to generuje.  
  
    > [!NOTE]
    >  Przy każdej zmianie DslDefinition.dsl, należy kliknąć opcję **Przekształć wszystkie szablony** przed możesz ponownie skompiluj rozwiązanie. Ten krok można zautomatyzować. Aby uzyskać więcej informacji, zobacz [jak zautomatyzować Przekształć wszystkie szablony](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
2.  Naciśnij klawisz F5, lub na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
     DSL kompilacje i jest zainstalowany w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uruchamia. Eksperymentalne wystąpienie trwa jego ustawienia z oddzielnych poddrzewo rejestru, których [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia są zarejestrowane na potrzeby debugowania. Normalne wystąpienia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie mają dostępu do zarejestrowanego rozszerzeń.  
  
3.  W eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], otwórz plik modelu o nazwie **testu** z **Eksploratora rozwiązań**.  
  
     \-lub -  
  
     Kliknij prawym przyciskiem myszy projekt debugowanie, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **elementu**. W **Dodaj element** okno dialogowe, wybierz typ pliku z DSL.  
  
     Otwiera plik modelu jako pusty diagram.  
  
     Przybornika otwiera i wyświetla narzędzia odpowiedni typ diagramu.  
  
4.  Narzędzia do tworzenia łączników i kształtów na diagramie.  
  
    1.  Aby utworzyć kształtów, przeciągnij z narzędzia przykład kształt na diagramie.  
  
    2.  Aby połączyć dwie kształty, kliknij przykład łącznik, kliknij pierwszy kształt, a następnie kliknij drugiego kształtu.  
  
5.  Kliknij pozycję etykiety kształty, aby je zmienić.  
  
 Twoje eksperymentalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] będzie wyglądać następująco:  
  
 ![](../modeling/media/dsl_min.png "DSL_min")  
  
### <a name="the-content-of-a-model"></a>Zawartość modelu  
 Zawartość pliku, który jest wystąpieniem DSL jest nazywany *modelu*. Model zawiera *modelu**elementy* i *łącza* między elementami. Określa, jakie typy elementów modelu definicji DSL i powiązań w modelu. Na przykład w DSL, utworzone na podstawie szablonu języka minimalne, ma jeden typ elementu modelu i jednego typu łącza.  
  
 Definicja DSL można określić sposób wyświetlania modelu na diagramie. Możesz z różnych stylów kształtów i łączników. Można określić, że niektóre kształty wystąpić wewnątrz innych kształtów.  
  
 Można wyświetlać modelu w drzewie **Explorer** wyświetlić podczas edytowania modelu. Podczas dodawania kształtów na diagramie, elementy modelu jest również dostępna w Eksploratorze. Można Eksploratora, nawet jeśli dostępny jest brak diagramu.  
  
 Nie widać Eksploratora w wystąpieniu debugowania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]na **widoku** menu wskaż **inne okna**, a następnie kliknij przycisk  *\<swój język >* **Explorer**.  
  
### <a name="the-api-of-your-dsl"></a>Funkcji API z DSL  
 Twoje DSL generuje interfejs API, który umożliwia odczytywanie i aktualizowanie modeli, które są wystąpieniami klasy DSL. Jednej aplikacji interfejsu API polega na generowaniu pliki tekstowe z modelu. Aby uzyskać więcej informacji, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 W rozwiązaniu debugowanie Otwórz pliki szablonów z rozszerzeniem ".TT —". Te przykłady pokazują, jak można wygenerować tekstu z modeli i umożliwiają testu z interfejsu API programu DSL. Jedną z próbek są zapisywane [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], inne w [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
 Na podstawie każdego szablonu plik jest plikiem, który generuje. Rozwiń plik szablonu w Eksploratorze rozwiązań, a następnie otwórz wygenerowany plik.  
  
 Plik szablonu zawiera krótki segment kodu, który zawiera listę wszystkich elementów w modelu.  
  
 Wygenerowany plik zawiera wynik.  
  
 Jeśli zmienisz plik modelu, zobaczysz odpowiednie zmiany w wygenerowanych plików po ponownym wygenerowaniu pliki.  
  
##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Można ponownie wygenerować pliki tekstowe po zmodyfikowaniu pliku modelu  
  
1.  W eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Zapisz plik modelu.  
  
2.  Upewnij się, że parametr nazwy pliku w każdym pliku .TT — odwołuje się do pliku modelu używanego do eksperymentów. Zapisz plik .TT —.  
  
3.  Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi **Eksploratora rozwiązań**.  
  
     \-lub -  
  
     Kliknij prawym przyciskiem myszy szablony, które chcesz ponownie wygenerować, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.  
  
 Można dodać dowolną liczbę plików tekstowych szablonu do projektu. Każdy szablon generuje jednego pliku wyników.  
  
> [!NOTE]
>  Po zmianie definicji DSL przykładowy kod szablonu tekstu nie będzie działać, chyba że go zaktualizować.  
  
 Aby uzyskać więcej informacji, zobacz [generowania kodu języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md) i [pisanie kodu, aby dostosować języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
## <a name="customizing-the-dsl"></a>Dostosowywanie DSL  
 Jeśli chcesz zmodyfikować definicję DSL, zamknij eksperymentalne wystąpienie i aktualizacji definicji w głównym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wystąpienia.  
  
> [!NOTE]
>  Po zmodyfikowaniu definicji DSL, może spowodować utratę informacji w modelach testu, które zostały utworzone za pomocą wcześniejszych wersji.  Na przykład debugowania rozwiązania zawiera plik o nazwie próbki, który zawiera niektóre kształty i łączniki. Po rozpoczęciu tworzenia definicję DSL, nie będą widoczne, a zostaną one utracone podczas zapisywania pliku.  
  
 Możesz wprowadzić szereg rozszerzeń do Twojej DSL. W poniższych przykładach przedstawiono wrażenie możliwości.  
  
 Po każdej zmianie zapisać definicji DSL, kliknij przycisk **Przekształć wszystkie szablony** w **Eksploratora rozwiązań**, a następnie naciśnij klawisz **F5** eksperymentować DSL zmienione.  
  
### <a name="rename-the-types-and-tools"></a>Zmień nazwę typu i narzędzia  
 Zmień nazwę istniejącej klasy i relacje. Na przykład zaczynając od definicji Dsl utworzone na podstawie szablonu minimalnego języka, możesz można wykonać następujące operacje zmiany nazwy, aby DSL reprezentują drzewa rodziny.  
  
##### <a name="to-rename-domain-classes-relationships-and-tools"></a>Aby zmienić nazwę klasy, relacje i narzędzia  
  
1.  Na diagramie DslDefinition zmienić **ExampleModel** do **FamilyTreeModel**, **ExampleElement** do **osoby**,  **Obiekty docelowe** do **nadrzędnych**, i **źródeł** do **dzieci**. Możesz kliknąć każda etykieta je zmienić.  
  
     ![Diagram definicji DSL &#45; model drzewa rodziny](../modeling/media/familyt_person.png "FamilyT_Person")  
  
2.  Zmień nazwę elementu i łącznik narzędzia.  
  
    1.  Otwórz okno Eksploratora DSL, klikając kartę w Eksploratorze rozwiązań. Jeśli nie widzisz, na **widoku** menu wskaż **inne okna** , a następnie kliknij przycisk **DSL Explorer**. Eksplorator DSL jest widoczny tylko wtedy, gdy aktywne okno na diagramie definicji DSL.  
  
    2.  Otwórz okno właściwości i umieść go, tak aby były widoczne Eksploratora DSL i właściwości, które znajdują się w tym samym czasie.  
  
    3.  W Eksploratorze DSL rozwiń **edytor**, **kart z przybornika**,  *\<Twojego DSL >*, a następnie **narzędzia**.  
  
    4.  Kliknij przycisk **ExampleElement**. Jest to element przybornika, który służy do tworzenia elementów.  
  
    5.  W oknie Właściwości zmień **nazwa** właściwości **osoby**.  
  
         Zwróć uwagę, że **podpis** również zmiany właściwości.  
  
    6.  W ten sam sposób, Zmień nazwę **ExampleConnector** narzędzia, aby **ParentLink**. Instrukcja ALTER **podpis** właściwości, że nie jest kopię właściwość Name. Na przykład wprowadź **łącza nadrzędnego**.  
  
3.  Odbuduj DSL.  
  
    1.  Zapisz plik definicji DSL.  
  
    2.  Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań  
  
    3.  Naciśnij F5. Poczekaj na wystąpienie eksperymentalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pojawi się.  
  
4.  W rozwiązaniu debugowanie w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], otwórz plik modelu testu. Przeciągnij elementy go z przybornika. Należy zauważyć, że zmieniono podpisy narzędzia i nazwy typów w Eksploratorze DSL.  
  
5.  Zapisz plik modelu.  
  
6.  Otwórz plik .TT — i Zastąp wystąpienia stare nazwy typu i właściwości nowej nazwy.  
  
7.  Upewnij się, że nazwa pliku, która została określona w pliku .TT — określa modelu testu.  
  
8.  Zapisz plik .TT —. Otwórz wygenerowany plik, aby zobaczyć wynik uruchomienia kod w pliku .TT —. Sprawdź, czy jest poprawna.  
  
### <a name="add-domain-properties-to-classes"></a>Dodaj właściwości domeny do klas  
 Dodaj właściwości do klasy domeny, na przykład w celu reprezentowania lat urodzenia i śmierci osoby.  
  
 Aby wyświetlić właściwości nowej na diagramie, należy dodać *dekoratory* kształtu, która wyświetla elementu modelu. Właściwości musi być również mapować do elementów decorator.  
  
##### <a name="to-add-properties-and-display-them"></a>Aby dodać właściwości i wyświetlić je  
  
1.  Dodaj właściwości.  
  
    1.  Na diagramie definicji DSL, kliknij prawym przyciskiem myszy **osoby** klasy domeny, wskaż **Dodaj**, a następnie kliknij przycisk **właściwości domeny**.  
  
    2.  Wpisz listę nowych nazw właściwości, takie jak **urodzenia** i **śmierci**. Naciśnij klawisz **Enter** po każdej z nich.  
  
2.  Dodawanie elementów decorator, które będą wyświetlane właściwości w kształcie.  
  
    1.  Wykonaj szara linia, który rozciąga się od klasy domeny osoba po drugiej stronie diagramu. Jest to diagram elementu mapy. Klasa domeny łączy do klasy kształtu.  
  
    2.  Kliknij prawym przyciskiem myszy tę klasę kształtu, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **Dekoratora tekstu**.  
  
    3.  Dodaj dwa dekoratory o nazwach takich jak **BirthDecorator** i **DeathDecorator**.  
  
    4.  Wybierz każdego nowego dekoratora i w oknie właściwości ustaw **pozycji** pola. Określa, gdzie wartość właściwości domeny będzie wyświetlana dla kształtu. Na przykład ustawić **InnerBottomLeft** i **InnerBottomRight**.  
  
         ![Definicja kształtu przedziału](../modeling/media/familyt_compartment.png "FamilyT_Compartment")  
  
3.  Elementy decorator mapować do właściwości.  
  
    1.  Otwórz okno Szczegóły DSL. Jest zwykle na karcie obok w oknie danych wyjściowych. Jeśli nie widzisz, na **widoku** menu wskaż **inne okna**, a następnie kliknij przycisk **szczegóły DSL**.  
  
    2.  Na diagramie definicji DSL, kliknij wiersz, który łączy **osoby** klasy domeny do klasy kształtu.  
  
    3.  W **szczegóły DSL**na **mapy Dekoratora** kliknij pole wyboru na Niemapowane dekoratora. W **wyświetlania właściwości**, wybierz właściwość domeny, do której ma on zamapowany. Na przykład mapowanie **BirthDecorator** do **urodzenia**.  
  
4.  Zapisz DSL, kliknij przycisk Przekształć wszystkie szablony i naciśnij klawisz F5.  
  
5.  W przykładowy diagram modelu Sprawdź, czy można teraz kliknij pozycje, którą wybrano i wpisz wartości do nich. Ponadto po wybraniu **osoby** kształtu, w oknie właściwości są wyświetlane nowe właściwości urodzenia i śmierci.  
  
6.  W pliku .TT — można dodać kod, który uzyskuje właściwości każdej osoby.  
  
 ![Diagram drzewa rodziny, przybornika i explorer](../modeling/media/familyt_instance.png "FamilyT_Instance")  
  
### <a name="define-new-classes"></a>Definiowanie nowych klas  
 Można dodać klasy i relacje do modelu. Na przykład można utworzyć nowej klasy reprezentujące miastach i nowej relacji do reprezentowania, że osoba żyła w mieście.  
  
 Aby różne typy distinct na diagramie modelu, możesz mapować klasy domeny do różnych rodzajów kształtu lub kształty z inną geometrię i kolory.  
  
##### <a name="to-add-and-display-a-new-domain-class"></a>Aby dodać i wyświetlić nową klasę domeny  
  
1.  Dodaj klasę domeny i była elementem podrzędnym elementu głównego.  
  
    1.  Na diagramie definicji DSL kliknij **relacja osadzania** narzędzia, kliknij przycisk klasy głównym **FamilyTreeModel**, a następnie kliknij pozycję pustą część diagramu.  
  
         Nowe klasy domeny zostanie wyświetlony połączoną z FamilyTreeModel z relacja osadzania.  
  
         Ustaw jego nazwę, na przykład **miejscowość**.  
  
        > [!NOTE]
        >  Każda klasa domeny, z wyjątkiem katalogu głównego modelu musi być elementem docelowym co najmniej jedna relacja osadzania lub musi dziedziczyć z klasy, która jest elementem docelowym osadzenia. Z tego powodu jest często wygodne utworzyć klasę domeny przy użyciu narzędzia relacja osadzania.  
  
    2.  Na przykład dodać właściwość domeny w nowej klasie **nazwa**.  
  
2.  Dodawanie relacji między i miasta osoby.  
  
    1.  Kliknij przycisk **relacji** narzędzia, kliknij przycisk osoby, a następnie kliknij przycisk miasta.  
  
         ![Fragment definicji DSL: katalogu głównego drzewa rodziny](../modeling/media/familyt_root.png "FamilyT_Root")  
  
        > [!NOTE]
        >  Relacje odwołania reprezentują odsyłacze z jednej części drzewa modelu do innego.  
  
3.  Dodanie kształtu do reprezentowania miastach na diagramach modelu.  
  
    1.  Przeciągnij **geometrii kształtu** z przybornika do diagramu i jego nazwa zostanie zmieniona, na przykład **TownShape**.  
  
    2.  W oknie właściwości ustaw wygląd pola nowy kształt, takie jak kolor wypełnienia i geometrii.  
  
    3.  Dodaj Dekoratora, aby wyświetlić nazwę miasta i zmień jego nazwę na NameDecorator. Ustaw dla właściwości pozycji.  
  
4.  Klasa domeny miejscowość są mapowane na TownShape.  
  
    1.  Kliknij przycisk **mapy Element diagramu** narzędzia, a następnie kliknij miejscowość klasy domeny, a następnie TownShape klasy kształtu.  
  
    2.  W **mapy Dekoratora** karcie **szczegóły DSL** wybrane okno z łącznikiem mapy, sprawdź NameDecorator i ustaw **wyświetlania właściwości** do nazwy.  
  
5.  Utwórz łącznik do wyświetlenia relacji między osoby i miast.  
  
    1.  Przeciągnij łącznika z przybornika do diagramu. Zmień nazwę i ustawienia swoich właściwości wyglądu.  
  
    2.  Użyj **mapy Element diagramu** narzędzia, aby połączyć nowego łącznika do relacji między i miasta osoby.  
  
         ![Definicja drzewa rodziny z mapy dodano kształt](../modeling/media/familyt_shapemap.png "FamilyT_ShapeMap")  
  
6.  Utwórz element narzędzia do tworzenia nowych miast.  
  
    1.  W **DSL Explorer**, rozwiń węzeł **edytor** następnie **kart z przybornika**.  
  
    2.  Kliknij prawym przyciskiem myszy  *\<Twojego DSL >* , a następnie kliknij przycisk **Dodaj nowe narzędzie elementu**.  
  
    3.  Ustaw **nazwa** właściwość nowe narzędzia i zestaw jej **klasy** właściwości miasta.  
  
    4.  Ustaw **ikonę przybornika** właściwości. Kliknij przycisk **[...]**  i **nazwę pliku** wybierz plik ikony.  
  
7.  Utwórz łącznik narzędzie do tworzenia łącza między miastach i osoby.  
  
    1.  Kliknij prawym przyciskiem myszy  *\<Twojego DSL >* , a następnie kliknij przycisk **Dodaj nowy łącznik**.  
  
    2.  Ustaw właściwość Nazwa nowego narzędzia.  
  
    3.  W **ConnectionBuilder** właściwości, wybierz konstruktora, który zawiera nazwę relacji miasta osoby.  
  
    4.  Ustaw **ikonę przybornika**.  
  
8.  Kliknij pozycję Zapisz definicję DSL **Przekształć wszystkie szablony**, a następnie naciśnij klawisz **F5**.  
  
9. W eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], otwórz plik modelu testu. Użycie nowych narzędzi do tworzenia miastach i linki między miastach i osoby. Należy zauważyć, że można tworzyć tylko łącza między poprawne typy elementu.  
  
10. Tworzenie kodu, która zawiera miejscowości, w którym mieszka każda osoba. Szablony tekstowe są jednym z miejsc, w którym można uruchomić taki kod. Na przykład można zmodyfikować istniejący plik Sample.tt w rozwiązaniu debugowanie tak, aby zawierał następujący kod:  
  
    ```  
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>  
    <#@ output extension=".txt" #>  
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>  
  
    <#  
      foreach (Person person in this.FamilyTreeModel.People)  
      {  
    #>  
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>  
  
    <#  
          foreach (Person child in person.Children)  
      {  
    #>  
                <#= child.Name #>  
    <#  
      }  
      }  
    #>  
  
    ```  
  
     Podczas zapisywania pliku *.tt utworzy przedstawicielstwach plik, który zawiera listę użytkowników i ich miejsc zamieszkania. Aby uzyskać więcej informacji, zobacz [generowania kodu języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="validation-and-commands"></a>Sprawdzanie poprawności i poleceń  
 Ten DSL dalsze można utworzyć przez dodanie ograniczenia sprawdzania poprawności. Te ograniczenia są metody, które można określić, które upewnij się, że model jest w odpowiednim stanie. Na przykład można zdefiniować ograniczenie, aby upewnić się, że datę urodzenia dziecka jest nowsza niż nadrzędnych. Funkcja weryfikacji wyświetli ostrzeżenie, jeśli użytkownik DSL próbuje zapisać modelu, który dzieli żadne ograniczenia. Aby uzyskać więcej informacji, zobacz [sprawdzania poprawności języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).  
  
 Można również zdefiniować poleceń menu, które może wywołać użytkownik. Polecenia można modyfikować modelu. Mogą również współpracować innych modeli w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i z zasobów zewnętrznych. Aby uzyskać więcej informacji, zobacz [porady: modyfikowanie standardowe polecenia Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="deploying-the-dsl"></a>Wdrażanie DSL  
 Aby zezwolić innym użytkownikom korzystanie z języka specyficznego dla domeny, dystrybucji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pliku rozszerzenia (VSIX). To jest tworzony podczas kompilowania rozwiązania DSL.  
  
 Zlokalizuj plik .vsix w folder bin rozwiązania. Skopiuj go na komputerze, na którym chcesz go zainstalować. Na tym komputerze kliknij dwukrotnie plik VSIX. DSL można używać we wszystkich wystąpieniach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na tym komputerze.  
  
 Tę samą procedurę służy do zainstalowania na własnym komputerze DSL, dzięki czemu nie trzeba używać eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań języka specyficznego dla domeny](../modeling/deploying-domain-specific-language-solutions.md).  
  
##  <a name="Reset"></a>Usuwanie starego DSLs eksperymentalne  
 Jeśli zostały utworzone eksperymentalne DSLs nie są już potrzebne, Usuń z komputera poprzez zresetowanie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eksperymentalne wystąpienie.  
  
 Spowoduje to usunięcie z komputera wszystkie DSLs eksperymentalne i inne eksperymentalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia. Są to rozszerzeń, które zostały wykonane w trybie debugowania.  
  
 Ta procedura nie powoduje usunięcia DSLs lub inne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzeń, które zostały w pełni zainstalowane, wykonując pliku VSIX.  
  
#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Aby zresetować programu Visual Studio eksperymentalne wystąpienie programu  
  
1.  Kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, **zestawu SDK programu Microsoft Visual Studio 2010**, **narzędzia**, a następnie **zresetować firmy Microsoft Visual Studio 2010 eksperymentalne wystąpienie**.  
  
2.  Odbuduj żadnych eksperymentalne DSLs lub inne eksperymentalne [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzeń, które chcesz użyć.  
  
## <a name="see-also"></a>Zobacz też  
 [Opis modeli, klasy i relacje](../modeling/understanding-models-classes-and-relationships.md)   
 [Sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)   

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

