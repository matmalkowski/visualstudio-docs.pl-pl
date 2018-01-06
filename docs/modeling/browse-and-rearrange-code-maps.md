---
title: "Przeglądanie i rozmieszczanie map kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
ms.assetid: 08f65f77-6ca7-4b25-b060-3f6c9f5847a4
caps.latest.revision: "91"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: 2870f057f34299a41dcb090f97bb13316cb28387
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="browse-and-rearrange-code-maps"></a>Przeglądanie i rozmieszczanie map kodu
Zmień kolejność elementów na mapy kodu, aby łatwiej odczytywać i zwiększyć ich wydajność.  
  
 Mapy kodu można dostosować, bez wywierania wpływu na kod źródłowy w rozwiązaniu. Jest to przydatne, gdy chcesz skupić się na elementy kodu klucza lub komunikacji pomysły dotyczące kodu. Na przykład aby wyróżnić interesujące obszary, możesz można wybierz elementy kodu na mapie i ich filtrowania, Zmień styl elementy kodu i linki ukryć lub usunąć elementy kodu i organizowanie elementów kodu za pomocą właściwości, kategorii lub grup.  
  
 **Wymagania**  
  
-   Aby utworzyć mapy kodu, musi mieć Visual Studio Enterprise.  
  
-   Można wyświetlić mapy kodu i dokonaj edycji ograniczone do mapy kodu w programie Visual Studio Professional.  
  
##  <a name="ManageLargeGraphs"></a>Rozpocząć pracę z usługą mapy kodu  
 Utwórz mapę kodu (zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md) więcej szczegółów). Jeśli nie chcesz czekać na mapie, aby zakończyć generowania, kliknij przycisk **anulować** link w dowolnym momencie, aby zatrzymać proces generowania. Jednak możesz nie będą widzieć szczegóły wszystkie zależności i linki w takim przypadku.  
  
 Po wygenerowaniu mapy wprowadzenie porady dotyczące przeglądania kodu:  
  
-   Spójrz na klastry fizyczne zależności w kodzie. Na pasku narzędzi mapy wybierz **układu**, **szybkie klastry**![przycisk szybkie klastry na pasku narzędzi wykresu](../modeling/media/quickclustersicon.gif "QuickClustersIcon"). Zobacz [zmiany układu mapy](#Selecting).  
  
     ![Wykres zależności &#45; Szybki układ klastrów](../modeling/media/dependencygraph_quickclusters.png "DependencyGraph_QuickClusters")  
  
-   Organizowanie mapy na mniejsze obszary przez grupowanie powiązanych węzłów. Zwinąć te grupy, aby wyświetlić tylko intergroup zależności, które są automatycznie wyświetlane. Zobacz [węzły grup](#OrganizeGroups).  
  
-   Używać filtrów w celu uproszczenia mapy i skoncentrować się na typy węzłów lub połączeń, które planuje się. Zobacz [filtrować węzły i linki](#FilterNodes).  
  
-   Zmaksymalizować wydajność dużych map. Zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md) Aby uzyskać więcej informacji. Na przykład włączyć **pominięcia kompilacji** na pasku narzędzi mapy, tak że Visual Studio nie odbudować rozwiązania podczas aktualizacji elementów na mapie.  
  
##  <a name="Selecting"></a>Zmian układu mapy  
  
|**Aby**|**Wykonaj te kroki**|  
|------------|-----------------------------|  
|Rozmieść przepływu zależności dla całej mapy w określonym kierunku. Może to pomóc w Zobacz warstwy architektury w kodzie.|Na pasku narzędzi mapy wybierz **układu**, a następnie:<br /><br /> -   **Z góry na dół** ![góry do dołu przycisku Wykres](../modeling/media/topbottomgraphbutton.gif "TopBottomGraphButton")<br />-   **Dołu do góry** ![dolnej do górnej wykres przycisku](../modeling/media/bottomtopgraphbutton.gif "BottomTopGraphButton")<br />-   **Od lewej do prawej** ![od lewej do układu prawy przycisk](../modeling/media/leftrightgraphbutton.gif "LeftRightGraphButton")<br />-   **Od prawej do lewej** ![prawo do przycisku po lewej stronie wykres](../modeling/media/rightleftgraphbutton.gif "RightLeftGraphButton")|  
|Zobacz klastry fizyczne zależności w kodzie z najbardziej zależnych węzłów w Centrum klastrów i najmniej zależnych węzłów na zewnątrz tych klastrach.|Na pasku narzędzi mapy wybierz **układu**, a następnie **szybkie klastry**![przycisk szybkie klastry na pasku narzędzi wykresu](../modeling/media/quickclustersicon.gif "QuickClustersIcon").|  
|Wybierz co najmniej jeden węzeł na mapie.|Kliknij węzeł, aby go wybrać. Wybierz lub Anuluj wybór więcej niż jeden węzeł, przytrzymaj **CTRL** podczas klikania.<br /><br /> Skróty: naciśnij **kartę** lub użyj klawiszy strzałek, aby przenieść prostokąt fokusu kropkowanej węzła i naciśnij klawisz **miejsca** aby go wybrać. Naciśnij klawisz **CTRL** + **miejsca** do wielokrotnego wyboru lub Anuluj wybór węzłów.|  
|Poruszanie określonych węzłów na mapie.|Przeciągnij węzły, aby przenieść je. Aby przenieść inne węzły i łącza do końca przeciągania węzłów, naciśnij i przytrzymaj klawisz **SHIFT** klucza.<br /><br /> Klawiatury: przytrzymaj **CTRL** i użyj klawiszy strzałek.|  
|Zmian układu wewnątrz grupy niezależnie od innych węzłów i grup na mapie.|Wybierz węzeł i otwórz menu skrótów. Wybierz **układu** i wybierz styl układu.<br /><br /> - lub -<br /><br /> Wybierz węzeł i rozwiń go do wyświetlenia podrzędnych węzłów. Kliknij tytuł węzła, aby pokazać grupę podręcznym pasku narzędzi, a następnie otwórz **Zmień styl układu grupy**![wykresu zależności &#45;narzędzi grupy &#45; układu](../modeling/media/dependencygraph_grouptoolbar.gif "DependencyGraph_ GroupToolbar") listy. Wybierz jeden z układów drzewa **szybkie klastry**, lub **widok listy** (który rozmieszcza zawartość grupy na liście).<br /><br /> Zobacz [węzły grup](#OrganizeGroups) więcej szczegółów.|  
|Cofnięcie akcji w planie.|Naciśnij klawisz **CTRL** + **Z** lub użyć programu Visual Studio **Cofnij** polecenia.|  
  
##  <a name="Explore"></a>Przeglądaj mapy  
  
|**Aby**|**Wykonaj te kroki**|  
|------------|-----------------------------|  
|Skanowanie mapy.|Przeciągnij mapy w dowolnym kierunku za pomocą myszy.<br /><br /> - lub -<br /><br /> Przytrzymaj **SHIFT** i obracania kółko myszy, aby przewijać w poziomie. Przytrzymaj **SHIFT** + **CTRL** i obracania kółko myszy, aby przewijać w poziomie.|  
|Powiększanie lub pomniejszanie mapy.|Obróć koło myszy.<br /><br /> - lub -<br /><br /> Użyj **powiększenie** listy rozwijanej na pasku narzędzi mapy kodu.<br /><br /> - lub -<br /><br /> Używanie skrótów klawiaturowych. Aby powiększyć, naciśnij klawisz **klawisze CTRL + SHIFT +.** (okres). Aby zmniejszyć, naciśnij klawisz **klawisze CTRL + SHIFT +,** (przecinek).|  
|Powiększ określonego obszaru za pomocą myszy.|Prowadzenie prawym przyciskiem myszy podczas rysowania prostokąta wokół tego obszaru, w których planuje się.|  
|Zmienianie rozmiaru i dopasowania mapy w jego oknie.|Wybierz **Dopasuj widok do rozmiaru** z **powiększenie** listy na pasku narzędzi mapy kodu.<br /><br /> - lub -<br /><br /> Kliknij przycisk **Dopasuj do** ikona ![powiększenia ikonę na pasku narzędzi mapy](../modeling/media/almcodemapzoomicon.png "ALMCodeMapZoomIcon") na pasku narzędzi mapy kodu. Skróty: naciśnij **CTRL + 0** (zero).|  
|Znajdź węzeł na mapie, według jego nazwy. **Porada:** ta dotyczy tylko elementów na mapie. Aby znaleźć elementy rozwiązania, ale nie na mapie, je znaleźć w **Eksploratora rozwiązań**, a następnie przeciągnij je do mapy. (Przeciągnij zaznaczenie lub kliknij na pasku narzędzi Eksplorator rozwiązań **pokazywanie w mapie kodu**).|1.  Wybierz **znaleźć** ikona ![Znajdź ikonę na pasku narzędzi mapy](../modeling/media/almcodemapfindicon.png "ALMCodeMapFindIcon") na pasku narzędzi mapy kodu (klawiatury: naciśnij **CTRL + F**) do wyświetlenia pole wyszukiwania w prawym górnym rogu mapy.<br />2.  Wpisz nazwę elementu i naciśnij klawisz **zwracać** lub kliknij ikonę "Lupa". Pierwszy element, który odpowiada wyszukiwania widoczny jako zaznaczony na mapie.<br />3.  Aby dostosować wyszukiwanie, otwarcie listy rozwijanej i wybierz opcję wyszukiwania. Dostępne są następujące opcje **Znajdź następny**, **Znajdź poprzednie**, i **Zaznacz wszystko**. Następnie kliknij odpowiedni przycisk Dalej, aby polu tekstowym wyszukiwania.<br />     ![Wyszukaj upuszczania Opcje &#45; w dół listy](../modeling/media/almcodemapssearchdropdown.png "ALMCodeMapsSearchDropDown")<br />     Można również użyć klawiatury: naciśnij **F3** wybierz następny węzeł pasującego lub **SHIFT + F3** do wyboru węzła poprzedniego dopasowania.<br />4.  Wybierz jeden z opcji, które określają sposób obsługi terminy wyszukiwania, klikając ikony poniżej pola tekstowego wyszukiwania.<br />     ![Opcje dopasowania wyszukiwania](../modeling/media/almcodemapssearchmatchicons.png "ALMCodeMapsSearchMatchIcons")<br />     Dostępne są następujące opcje, od lewej do prawej strony, wielkość liter dopasowanie poufnych zgodny tylko całe wyrazy, użyj składni wyrażeń regularnych programu .NET, automatycznie rozwiń węzeł grupy w celu wyświetlania dopasowań do zamkniętych elementów. **Ważne:** można użyć pola wyszukiwania można znaleźć dopasowania w zwinięte grupy tylko wtedy, gdy te grupy zostały wcześniej powiększone. Aby znaleźć te dopasowania i automatycznie rozwijać ich grupy nadrzędnej, wybierz tę opcję w polu wyszukiwania.|  
|Zaznacz wszystkie węzły niezaznaczone.|Otwórz menu skrótów dla wybranych węzłów. Wybierz **wybierz**, **Odwróć zaznaczenie**.|  
|Wybierz dodatkowe węzły, które łącze do zaznaczonych.|Otwórz menu skrótów dla wybranych węzłów. Wybierz **wybierz** i jeden z nich:<br /><br /> -Aby wybrać dodatkowe węzły, które łączą się bezpośrednio do wybranego węzła, wybierz **przychodzące zależności**.<br />-Aby wybrać dodatkowe węzły połączone bezpośrednio z wybranego węzła, wybierz **wychodzących zależności**.<br />-Aby wybrać dodatkowe węzły połączone bezpośrednio do i z wybranego węzła, wybierz **zarówno**.<br />-Aby wybrać wszystkie węzły, które łączy do i z zaznaczonego węzła, wybierz **połączone Subgraph**.<br />-Aby wybrać wszystkie elementy podrzędne wybranego węzła, wybierz **dzieci**.|  
  
##  <a name="FilterNodes"></a>Filtr węzły i łącza  
  
|**Aby**|**Wykonaj te kroki**|  
|------------|-----------------------------|  
|Pokazywanie lub ukrywanie okienka filtrów.|Wybierz **filtry** przycisk na pasku narzędzi mapy kodu. W okienku filtrów jest domyślnie wyświetlany jako stronę karty w oknie Eksploratora rozwiązań.|  
|Filtr typy węzłów, które są wyświetlane na mapie.|Ustaw lub usuń zaznaczenie pola wyboru w **elementy kodu** na liście w okienku filtrów.|  
|Filtrowania typów łączy, które są wyświetlane na mapie.|Ustaw lub usuń zaznaczenie pola wyboru w **relacje** na liście w okienku filtrów.|  
|Pokaż lub Ukryj węzły projektu testowego na mapie.|Ustawianie lub czyszczenie **zasoby testu** checkbox w **różne** na liście w okienku filtrów.|  
  
 Ikony wyświetlane w panelu legendy mapy odzwierciedlają ustawienia wprowadzone na liście. Aby wyświetlić lub ukryć panel legendy, kliknij przycisk **legendy** przycisk na pasku narzędzi mapy kodu.  
  
##  <a name="Inspect"></a>Sprawdź, czy węzły i łącza  
 Mapy kodu Pokaż tego łącza:  
  
-   Łącze poszczególnych reprezentuje jednej relacji między dwoma węzłami.  
  
-   Łącza współzależności grup reprezentuje relację między dwoma węzłami w różnych grupach.  
  
-   Łącze zagregowane reprezentuje wszystkie relacje, które wskazują w tym samym kierunku między dwiema grupami.  
  
> [!TIP]
>  Domyślnie mapy zawiera linki międzygrupowe tylko do wybranych węzłów. Aby zmienić to zachowanie, aby pokazać lub ukryć zagregowane łącza między grupami, kliknij przycisk **układu** kod mapy paska narzędzi i wybierz polecenie **zaawansowane**, następnie **Pokaż wszystkie linki Międzygrupowe** lub **Ukryj wszystkie linki Międzygrupowe**. Zobacz [Ukryj lub Pokaż węzły i linki](#HidingShowing) więcej szczegółów.  
  
|**Aby**|**Wykonaj te kroki**|  
|------------|-----------------------------|  
|Zobacz więcej informacji na temat węzeł lub połączenie.|Umieść kursor myszy na węźle lub łącze do czasu jest wyświetlany w etykietce narzędzia.<br /><br /> Etykietka narzędzia dla zagregowane łącze zawiera indywidualne zależności, które reprezentuje.<br /><br /> - lub -<br /><br /> Otwórz menu skrótów węzła lub łącze. Wybierz **Edytuj**, **właściwości**.|  
|Pokaż lub Ukryj zawartość grupy.|-Aby rozwinąć grupę, otwórz menu skrótów węzła i wybierz polecenie **grupy**, **rozwiń**.<br />     - lub -<br />     Przesuń wskaźnik myszy na węźle, aż pojawi się przycisk cudzysłów ostrokątny (strzałkę). Kliknij ten przycisk, aby rozwinąć grupę. Klawiatury: Aby rozwinąć lub zwinąć wybraną grupę, naciśnij klawisz **PLUS** klucza (**+**) lub **MINUS** klucza ( **-** ).<br />-Aby zwinąć grupę, otwórz menu skrótów węzła i wybierz polecenie **grupy**, **Zwiń**.<br />     - lub -<br />     Umieść kursor myszy na grupę, aż pojawi się przycisk cudzysłów ostrokątny (Strzałka w górę). Kliknij ten przycisk, aby zwinąć grupie.<br />-Aby rozszerzyć wszystkich grup, naciśnij klawisz **CTRL** + **A** zaznacz wszystkie węzły. Otwórz menu skrótów mapy i wybierz polecenie **grupy**, **rozwiń**. **Uwaga:** to polecenie nie jest dostępne w przypadku rozszerzania wszystkich grup generuje bezużyteczne mapy lub problemy z pamięcią. Zalecane jest, rozwiń węzeł mapy tylko do poziomu szczegółowości, które są dla Ciebie ważne.<br />-Aby należy Zwiń wszystkie grupy, otwórz menu skrótów węzła lub mapy. Wybierz **grupy**, **Zwiń wszystkie**.|  
|Patrz definicja kodu dla przestrzeni nazw, typu lub elementu członkowskiego.|Otwórz menu skrótów węzła i wybierz polecenie **przejdź do definicji**.<br /><br /> —lub—<br /><br /> Kliknij dwukrotnie węzeł. Dla grup rozwinięty kliknij dwukrotnie nagłówka w grupie.<br /><br /> —lub—<br /><br /> Wybierz węzeł i naciśnij klawisz **F12**.<br /><br /> Na przykład:<br /><br /> — Dla przestrzeni nazw zawierających jedną klasę pliku kodu dla klasy otwiera Pokaż definicji klas. W pozostałych przypadkach **wyniki Znajdź Symbol** okno Lista plików kodu. **Uwaga:** podczas wykonywania tego zadania w Visual Basic .NET przestrzeni nazw, nie powoduje otwarcia pliku kodu za przestrzeni nazw. Ten problem występuje również w przypadku wykonywania tego zadania w grupie wybranych węzłów, które obejmują przestrzeni nazw programu Visual Basic .NET. Aby obejść ten problem, ręcznie przejdź do pliku kodu za przestrzeni nazw lub pominąć węzła dla przestrzeni nazw z zaznaczenia.<br />— Dla klasy lub klasy częściowej pliku kodu dla tej klasy otwiera Pokaż definicji klasy.<br />— W przypadku metody plik kodowy dla klasy nadrzędnej otwiera Pokaż definicję metody.|  
|Sprawdź, czy zależności i elementy, które uczestniczą w łącznych danych łączy.|Wybierz interesuje i otwórz menu skrótów dla wybranego łącza. Wybierz **Pokaż linki** lub **Pokaż linki na nowej mapie kodu**.<br /><br /> Program Visual Studio rozwija grupy na obu końcach połączenia i pokazuje tylko te elementy i zależności, które w nim uczestniczą. **Uwaga:** podczas badania zależności między elementami w grupach z częściowa napotkać tego zachowania: <ul><li>Linki do elementów, które nie uczestniczą w Twojej badania są usuwane z mapy, nawet jeśli te linki nadal istnieje.</li><li>Załóżmy zbadać łącze do elementu z częściowa grupy, a następnie zbadania różnych łącze do tego samego elementu. Podczas badania z drugiego częściowe Grupa docelowa zawiera tylko elementy z Twojego pierwszego badania. Łącza i elementów docelowych, które nie uczestniczyć w Twojego pierwszego badania, ale uczestniczyć w Twojej badanie nie są wyświetlane.</li></ul> Aby wyświetlić brakujące elementy z grupy, wybierz pozycję **Refetch dzieci**![Refetch ikony elementów podrzędnych](../modeling/media/dependencygraph_deletednodesicon.png "DependencyGraph_DeletedNodesIcon") (co oznacza, że nie wszystkie elementy członkowskie grupy są wyświetlane na mapie). Można też spróbować cofanie operacji (klawiatury: naciśnij **CTRL + Z**) i sprawdź, czy zależności na nowej mapie.|  
|Sprawdź, czy zależności w wielu węzłach w różnych grupach.|Rozwiń grupy, tak aby był widoczny ich elementy podrzędne. Zaznacz wszystkie węzły, które są potrzebne, łącznie z ich elementy podrzędne. Mapa pokazuje linki międzygrupowe między wybranych węzłów.<br /><br /> Aby wybrać wszystkie węzły w grupie, naciśnij i przytrzymaj klawisz **SHIFT** i lewego przycisku myszy podczas rysowania prostokątem tej grupy. Aby wybrać wszystkie węzły na mapie, naciśnij klawisz **CTRL**+**A**. **Porada:** pokazanie linki międzygrupowe przez cały czas, wybierz **układu** na pasku narzędzi mapy **zaawansowane**, **Pokaż wszystkie linki Międzygrupowe**.|  
|Zobacz elementy, które odwołuje się do węzła lub łącza.|Otwórz menu skrótów węzła i wybierz polecenie **Znajdź wszystkie odwołania**. **Uwaga:** ma to zastosowanie tylko wtedy, gdy `Reference` atrybut jest ustawiony dla węzła lub łącze w pliku .dgml mapy. Aby dodać odwołania do elementów z węzłami lub łączy, zobacz [mapy Dostosuj kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|  
  
##  <a name="HidingShowing"></a>Ukrycie lub pokazanie węzły i łącza  
 Ukrywanie węzłów wyklucza je z udziału w układzie algorytmów. Domyślnie łącza między grupami są ukryte. Łącza grupy współzależności są poszczególnymi łączami połączenia między grupami węzłów. Jeśli są zwinięte grupy, mapy agreguje wszystkie linki międzygrupowe do jednego łącza między grupami. Gdyby rozwinąć grupę i wybrać węzły wewnątrz grupy, łącza grupy współzależności pojawiają się i pokażą zależności w tej grupie.  
  
> [!CAUTION]
>  Przed udostępnieniem mapy, który został utworzony w Visual Studio Enterprise z tych, którzy korzystają z programu Visual Studio Professional, upewnij się, że odkryć wszystkie węzły lub łącza współzależności grup, które mają innym użytkownikom. W przeciwnym razie użytkownicy nie mogą odkryć tych elementów.  
  
### <a name="to-hide-or-show-nodes"></a>Aby ukryć lub pokazać węzły  
  
|**Aby**|**Wykonaj te kroki**|  
|------------|-----------------------------|  
|Ukryj wybranych węzłów.|1.  Wybierz węzły, które chcesz ukryć.<br />2.  Otwórz menu skrótów dla wybranych węzłów lub mapy. Wybierz **wybierz**, **Ukryj wybrane**.|  
|Ukryj niezaznaczone węzłów.|1.  Wybierz węzeł, który ma być widoczna.<br />2.  Otwórz menu skrótów dla wybranych węzłów lub mapy. Wybierz **wybierz**, **Ukryj niezaznaczoną**.|  
|Pokaż ukryte węzłów.|— Aby wyświetlić wszystkich węzłów w grupie, najpierw upewnij się, że jest rozwinięta w grupie. Otwórz menu skrótów i wybierz polecenie **wybierz**, **odkryć dzieci**.<br />     - lub -<br />     Kliknij przycisk **odkryć dzieci**![Pokaż ikonę elementów podrzędnych](../modeling/media/dependencygraph_filtericon_hiddennodes.gif "DependencyGraph_FilterIcon_HiddenNodes") ikonę w lewym górnym rogu (jest widoczny tylko wtedy, gdy grupy Brak węzłów podrzędnych ukryte).<br />— Aby wyświetlić wszystkich węzłów, otwórz menu skrótów dla mapy lub węzeł i wybierz polecenie **wybierz**, **Pokaż wszystkie**.|  
  
### <a name="to-hide-or-show-links"></a>Aby pokazać lub ukryć łącza  
  
|**Aby**|**Na pasku narzędzi mapy, wybierz układ, zaawansowane, a następnie wybierz pozycję**|  
|------------|----------------------------------------------------------------------|  
|Pokaż linki międzygrupowe przez cały czas.|**Pokaż wszystkie linki Międzygrupowe**. Powoduje to ukrycie agregowanych łącz między grupami.|  
|Ukryj linki międzygrupowe przez cały czas.|**Ukryj wszystkie linki Międzygrupowe**|  
|Pokaż tylko linki międzygrupowe dla zaznaczonych węzłów.|**Pokaż linki Międzygrupowe w zaznaczonych węzłach**|  
|Ukryj wszystkie linki.|**Ukryj wszystkie linki**. Aby ponownie wyświetlić łącza, wybierz jedną z opcji wymienionych powyżej.|  
  
##  <a name="OrganizeGroups"></a>Węzły grup  
  
|**Aby**|**Wykonaj te kroki**|  
|------------|-----------------------------|  
|Pokaż węzły kontenerów grupy węzłów lub węzłów liści.|Aby wyświetlić węzły kontenerów jako węzły liści: zaznacz węzły, otwórz menu skrótów dla wybranego i wybierz polecenie **grupy**, **konwersji typu liść**.<br /><br /> Aby wyświetlić węzły kontenerów jako węzły grupy: zaznacz węzły, otwórz menu skrótów dla wybranego i wybierz polecenie **grupy**, **Konwertuj do grupy**.|  
|Zmian układu w grupie.|Wybierz grupę, otwórz menu skrótów, wybierz pozycję **układu**i wybierz żądany styl układu.<br /><br /> - lub -<br /><br /> 1.  Wybierz grupę i upewnij się, że jest rozwinięte.<br />2.  Ponownie kliknij nagłówek grupy i zostanie wyświetlony pasek narzędzi grupy.<br />     ![Wykres zależności &#45; pasek narzędzi grupy](../modeling/media/dependencygraph_group.png "DependencyGraph_Group")<br />3.  Otwórz **Zmień styl układu grupy** listy ![wykresu zależności &#45;narzędzi grupy &#45; układu](../modeling/media/dependencygraph_grouptoolbar.gif "DependencyGraph_GroupToolbar") i wybieranie układu odpowiedni styl.<br /><br /> **Widok listy** Reorganizuje do listy członków grupy. **Wykres domyślny** powoduje przywrócenie grupy mapy układ domyślny. Inne opcje, zobacz [zmiany układu mapy](#Selecting).|  
|Dodaj węzeł do grupy.|Przeciągnij węzeł na grupę.<br /><br /> Podczas przeciągania węzła, Visual Studio wyświetlany wskaźnik do wyświetlenia przenosisz węzła.<br /><br /> Można również przeciągać węzły na zewnątrz grupy.|  
|Dodaj węzeł do węzła z systemem innym niż grupy.|Przeciągnij węzeł na węzeł docelowy. Możesz przekonwertować dowolnego węzła docelowego do grupy, dodając do niego węzły.|  
|Wybrane węzły grup.|1.  Zaznacz węzły, które chcesz grupować. Podręcznym pasku narzędzi pojawia się powyżej ostatniego węzła, którą wybierzesz.<br />     ![Narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")<br />2.  Na pasku narzędzi wybierz ikonę czwarty **Grupuj wybrane węzły** (Jeśli węzeł jest rozwinięty będzie miał pięć zamiast cztery ikony). Wpisz nazwę nowej grupy i naciśnij klawisz **zwracać**.<br />     - lub -<br />     Wybierz węzły, które mają być grupy i otwartej menu skrótów dla wybranego. Wybierz **grupy**, **dodać grupy nadrzędnej**, wpisz nazwę nowej grupy, a następnie naciśnij klawisz **zwracać**.<br /><br /> Można zmienić nazwę grupy. Otwórz menu skrótów dla grupy i wybierz polecenie **Edytuj**, **właściwości** otworzyć okno właściwości usługi Visual Studio. W **etykiety** właściwości, Zmień nazwę grupy, zgodnie z wymaganiami.|  
|Usuń grupy.|Zaznacz jedną grupę lub kilka, które chcesz usunąć. Otwórz menu skrótów dla wybranego i wybierz polecenie **grupy**, **Usuń grupę**.|  
|Usuń węzły z ich grupy nadrzędnej.|Zaznacz węzły, które chcesz przenieść. Otwórz menu skrótów dla wybranego i wybierz polecenie **grupy**, **Usuń z nadrzędnego**. Spowoduje to usunięcie węzłów się ich nadrzędnego, lub do spoza grupy, gdy mają żadnej grupy nadrzędny.<br /><br /> - lub -<br /><br /> Wybierz węzły i przeciągnij je z grupy.|  
  
##  <a name="AddRemoveNodesLinks"></a>Dodaj, usuń lub zmień nazwę, komentarze węzły i łącza  
 Można wyświetlić więcej lub mniej elementów na mapie, aby przejść do szczegółów lub w celu uproszczenia mapy. Można także zmienić nazwy elementów i dodawanie komentarzy do elementów.  
  
> [!CAUTION]
>  Przed udostępnieniem mapy, który został utworzony przy użyciu programu Visual Studio Enterprise z osób, które używają Visual Professional, upewnij się, że wszystkie elementy kodu innych użytkowników, aby zobaczyć, są widoczne na mapie. W przeciwnym razie tych użytkowników, nie będzie można pobrać elementów usuniętych kodu.  
  
### <a name="add-a-node-for-a-code-element"></a>Dodawanie węzła dla elementu kodu  
  
|**Aby**|**Wykonaj te kroki**|  
|------------|-----------------------------|  
|Dodanie nowego węzła ogólnego w bieżącej lokalizacji wskaźnika myszy.|1.  Przesuń wskaźnik myszy do miejsca na mapie gdzie chcesz umieścić nowy element kodu i naciśnij klawisz **Wstaw**.<br />     - lub -<br />     Otwórz menu skrótów mapy i wybierz polecenie **Edytuj**, **Dodaj**, **ogólne węzła**.<br />2.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracać**.|  
|Dodaj węzeł elementu kodu dla określonego typu w bieżącej lokalizacji wskaźnika myszy.|1.  Przesuń wskaźnik myszy do miejsca na mapie, w którym ma być umieszczony nowy element kodu i otwórz menu skrótów dla mapy.<br />2.  Wybierz **Edytuj**, **Dodaj**i wybierz typ węzła ma.<br />3.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracać**.|  
|Dodawanie do grupy ogólnego lub określonego typu węzeł elementu kodu.|1.  Wybierz węzeł grupy i otwórz menu skrótów.<br />2.  Wybierz **Edytuj**, **Dodaj**i wybierz typ węzła ma.<br />3.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracać**.|  
|Dodanie nowego węzła tego samego typu i połączone z istniejący węzeł.|1.  Wybierz element kodu. Podręcznym pasku narzędzi pojawia się powyżej.<br />     ![Narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")<br />2.  Na pasku narzędzi wybierz ikonę drugi **utworzyć węzeł w tej samej kategorii co ten węzeł i Dodaj nowe łącze do niej**.<br />3.  Wybierz miejsce na mapie, aby umieścić nowy element kodu i kliknij lewy przycisk myszy.<br />4.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracać**.|  
|Dodać nowego węzła ogólnego, który jest połączony z istniejącego elementu kodu, który ma fokus.|1.  Przy użyciu klawiatury, naciśnij klawisz **kartę** dopóki element kodu z ma fokus (kropkowanej prostokąt).<br />2.  Naciśnij klawisz **Alt**+**Wstaw**.<br />3.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracać**.|  
|Dodaj nowy węzeł ogólnego, który stanowi łącze do elementu kodu, który ma fokus.|1.  Przy użyciu klawiatury, naciśnij klawisz **kartę** aż do elementu kodu, aby utworzyć link do ma fokus (kropkowanej prostokąt).<br />2.  Naciśnij klawisz **Alt**+**Shift**+**Wstaw**.<br />3.  Wpisz nazwę dla nowego węzła i naciśnij klawisz **zwracać**.|  
  
|**Aby dodać elementy kodu dla**|**Wykonaj te kroki**|  
|----------------------------------|-----------------------------|  
|Elementy kodu w rozwiązaniu.|1.  Znajdź element kodu w **Eksploratora rozwiązań**. Użyj **Eksploratora rozwiązań** polu wyszukiwania lub Przeglądaj w rozwiązaniu. **Porada:** Aby znaleźć elementy kodu, które są zależne od typu lub elementu członkowskiego, otwórz menu skrótów dla tego typu lub elementu członkowskiego w **Eksploratora rozwiązań**. Wybierz odpowiednią relację. **Eksplorator rozwiązań** zawiera tylko elementy kodu z określonym zależności.<br />2.  Przeciągnij elementy kodu interesujące powierzchnię mapy. Możesz także przeciągnąć elementy kodu z widoku klasy lub przeglądarki obiektów.<br />     - lub -<br />     W **Eksploratora rozwiązań**, wybierz elementy kodu, które mają być mapy. Następnie na **Eksploratora rozwiązań** narzędzi, kliknij przycisk **pokazywanie w mapie kodu**.<br /><br /> Domyślnie w hierarchii kontenera nadrzędnego nowe elementy kodu jest wyświetlany na mapie. Użyj **obejmują nadrzędnych** przycisk na pasku narzędzi mapy kodu, aby zmienić to zachowanie. Gdy wyłączone, tylko kod elementu jest dodany do mapy. Aby wycofać to zachowanie dla tylko jednego przeciągania i upuszczania akcji, naciśnij i przytrzymaj klawisz **CTRL** klucza podczas przeciągania elementy kodu do mapy.<br /><br /> Visual Studio dodaje elementy kodu dla elementów najwyższego poziomu kodu w zaznaczeniu. Aby sprawdzić, czy element kodu zawiera inne elementy kodu, przenieś wskaźnik myszy na górze elementu kodu, aby był wyświetlany cudzysłów ostrokątny (strzałkę). Wybierz cudzysłów ostrokątny, aby rozwinąć elementu kodu. Aby rozszerzyć wszystkie elementy kodu, naciśnij klawisz **CTRL**+**A** aby wybrać wszystkie elementy, otwórz menu skrótów mapy i wybierz polecenie **grupy**, **rozwijania** . To polecenie nie jest dostępne, jeśli rozszerzania wszystkich grup może utworzyć mapę bezużyteczne lub braku problemy z pamięcią.|  
|Powiązane elementy kodu na mapie elementy kodu.|Kliknij przycisk **Pokaż powiązane** znajdującego się na pasku narzędzi mapy kodu i wybierz typ pozycje powiązane osób zainteresowanych.<br /><br /> - lub -<br /><br /> Otwórz menu skrótów dla elementu kodu. Wybierz jedną z **Pokaż...**  elementów menu w zależności od rodzaju relacji interesujący Cię. Można na przykład Zobacz elementy, które odwołuje się do bieżącego elementu, elementy, które odwołują się do bieżącego elementu, typów podstawowych i pochodnych dla klasy, wywołań metody i zawierający klasy, przestrzeni nazw i zestawów.<br /><br /> Aby uzyskać więcej informacji, zobacz [w tym temacie](../modeling/map-dependencies-across-your-solutions.md).|  
|Skompilowane zestawy .NET (.dll lub .exe) lub plików binarnych.|Przeciągnij zestawy lub plików binarnych z zewnętrznego programu Visual Studio do mapy.<br /><br /> Tylko wtedy, gdy są uruchomione na tym samym poziomie uprawnień kontroli dostępu użytkownika (UAC) i Visual Studio można przeciągnąć z Eksploratora Windows lub Eksploratora plików. Na przykład jeśli jest włączona funkcja Kontrola konta użytkownika i używasz programu Visual Studio jako Administrator, Eksploratora Windows lub Eksploratora plików będzie blokował operację przeciągania.|  
  
###  <a name="AddNodes"></a>   
##### <a name="add-a-link-between-existing-code-elements"></a>Dodaj powiązanie istniejące elementy kodu  
  
1.  Wybierz element kodu źródłowego. Pasek narzędzi pojawia się powyżej elementu kodu.  
  
     ![Narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")  
  
2.  Na pasku narzędzi wybierz ikonę pierwszy **Utwórz nowy link z tego węzła do węzła, który który klikniesz w następnej kolejności**.  
  
3.  Wybierz element docelowy kodu. Łącze jest wyświetlane między elementami dwóch kodu.  
  
 \-lub -  
  
1.  Wybierz element kodu źródłowego na mapie.  
  
2.  Jeśli używasz myszy, zainstalowane, przenieś wskaźnik myszy poza granicami mapy.  
  
3.  Otwórz element kodu menu skrótów i wybierz polecenie **Edytuj**, **Dodaj**, **ogólnego łącze**.  
  
4.  Aby i wybierz element kodu docelowego dla łącza.  
  
5.  Naciśnij klawisz **ZWRACAĆ**.  
  
###  <a name="AddComments"></a>   
##### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Dodaj komentarz do istniejący węzeł na mapie  
  
1.  Wybierz element kodu. Pasek narzędzi pojawi się powyżej.  
  
     ![Narzędzi wykresu zależności](../modeling/media/depedencygraph_toolbar.png "DepedencyGraph_Toolbar")  
  
2.  Na pasku narzędzi wybierz ikonę trzeci **Utwórz nowy węzeł komentarzy z nowym linkiem do wybranego węzła**.  
  
     \-lub -  
  
     Otwórz menu skrótów dla elementu kodu i wybierz polecenie **Edytuj**, **nowy komentarz**.  
  
3.  Wpisz swoje komentarze. Aby wpisać w nowym wierszu, naciśnij klawisz **SHIFT** + **ZWRACAĆ**.  
  
##### <a name="add-a-comment-to-the-map-itself"></a>Dodaj komentarz do mapy  
  
1.  Otwórz menu skrótów mapy i wybierz polecenie **Edytuj**, **nowy komentarz**.  
  
2.  Wpisz swoje komentarze. Aby wpisać w nowym wierszu, naciśnij klawisz **SHIFT** + **ZWRACAĆ**.  
  
###  <a name="RenameNodes"></a>   
##### <a name="rename-a-code-element-or-link"></a>Zmiana nazwy elementu kodu lub łącza  
  
1.  Wybierz element kodu lub łącze, które chcesz zmienić.  
  
2.  Naciśnij klawisz **F2**, lub Otwórz menu skrótów i wybierz polecenie **Edytuj**, **zmienić**.  
  
3.  Gdy pojawi się okno edycji na mapie, Zmień nazwę elementu kodu lub łącze.  
  
     \-lub -  
  
4.  Otwórz menu skrótów i wybierz polecenie **Edytuj**, **właściwości**.  
  
5.  Edytuj **etykiety** właściwości w oknie właściwości usługi Visual Studio.  
  
##### <a name="remove-a-code-element-or-link-from-the-map"></a>Usuń element kodu lub Utwórz połączenie z mapy  
  
1.  Wybierz element kodu lub łącza i naciśnij klawisz **usunąć** klucza.  
  
     \-lub -  
  
     Otwórz menu skrótów dla elementu kodu lub łącza i wybierz polecenie **Edytuj**, **Usuń**.  
  
2.  Jeśli element lub łącze jest częścią grupy, **Refetch dzieci** przycisk ![Refetch ikony elementów podrzędnych](../modeling/media/dependencygraph_deletednodesicon.png "DependencyGraph_DeletedNodesIcon") pojawia się w grupie. Kliknij tutaj, aby pobrać brakujące elementy i łącza.  
  
-   Możesz usunąć elementy kodu i linki z mapy bez wpływu na kod źródłowy. Jeśli je usuniesz, ich definicje są usuwane z pliku DGML (.dgml).  
  
-   Mapy utworzone, edytując kod DGML, dodając elementy Niezdefiniowany kod lub za pomocą programu Visual Studio, niektóre starsze wersje nie obsługują tej funkcji.  
  
##### <a name="flag-a-code-element-for-follow-up"></a>Flaga element kodu do monitowania  
  
1.  Wybierz element kodu lub łącza, które chcesz Flaga monitowania.  
  
2.  Otwórz menu skrótów i wybierz polecenie **Edytuj**, **Flaga monitująca**.  
  
-   Domyślnie element kodu uzyskuje czerwone tło. Należy wziąć pod uwagę [Dodawanie komentarza](#AddComments) do niego odpowiednie informacje uzupełniające.  
  
-   Zmiana koloru tła elementu, lub wyczyść Flaga monitująca, wybierając **Edytuj**, **inne kolory flagi**.  
  
##  <a name="ChangeStyleCodeOrLink"></a>Zmień styl elementu kodu lub łącza  
 Możesz zmienić ikony na elementy kodu i kolory elementy kodu i linki przy użyciu wstępnie zdefiniowanych ikony i kolory. Na przykład można kolorów, aby wyróżnić elementy kodu i linki, które ma określonych kategorii ani właściwości. Dzięki temu można zidentyfikować i skoncentrować się na określonych obszarów mapy. Możesz określić niestandardowe ikony i kolory, edytując plik .dgml mapy; zobacz [mapy Dostosuj kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
#### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Aby zastosować kolor wstępnie zdefiniowanych lub ikonę elementy kodu lub powiązania z niektórych właściwości lub kategorii  
  
1.  Na pasku narzędzi mapy wybierz **legendy**.  
  
2.  W **legendy** polu, zobacz, jeśli kod elementu kategoria lub właściwość już występuje na liście.  
  
3.  Jeśli lista nie zawiera kategorii lub właściwości, wybierz  **+**  w **legendy** polu, a następnie wybierz **właściwość węzła**, **węzła kategorii** , **Właściwość łącza**, lub **Link kategorii**. Następnie wybierz pozycję właściwości lub kategorii. Kategoria lub właściwość jest teraz wyświetlany w **legendy** pole.  
  
    > [!NOTE]
    >  Aby utworzyć i przypisać kategorię lub właściwości do elementu kodu, należy edytować pliku .dgml mapy; zobacz [mapy Dostosuj kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
4.  W **legendy** polu, kliknij ikonę obok kategorii lub właściwości zostały dodane lub chcesz zmienić.  
  
5.  Skorzystaj z poniższej tabeli, aby wybrać styl, który ma zostać zmieniony:  
  
    |**Aby zmienić**|**Wybierz pozycję**|  
    |-----------------------|----------------|  
    |Kolor tła|**Tła**|  
    |Kolor konturu|**Obrysu**|  
    |Kolor tekstu (litery "f" jest wyświetlana dla wskazuje wynik)|**Pierwszego planu**|  
    |Ikona|**Ikony**|  
  
     **Ustawić próbnika kolorów** lub **selektora ustawić ikonę** można wybrać kolor lub ikony zostanie wyświetlone okno dialogowe.  
  
6.  W **ustawić próbnika kolorów** lub **selektora ustawić ikonę** okno dialogowe, wykonaj jedną z następujących czynności:  
  
    |**Aby zastosować**|**Wykonaj te kroki**|  
    |--------------------|-----------------------------|  
    |Zestaw kolorów lub ikony|Otwórz **wybierz kolor** (lub **ikona**) **ustawić** listy. Wybierz zestaw kolorów lub ikon.|  
    |Określone lub ikon|Otwórz listę wartości kategorii lub właściwości. Wybierz kolor lub ikonę.|  
  
    > [!NOTE]
    >  Rozmieszczanie, usunąć lub tymczasowo Dezaktywuj style w **legendy** pole. Zobacz [edytować pole legendy](#ModifyLegend).  
  
##  <a name="ModifyLegend"></a>Edytuj pola legendy  
 Rozmieszczanie, usunąć lub tymczasowo Dezaktywuj style w **legendy** pola:  
  
1.  Otwórz menu skrótów w stylu w **legendy** pole.  
  
2.  Wykonaj jedno z następujących zadań:  
  
    |**Aby**|**Wybierz pozycję**|  
    |------------|----------------|  
    |Dezaktywuj elementu kodu|**Wyłącz**|  
    |Usuń code element|**Usuwanie**|  
    |Przenieś styl w górę|**Przenieś w górę**|  
    |Przenieś element kodu w dół|**Przenieś w dół**|  
  
##  <a name="CopyLegend"></a>Skopiuj style z jedną mapę do innego  
  
1.  Upewnij się, że **legendy** na mapy źródłowej zostanie wyświetlone okno. Jeśli nie jest widoczna na pasku narzędzi mapy, kliknij przycisk **legendy**.  
  
2.  Otwórz menu skrótów **legendy** pole. Wybierz **skopiuj legendy**.  
  
3.  Wklej legendy na mapę docelowej.  
  
##  <a name="MergeMaps"></a>Scal mapy kodu  
 Można scalać mapy przez kopiowanie i wklejanie elementów kodu między mapy. Jeśli identyfikatory elementu kodu są zgodne, wklejanie kodu elementy funkcje takie jak operacji scalania. Aby ułatwić to zadanie, umieść wszystkie zestawy lub plików binarnych, które mają być wyświetlane w tym samym folderze, dzięki czemu pełną ścieżkę każdego zestawu lub pliku binarnego jest taka sama dla każdego mapowania, które chcesz scalić.  
  
 Alternatywnie można przeciągnąć tych zestawów lub dane binarne do tej samej mapy z tego folderu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)   
 [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)   
 [Dokumentacja języka DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)
