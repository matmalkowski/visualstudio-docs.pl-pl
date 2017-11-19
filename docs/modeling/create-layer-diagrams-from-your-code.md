---
title: "Tworzenie diagramów zależności z kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: "64"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: 2e98b690fb8ba87dabb7fd8aa76a9aa44c613a38
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="create-dependency-diagrams-from-your-code"></a>Tworzenie diagramów zależności w kodzie
W celu wizualizacji Architektura wysokiego poziomu, logicznych systemu oprogramowania, utworzyć *diagram zależności* w programie Visual Studio. Aby upewnić się, że kod jest zgodny z tego projektu, sprawdź poprawność kodu przy użyciu diagramu zależności. Można tworzyć diagramy zależności dla projektów Visual C# .NET i Visual Basic .NET. Aby dowiedzieć się, które wersje programu Visual Studio obsługują tę funkcję, zobacz [obsługę wersji architektura i modelowanie narzędzi](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 ![Utwórz diagram zależności](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")  
  
 Diagram zależności umożliwia organizowanie elementów rozwiązania Visual Studio w grupy logiczne, abstrakcyjny o nazwie *warstwy*. Można użyć warstw do opisania głównych zadań wykonywanych przez te artefakty lub główne składniki systemu. Każda warstwa może zawierać innych warstwy opisujące bardziej szczegółowe zadania. Można również określić przeznaczone lub istniejące *zależności* między warstwami. Te zależności, które są reprezentowane jako strzałki, wskazują, które warstwy mogą używać lub obecnie używają funkcje reprezentowane przez inne warstwy. Aby utrzymać kontrolę architektury kodu, wyświetl zamierzone zależności na diagramie i przeprowadź walidację kodu na podstawie diagramu.  
  
 [Wideo: Sprawdzanie poprawności zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 
  
##  <a name="CreateDiagram"></a>Utwórz diagram zależności  
 Przed utworzeniem diagramu zależności, upewnij się, że rozwiązanie zawiera projekt modelowania. 
  
> [!IMPORTANT]
>  Nie dodawaj, przeciągnij lub skopiuj istniejący diagram zależności z projektem modelowania do innego projektu modelowania lub w inne miejsce w rozwiązaniu. Pozwala to zachować odniesienia z oryginalnego diagramu nawet po zmianie diagramu. Mogłoby to także uniemożliwić prawidłowe działanie walidacji warstwy i spowodować wystąpienie innych problemów, takich jak brakujące elementy lub inne błędy, przy próbie otwarcia diagramu.  
>   
>  Zamiast tego należy dodać nowy diagram zależności do projektu modelowania. Skopiuj elementy z diagramu źródłowego do nowego diagramu. Zapisać projekt modelowania i nowy diagram zależności.  
  
#### <a name="to-add-a-new-dependency-diagram-to-a-modeling-project"></a>Aby dodać nowy diagram zależności do projektu modelowania  
  
1.  Na **architektura** menu, wybierz **nowy Diagram zależności**.  
  
2.  W obszarze **szablony**, wybierz **diagram zależności**.  
  
3.  Nadaj nazwę diagramowi.  
  
4.  W **Dodaj do projektu modelowania**, wyszukaj i wybierz istniejący projekt modelowania w rozwiązaniu.  
  
     —lub—  
  
     Wybierz **Utwórz nowy projekt modelowania** Aby dodać nowy projekt modelowania do rozwiązania.  
  
    > [!NOTE]
    >  Diagram zależności musi istnieć wewnątrz projektu modelowania. Możesz jednak połączyć elementy w innym miejscu rozwiązania.  
  
5.  Upewnij się zapisać projekt modelowania i diagram zależności.  

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Przeciągnij i upuść, lub skopiowania i wklejenia mapy kodu

1. Generuj mapę kodu dla rozwiązania za pomocą **architektura** menu. 

2. Należy rozważyć stosowanie filtru mapy kodu w celu usuń foldery rozwiązania i "Test zasoby", jeśli chcesz wymusić zależności w kod produktu.

3. Na mapie wygenerowanego kodu Usuń węzeł "External", lub rozwinąć, aby wyświetlić zestawy zewnętrzne, w zależności od tego, czy chcesz wymusić zależności przestrzeni nazw i usunąć — wymagane zestawy z mapy kodu. 

4. Utwórz nowy Diagram zależności dla rozwiązania za pomocą **architektura** menu

5. Zaznacz wszystkie węzły na mapie kodu (Użyj _Ctrl_ + _A_, lub zaznacz pole wyboru gumki, naciskając _Shift_ klucza przed kliknij lub przeciągnij, a wersji.

6. Przeciągnij i upuść, lub kopiowania i wklejania, wybrane elementy do nowego diagramu walidacji zależności. 

7. Wskazuje bieżący architektury aplikacji. Zdecydować, co architektura się i zmodyfikuj odpowiednio diagram zależności.

![Diagram zależności wygenerowane z mapy kodu](media/dependency-validation-01.png)
  
##  <a name="CreateLayers"></a>Tworzenie warstw z artefaktów  
 Warstwy możesz tworzyć z elementów rozwiązania Visual Studio, takich jak projekty, pliki kodu, przestrzenie nazw, klasy i metody. Powoduje to automatyczne tworzenie łączy między warstwami i elementami, uwzględniając je w procesie walidacji warstwy.  
  
 Możesz również połączyć warstwy z elementami, które nie obsługują walidacji, takimi jak dokumenty programu Word lub prezentacji programu PowerPoint, tak aby można było skojarzyć warstwy ze specyfikacjami lub planami. Możesz również połączyć warstwy z plikami projektów współużytkowanymi przez wiele aplikacji, ale proces walidacji nie uwzględni warstw wyświetlanych z nazwami rodzajowymi, takimi jak „Warstwa 1” i „Warstwa 2”.  
  
 Aby sprawdzić, czy połączony element obsługuje sprawdzanie poprawności, otwórz **Explorer warstwy** i sprawdź, czy **obsługuje sprawdzanie poprawności** właściwości elementu. Zobacz [Zarządzanie linki do artefaktów](#Managing).  
  
|**Aby**|**Wykonaj następujące kroki**|  
|------------|----------------------------|  
|Utworzyć warstwę dla pojedynczego artefakt|<ol><li>Przeciągnij element na diagramie zależności z tych źródeł:<br /><br /> <ul><li>**Eksplorator rozwiązań**<br /><br />         Możesz na przykład przeciągać pliki lub projekty.</li><li>Mapy kodu<br /><br />         Zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md) i [mapy użycie kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Widok klasy** lub **przeglądarka obiektów**</li></ul><br />     Warstwy jest wyświetlana na diagramie i jest połączona z artefaktem.</li><li>Zmień nazwę warstwy, aby odzwierciedlała obowiązki skojarzonego kodu lub artefaktów.</li></ol> **Ważne:** przeciąganie plików binarnych do diagramu zależności nie powoduje automatycznego dodania ich odwołania do projektu modelowania. Musisz ręcznie dodać do projektu modelowania pliki binarne, które chcesz walidować. **Aby dodać pliki binarne do projektu modelowania** <ol><li>W **Eksploratora rozwiązań**, otwórz menu skrótów projektu modelowania, a następnie wybierz **Dodaj istniejący element**.</li><li>W **Dodaj istniejący element** okno dialogowe, przejdź do plików binarnych, wybierz je, a następnie wybierz **OK**.     Pliki binarne pojawią się w projekcie modelowania.</li><li>W **Eksploratora rozwiązań**, wybierz plik binarny, który zostanie dodany, a następnie naciśnij **F4** otworzyć **właściwości** okna.</li><li>Na każdym pliku binarnego, ustaw **Akcja kompilacji** właściwości **weryfikacji**.</li></ol>|  
|Utwórz jedną warstwę dla wszystkich zaznaczonych artefaktów|Przeciągnij wszystkie artefakty do diagramu zależności, w tym samym czasie.<br /><br /> Warstw pojawi się na diagramie i będzie połączona z artefaktami.|  
|Tworzenie warstwy dla każdego zaznaczonego artefaktu|Naciśnij i przytrzymaj klawisz **SHIFT** klucza podczas przeciągania wszystkie artefakty do diagramu zależności w tym samym czasie. **Uwaga:** użycie **SHIFT** klawisz, aby wybrać zakres elementów, zwolnij klawisz po wybraniu artefaktów. Naciśnij i przytrzymaj go ponownie podczas przeciągania artefaktów do diagramu. <br /><br /> Warstwa dla każdego artefaktu pojawia się na diagramie i jest połączona z poszczególnymi artefaktami.|  
|Dodawanie artefaktu do warstwy|Przeciągnij artefakt do warstwy.|  
|Tworzenie nowej niepołączonej warstwy|W **przybornika**, rozwiń węzeł **Diagram zależności** sekcji, a następnie przeciągnij **warstwy** do diagramu zależności.<br /><br /> Aby dodać wiele warstw, kliknij dwukrotnie narzędzie. Gdy skończysz, wybierz pozycję **wskaźnika** narzędzi lub naciśnij klawisz **ESC** klucza.<br /><br /> - lub -<br /><br /> Otwórz menu skrótów dla diagramu zależność, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **warstwy**.|  
|Tworzenie zagnieżdżonych warstw|Przeciągnij istniejącą warstwę na inną warstwę.<br /><br /> - lub -<br /><br /> Otwórz menu skrótów dla warstwy, wybierz pozycję **Dodaj**, a następnie wybierz pozycję **warstwy**.|  
|Tworzenie nowej warstwy zawierającej dwie lub więcej istniejących warstw|Zaznacz warstwy, otwórz menu skrótów dla wybranego, a następnie wybierz **grupy**.|  
|Zmienianie koloru warstwy|Ustaw jego **kolor** kolor, który chcesz dla właściwości.|  
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Typ przestrzeni nazw na warstwie **zabronione przestrzenie nazw** właściwości. Użyj średnika (**;**) do oddzielania przestrzenie nazw.|  
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Typ przestrzeni nazw na warstwie **zabronione zależności Namespace** właściwości. Użyj średnika (**;**) do oddzielania przestrzenie nazw.|  
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Typ przestrzeni nazw na warstwie **wymagane obszary nazw** właściwości. Użyj średnika (**;**) do oddzielania przestrzenie nazw.|  
  
 Liczba na warstwie oznacza liczbę artefaktów, które są połączone z warstwą. Jednak odczytując tę liczbę, należy pamiętać, że:  
  
-   Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.  
  
     Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.  
  
-   Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.  
  
##  <a name="Managing"></a>Zarządzanie łącza między warstwami i artefaktów  
  
1.  Na diagramie zależności, otwórz menu skrótów dla warstwy, a następnie wybierz **Wyświetl łącza**.  
  
     **Warstwy Explorer** zawiera linki artefaktu dla wybranej warstwy.  
  
2.  Wykonaj następujące zadania, aby zarządzać tymi łączami:  
  
|**Aby**|**W Eksploratorze warstwy**|  
|------------|---------------------------|  
|Usuwanie łącza między warstwą i artefaktem|Otwórz menu skrótów link artefaktu, a następnie wybierz pozycję **usunąć**.|  
|Przenoszenie łącza z jednej warstwy na drugą|Przeciągnij łącze artefaktu do istniejącej warstwy na diagramie.<br /><br /> - lub -<br /><br /> 1.  Otwórz menu skrótów link artefaktu, a następnie wybierz pozycję **Wytnij**.<br />2.  Na diagramie zależności, otwórz menu skrótów dla warstwy, a następnie wybierz **Wklej**.|  
|Kopiowanie łącza z jednej warstwy na drugą|1.  Otwórz menu skrótów link artefaktu, a następnie wybierz pozycję **kopiowania**.<br />2.  Na diagramie zależności, otwórz menu skrótów dla warstwy, a następnie wybierz **Wklej**.|  
|Tworzenie nowej warstwy z istniejącego łącza artefaktu|Przeciągnij łącze artefaktu do pustego obszaru na diagramie.|  
|Sprawdź, czy połączony artefakt obsługuje sprawdzenia poprawności względem diagram zależności.|Przyjrzyj się **weryfikacji obsługuje** kolumny łącza artefaktu.|  
  
##  <a name="Discovering"></a>Odtwarzanie istniejącej zależności  
 Zależność istnieje wszędzie tam, gdzie artefakt, który jest skojarzony z jedną warstwą zawiera odwołanie do artefaktu skojarzonego z inną warstwą. Na przykład klasa w jednej warstwie deklaruje zmienną, która zawiera klasę w innej warstwie. Możesz odtwarzać istniejące zależności dla artefaktów, które są połączone z warstwami na diagramie.  
  
> [!NOTE]
>  Zależności nie mogą być odtwarzane dla niektórych rodzajów artefaktów. Na przykład nie zostaną odtworzone żadne zależności z lub do warstwy, która jest połączona z plikiem tekstowym. Aby zobaczyć, które artefakty zależnościami mogących odtwarzanie, otwórz menu skrótów dla jednej lub kilku warstw, a następnie wybierz **Wyświetl łącza**. W **Explorer warstwy**, sprawdź **weryfikacji obsługuje** kolumny. Nie można w zależności, odtworzone artefaktów, dla których ta kolumna zawiera **False**.  
  
-   Wybierz jednego lub wielu warstw, otwórz menu skrótów dla wybranej warstwy, a następnie wybierz **Generowanie zależności**.  
  
 Zazwyczaj zobaczysz niektóre zależności, które nie powinny istnieć. Możesz edytować te zależności, aby dopasować je do zamierzonego projektu.  
  
##  <a name="EditDependencies"></a>Edycja warstw i zależności, aby pokazać projektowi  
 Aby opisano zmiany, które mają być system lub docelowej architektury, należy edytować diagram zależności:  
  
|**Aby**|**Wykonaj te kroki**|  
|------------|-----------------------------|  
|Zmień lub ogranicz kierunek zależności|Ustaw jego **kierunek** właściwości.|  
|Tworzenie nowych zależności|Użyj **zależności** i **zależności dwukierunkowego** narzędzia.<br /><br /> Aby narysować wiele zależności, kliknij dwukrotnie narzędzie. Gdy skończysz, wybierz pozycję **wskaźnika** narzędzi lub naciśnij klawisz **ESC** klucza.|  
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Typ przestrzeni nazw na warstwie **zabronione zależności Namespace** właściwości. Użyj średnika (**;**) do oddzielania przestrzenie nazw.|  
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Typ przestrzeni nazw na warstwie **zabronione przestrzenie nazw** właściwości. Użyj średnika (**;**) do oddzielania przestrzenie nazw.|  
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Typ przestrzeni nazw na warstwie **wymagane obszary nazw** właściwości. Użyj średnika (**;**) do oddzielania przestrzenie nazw.|  
  
##  <a name="EditLayout"></a>Zmień sposób wyświetlania elementów na diagramie  
 Możesz zmieniać rozmiar, kształt, kolor i położenie warstw lub kolor zależności, edytując ich właściwości.  
  
##  <a name="Codemaps"></a>Odnajdywanie wzorców i zależności w mapie kodu  
 Podczas tworzenia diagramów zależności, można również tworzyć **code map**. Te diagramy ułatwia odnajdywanie wzorców i zależności podczas eksplorowania kodu. Użyj Eksploratora rozwiązań, widoku klasy lub przeglądarki obiektów do eksplorowania zestawy, obszary nazw i klasy — które często odnoszą się również z istniejącymi warstwami. Aby uzyskać więcej informacji na temat mapy kodu zobacz:  
  
-   [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wideo: Sprawdzanie poprawności zależności architektury w czasie rzeczywistym](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
 [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)   
 [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)   
 [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)   
 [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
