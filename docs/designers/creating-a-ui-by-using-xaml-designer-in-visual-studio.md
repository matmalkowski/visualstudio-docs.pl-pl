---
title: Tworzenie interfejsu użytkownika przy użyciu projektanta XAML w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/17/2017
ms.technology:
- vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: eee5da84104e559d8e95ef022e4496cd3942627f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-ui-by-using-xaml-designer-in-visual-studio"></a>Tworzenie interfejsu użytkownika przy użyciu projektanta XAML w programie Visual Studio
Projektant XAML w programie Visual Studio udostępnia interfejs visual ułatwiające, projektowanie opartych na języku XAML systemu Windows i aplikacje sieci Web. Interfejsy użytkownika można tworzyć dla aplikacji, przeciągając formantów z **przybornika** i ustawianie właściwości w **właściwości** okna. Można również edytować XAML bezpośrednio w widoku XAML.  
  
 Zaawansowane XAML projektowania wykonywanie zadań takich jak animacji i zachowania, zobacz [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md). Zobacz też [projektowania XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md) do porównania narzędzi.
  
## <a name="xaml-designer-workspace"></a>Obszar roboczy Projektanta XAML  
 Obszar roboczy w Projektancie XAML składa się z kilku elementów wizualnych interfejsu. Obejmują one obszaru roboczego edytora XAML urządzenia okna, okno konspektu dokumentu i w oknie właściwości. Aby otworzyć projektanta XAML, kliknij prawym przyciskiem myszy plik XAML w **Eksploratora rozwiązań** i wybierz polecenie **Widok projektanta**.  
  
## <a name="authoring-views"></a>Tworzenie widoków  
 Projektant XAML zapewnia widok XAML i zsynchronizowany widok projektu aplikacji renderowanego kodu znaczników XAML. Z pliku XAML Otwórz w programie Visual Studio, można przełączać się między widokiem projektu i XAML przy użyciu **projekt** i **XAML** karty. Można użyć **wymiany okienka** przycisk, aby przełączyć okna, które pojawia się na wierzchu: obszar roboczy lub edytora XAML.  
  
 W widoku Projekt zawierający okna *kompozycji* jest aktywne okno i służy jako powierzchnia podstawowego. Służy on do wizualne projektowanie strony w aplikacji przez dodanie lub rysowanie elementów, a następnie modyfikując je. Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md). Na tej ilustracji przedstawiono obszar roboczy w widoku Projekt.  
  
 ![Widok projektanta XAML projektu](../designers/media/xaml_editor_design_view.png "xaml_editor_design_view")  
  
 Te funkcje są dostępne w obszarze roboczym:  
  
 **Linie przyciągania**  
 Linie przyciągania są *granice wyrównanie* pojawiających się jako linia przerywana czerwony wierszy wyświetlanych po wyrównania krawędzi formantów lub kiedy są wyrównane linii bazowych tekstu. Wyrównanie granice są wyświetlane tylko wtedy, gdy **przyciąganie do linii wyrównania** jest włączona.  
  
 **Szyny siatki**  
 `Grid` szyny są używane do zarządzania wierszy i kolumn w [siatki](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) panelu. Można tworzyć i usuwać wiersze i kolumny, a można dostosować ich względne szerokości i wysokości. Pionowy szyny siatki, które pojawia się po lewej stronie obszaru roboczego, jest używany dla wierszy i linia pozioma, który jest wyświetlany u góry, służy do kolumny.  
  
 **Definiowania układu siatki**  
 A `Grid` modułu definiowania układu kodu jest wyświetlany jako trójkąt, który ma do niego dołączony na linii pionowych lub poziomych `Grid` kolei. Przeciągnięcie `Grid` modułu definiowania układu kodu, szerokości lub wysokości wierszy lub kolumn sąsiadujących aktualizacji podczas przesuwania myszy.  
  
 `Grid` modułu definiowania układu kodu są używane do kontrolowania szerokość i wysokość `Grid`dla wierszy i kolumn. Można dodać nowej kolumny lub wiersza, klikając w `Grid` szyny. Po dodaniu nowego wiersza wierszy lub kolumn dla `Grid` panelu, które ma dwie lub więcej kolumn lub wierszy, minimalnej narzędzi pojawi się poza kolei, który służy do ustawiania szerokości i wysokości jawnie. Mini narzędzi pozwala ustawić opcje rozmiaru dla `Grid` wierszy i kolumn.  
  
 **Uchwyty zmiany rozmiaru**  
 Zmień rozmiar uchwytów znajdują się w zaznaczonych formantów i umożliwiają rozmiar formantu. Podczas zmiany rozmiaru formantu wartości szerokości i wysokości wyświetlane są zwykle ułatwiające rozmiar formantu. Aby uzyskać więcej informacji na temat manipulowanie formanty w widoku Projekt, zobacz [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md).  
  
 **Marginesy**  
 Marginesy reprezentuje ilość stały odstęp między krawędzią formantu a krawędzią jego kontenera. Marginesy formantu można ustawić przy użyciu [margines](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) właściwości pod **układu** w oknie właściwości.  
  
 **Margines modułu definiowania układu kodu**  
 Margines takich modułów służy do zmiany marginesu elementu względem jego kontenera układu. Po otwarciu moduł definiowania układu kodu margines margines nie jest ustawiona, a moduł definiowania układu margines Wyświetla łańcuch przerwane. Gdy nie ustawiono marginesie, elementy pozostaną w miejscu, gdy kontener układu zmieniany jest rozmiar w czasie wykonywania. Po zamknięciu moduł definiowania układu kodu margines margines modułu definiowania układu kodu wyświetla nieprzerwany łańcuch, a elementy zostanie przesunięty do marginesu jako kontener układu zmieni się rozmiar w czasie wykonywania (margines pozostaje stały).  
  
 **Uchwyty — element**  
 Element można modyfikować za pomocą uchwytów elementu w obszarze roboczym, gdy wskaźnik myszy znajduje się nad narożników obramowania, otaczający element. Uchwyty umożliwiają obracanie, zmienianie rozmiaru, przerzuć, Przenieś i Dodaj promień narożnika do elementu. Symbol uchwytu elementu jest zależna od funkcji i zmian w zależności od dokładnej lokalizacji wskaźnika. Jeśli nie widzisz uchwytów elementu, upewnij się, że element jest zaznaczony.  
  
 W widoku Projekt kompozycji dodatkowe polecenia są dostępne w lewej dolnej części ekranu, jak pokazano poniżej:  
  
 ![Projektowanie widok poleceń](../designers/media/xaml_editor_design_controls.png "xaml_editor_design_controls")  
  
 Te polecenia są dostępne na tym narzędzi:  
  
 **Zoom**  
 Powiększenie umożliwia rozmiaru powierzchnię projektu. Powiększenie z 12,5% 800%, lub wybrać opcje, takie jak **Dopasuj do wyboru** i **dopasowania do wszystkich**.  
  
 **Pokaż/Ukryj siatkę przyciągania**  
 Wyświetla lub ukrywa siatkę przyciągania, który pokazuje linie siatki. Linie siatki są używane podczas albo **przyciąganie do linii siatki** lub **przyciąganie do linii wyrównania** jest włączona.  
  
 **Włącz/wyłącz przyciąganie do linii siatki**  
 Jeśli **przyciąganie do linii siatki** jest włączona, gdy użytkownik przeciąga element w obszarze roboczym, zwykle element, aby były wyrównane z najbliższego poziome i pionowe linie siatki.  
  
 **Włącz/wyłącz przyciąganie do linii wyrównania**  
 Wyrównuje linie przyciągania pomocy określa względem siebie. Jeśli **przyciąganie do linii wyrównania** jest włączona, podczas przeciągania kontroli względem innych kontrolek wyrównanie granice są wyświetlane podczas krawędzi, z tekstem niektóre kontrolki są wyrównane w poziomie lub pionie. Granicy wyrównania jest wyświetlany jako linii kreskowanej czerwony.  
  
 W widoku XAML okna zawierającego edytora XAML jest aktywne okno i edytora XAML jest podstawowym narzędzie autorskie. Extensible Application Markup Language (XAML) zawiera słownik deklaratywne, opartych na języku XML w celu określenia interfejsu użytkownika aplikacji. Widok XAML zawiera IntelliSense, automatycznego formatowania wyróżnianie składni i tagu nawigacji. Na tej ilustracji przedstawiono widok XAML:  
  
 ![Widok XAML](../designers/media/xaml_editor.png "xaml_editor")  
  
 **Widok podziału**  
 Wyświetl pasek podziału jest wyświetlany w górnej części widoku XAML, gdy edytora XAML jest w dolnym okienku. Pasek podziału widoku umożliwia sterowanie względnych rozmiarów widok projektu i języka XAML. Należy również wymienić lokalizacje widoki (przy użyciu **wymiany okienka** przycisk), a następnie określ, czy widoki ułożone poziomo czy pionowo i zwinięcie widoku albo.  
  
 **Kod znaczników powiększenia**  
 Powiększenie znacznika umożliwia rozmiar widoku XAML. 20% można powiększyć do 400%.  
  
## <a name="device-window"></a>Okno urządzenia  
 Okno urządzenia w Projektancie XAML można symulować w czasie projektowania różne widoki, wyświetla i opcje wyświetlania dla projektu. Okno urządzenia jest dostępna w **projekt** menu podczas pracy w Projektancie XAML. Oto wygląda następująco:  
  
 ![Okno urządzenia](../designers/media/xaml_editor_device_panel.png "xaml_editor_device_panel")  
  
 Są to opcje dostępne w oknie urządzenia:  
  
 **Wyświetl**  
 Określa różne rozmiary i rozwiązania dla aplikacji.  
  
 **Orientacja**  
 Określa różnych orientacji dla aplikacji: **pozioma** lub **pionowa**.  
  
 **Krawędzi**  
 Określa wyrównanie krawędzi różnych aplikacji: **zarówno**, **lewej**, **prawej**, lub **Brak**.  
  
 **Duży kontrast**  
 Wyświetla podgląd aplikacji, w oparciu o wybrane ustawienie kontrastu. To ustawienie, jeśli wartość do wartości innych niż **domyślne**, spowoduje zastąpienie `RequestedTheme` właściwość w pliku App.xaml.  
  
 **Zastąpienie skalowania**  
 Włącza i wyłącza emulacji dokumentu skalowanie w powierzchnię projektu. Dzięki temu można zwiększać odsetek skalowania przez jeden składnik. Zaznacz pole wyboru, aby włączyć emulacji. Na przykład jeśli Twoje procent skalowania jest 100%, dokumentu w powierzchnię projektu skalować maksymalnie 140%. Ta opcja jest wyłączona, jeśli bieżąca wartość skalowania jest 180.  
  
 **Minimalna szerokość**  
 Określa ustawienia minimalnej szerokości. Minimalna szerokość można zmienić w pliku App.xaml.  
  
 **Motyw**  
 Określa motyw aplikacji. Na przykład użytkownik może przełączać się między ciemnego i motywu jasny.  
  
 **Pokaż chrome**  
 Włącza i wyłącza ramki symulowane tablet wokół aplikacji w widoku Projekt. Zaznacz pole wyboru, aby wyświetlić ramki.  
  
 **Obiekty do wyświetlenia**  
 Określa tryb wyświetlania. Zaznacz pole wyboru, aby obcina rozmiar dokumentu do rozmiaru ekranu.  
  
## <a name="document-outline-window"></a>Okno konspektu dokumentu  
 Okno konspektu dokumentu w Projektancie XAML ułatwia wykonywanie tych zadań:  
  
-   Struktura hierarchiczna wszystkie elementy w obszarze roboczym.  
  
-   Wybierz elementy, dzięki czemu można zmodyfikować je (przenieś je w hierarchii, zmodyfikuj je w obszarze roboczym, ich właściwości w oknie właściwości i tak dalej). Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md)  
  
-   Tworzenie i modyfikowanie szablonów dla elementów, które są formanty.  
  
-   Użyj menu kontekstowego dla wybranych elementów. Tym samym menu jest również dostępna dla wybranych elementów w obszarze roboczym.  
  
 Aby wyświetlić okno konspektu dokumentu, na pasku menu wybierz **widoku**, **inne okna**, **konspekt dokumentu**.  
  
 ![Okno konspektu dokumentu](../designers/media/xaml_editor_doc_outline.png "xaml_editor_doc_outline")  
  
 Są to opcje dostępne w okno konspektu dokumentu:  
  
 **Konspekt dokumentu**  
 Widok główny okno konspektu dokumentu Wyświetla hierarchię dokumentu w strukturze drzewa. Za pomocą hierarchicznej charakter konspekt dokumentu do sprawdzenia dokument na różnych poziomach szczegółowości, Zablokuj i Ukryj elementy pojedynczo lub grupowo.  
  
 **Pokaż/Ukryj**  
 Wyświetla lub ukrywa obszar roboczy elementy, które odpowiadają elementom konspektu dokumentu. Użyj **Pokaż/Ukryj** przycisków, które wyświetlanie symboli oka, gdy wyświetlana lub naciśnij klawisze CTRL + H, aby ukryć elementy i SHIFT + CTRL + H, aby je wyświetlić.  
  
 **Zablokuj/Odblokuj**  
 Umożliwia zablokowanie lub odblokowanie obszar roboczy elementy, które odpowiadają elementom konspektu dokumentu. Nie można zmodyfikować zablokowanych elementów. Użyj **Zablokuj/Odblokuj** przycisków, które zawierają kłódka symboli, gdy zablokowany, lub naciśnij klawisze CTRL + L elementy blokady i SHIFT + CTRL + L do ich odblokowania.  
  
 **Przywrócenie zakres pageRoot**  
 Opcja u góry okna konspekt dokumentu znajduje się symbol strzałki, zwraca konspekt dokumentu do poprzedniego zakresu. Określanie zakresu się ma zastosowanie tylko wtedy, gdy jesteś w zakresie stylu lub szablonie.  
  
## <a name="properties-window"></a>Okno właściwości  
 Okno właściwości umożliwia ustawiania wartości właściwości kontrolki. Oto wygląda następująco:  
  
 ![Okno właściwości](../designers/media/xaml_editor_prop_window.png "xaml_editor_prop_window")  
  
 Istnieją różne opcje w górnej części okna właściwości. Możesz zmienić nazwę aktualnie zaznaczonego elementu przy użyciu **nazwa** pole. W lewym górnym rogu ma ikony reprezentującej obecnie wybranego elementu. Aby ustawić właściwości według kategorii lub alfabetycznie, kliknij przycisk **kategorii**, **nazwa**, lub **źródła** w **Rozmieść według** listy. Aby wyświetlić listę zdarzeń dla formantu, kliknij **zdarzenia** przycisku, który wyświetla lightning bolt symbol. Aby wyszukać właściwości, uruchom nazwy właściwości w **właściwości wyszukiwania** pole. Okno właściwości są wyświetlane właściwości spełniających kryteria wyszukiwania. Niektóre właściwości umożliwiają skonfigurowanie zaawansowanych właściwości, wybierając przycisk strzałki w dół. Aby uzyskać więcej informacji na przy użyciu właściwości i ich obsługi zdarzeń, zobacz [Szybki Start: dodawanie formantów i obsługa zdarzeń](http://go.microsoft.com/fwlink/?LinkID=247983)  
  
 Po prawej stronie każdej właściwości jest wartość *znacznik właściwości* wyświetlany jako symbol pola. Wygląd znacznik właściwości wskazuje, czy powiązania danych lub zastosować do właściwości zasobu. Na przykład symbol biała Skrzynka wskazuje wartość domyślną, symbol czarne pole zwykle wskazuje, że zastosowano zasobów lokalnych i pomarańczowy pole zwykle wskazuje, że zastosowano powiązania danych. Po kliknięciu znacznik właściwości można przejść do definicji stylu, otworzyć Konstruktora powiązania danych lub Otwórz selektor zasobów.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md)   
 [Jak utworzyć i zastosować zasobu](../designers/how-to-create-and-apply-a-resource.md)   
 [Przewodnik: tworzenie powiązań z danymi w projektancie XAML](../designers/walkthrough-binding-to-data-in-xaml-designer.md)