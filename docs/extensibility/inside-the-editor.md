---
title: W edytorze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 181a414d4cf1b9def941f32560d41158c0ed92fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="inside-the-editor"></a>W edytorze
Edytor składa się z liczbą różne podsystemy, które pozwalają zapobiec Edytor tekstu oddzielnego modelu widoku tekstu i interfejs użytkownika.  
  
 W tych sekcjach opisano różne aspekty edytora:  
  
-   [Omówienie podsystemów](../extensibility/inside-the-editor.md#overview)  
  
-   [Modelu tekstu](../extensibility/inside-the-editor.md#textmodel)  
  
-   [Wyświetlanie tekstu](../extensibility/inside-the-editor.md#textview)  
  
 W tych sekcjach opisano funkcje edytora:  
  
-   [Znaczniki i klasyfikatory](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [Skojarzenia](../extensibility/inside-the-editor.md#adornments)  
  
-   [Projekcja](../extensibility/inside-the-editor.md#projection)  
  
-   [Obramowanie](../extensibility/inside-the-editor.md#outlining)  
  
-   [Powiązania myszy](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [Operacje edytora](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [Funkcja IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> Omówienie podsystemów  
  
### <a name="text-model-subsystem"></a>Podsystem modelu tekstu  
 Podsystem modelu tekstu jest odpowiedzialny za reprezentujący tekstu i włączenie jej manipulowanie. Zawiera podsystemu modelu tekstu <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfejsu, co opisano sekwencji znaków, który ma być wyświetlany przez edytor. Ten tekst można modyfikować, śledzone i w przeciwnym razie manipulować na wiele sposobów. Modelu tekstu udostępnia typy dla następujących elementów:  
  
-   Usługa, która kojarzy tekstu z plików i zarządza odczytywanie i zapisywanie ich w systemie plików.  
  
-   Usługa różnicowych znajduje minimalnego różnice między dwóch sekwencji obiektów.  
  
-   System opisujące tekstu w buforze pod względem podzbiór tekstu w innych buforów.  
  
 Podsystem modelu tekstu jest bezpłatna koncepcji interfejsu użytkownika. Na przykład nie jest odpowiedzialny za formatowania tekstu lub układu tekstu i go nie ma informacji o visual skojarzenia, które mogą być skojarzone z tekstu.  
  
 Typy publiczne podsystemu modelu tekstu znajdują się w Microsoft.VisualStudio.Text.Data.dll i Microsoft.VisualStudio.CoreUtilitiy.dll, zależnych tylko od klasy podstawowej biblioteki .NET Framework i Framework Managed Extensibility (MEF).  
  
### <a name="text-view-subsystem"></a>Podsystem widoku tekstu  
 Podsystem widoku tekstu jest odpowiedzialny za formatowania i wyświetlania tekstu. Typy w tym podsystemu są podzielone na dwie warstwy, w zależności od tego, czy typy polegać na systemie Windows Presentation Foundation (WPF). Najważniejsze typy są <xref:Microsoft.VisualStudio.Text.Editor.ITextView> i <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, które kontrolować zestawu wierszy tekstu, które mają być wyświetlane i również karetki, zaznaczenia i urządzenia do adorning tekst przy użyciu elementów interfejsu użytkownika WPF. Podsystem ten zawiera również obszar wyświetlania marginesy wokół tekstu. Marginesy te można ją rozszerzyć i może zawierać różne rodzaje efekty zawartości i visual. Przykłady marginesy wiersza numer Wyświetla i pasków przewijania.  
  
 Typy publiczne podsystemu widoku tekstu znajdują się w Microsoft.VisualStudio.Text.UI.dll i Microsoft.VisualStudio.Text.UI.Wpf.dll. Pierwszy zestaw zawiera elementy niezależne od platformy, a drugi zawiera elementy specyficzne dla WPF.  
  
### <a name="classification-subsystem"></a>Podsystem klasyfikacji  
 Podsystem klasyfikacji jest odpowiedzialny za określenie właściwości czcionki tekstu. Klasyfikator dzieli tekst na różnych klas, na przykład "— słowo kluczowe" lub "comment". Mapa formatu klasyfikacji dotyczy tych klas właściwości rzeczywiste czcionki, na przykład "niebieski Consolas 10 pt". Te informacje jest używany przez widoku tekstu, kiedy formatuje i renderowanie tekstu. Znakowanie, który jest opisany bardziej szczegółowo w dalszej części tego tematu, umożliwia danych ma zostać skojarzony z zakresami tekstu.  
  
 Typy publiczne podsystemu klasyfikacji są zawarte w Microsoft.VisualStudio.Text.Logic.dll i ich interakcji z visual aspekty klasyfikacji, które są zawarte w Microsoft.VisualStudio.Text.UI.Wpf.dll.  
  
### <a name="operations-subsystem"></a>Podsystem działania  
 Podsystem działania definiuje zachowanie edytora. Udostępnia implementację dla poleceń edytora programu Visual Studio i system cofania.  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Bliższe spojrzenie na modelu tekstu i widoku tekstu  
  
###  <a name="textmodel"></a> Modelu tekstu  
 Podsystem modelu tekstu składa się z różnych grup z typów tekstu. Obejmują one buforu tekstu, migawek tekstu i zakresami tekstu.  
  
#### <a name="text-buffers-and-text-snapshots"></a>Bufory tekstu i migawek tekstu  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> Interfejsu reprezentuje sekwencję znaków Unicode, które są zakodowane za pomocą UTF-16, który jest używany przez `String` typu w programie .NET Framework. Bufor tekstowy może zostać utrwalony jako dokument systemu plików, ale nie jest to wymagane.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> Służy do tworzenia buforu pusty tekst lub buforu tekstu, który został zainicjowany z ciągiem lub <xref:System.IO.TextReader>. Bufor tekstowy mógł być trwały w systemie plików jako <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 Bufor tekstowy mogą być edytowane przez dowolnego wątku do momentu wątku przejmuje buforu tekst przez wywołanie metody <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Po wykonaniu tej tylko wątek można wykonać zmiany.  
  
 Bufor tekstowy można przejść przez wiele wersji przez jego okres istnienia. Nowa wersja jest generowana za każdym razem, gdy bufor jest edytowany oraz modyfikować <xref:Microsoft.VisualStudio.Text.ITextSnapshot> reprezentuje zawartość wersji buforu. Ponieważ tekst migawki są niezmienne, są dostępne migawki tekstu w którymkolwiek wątku bez ograniczeń, nawet wtedy, gdy bufor tekstowy, który reprezentuje on w dalszym ciągu zmiany.  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>Tekst migawki i liniami migawek tekstu  
 Można wyświetlić zawartość migawki tekstu, jako sekwencja znaków lub sekwencji wierszy. Znaki i wiersze są indeksowane zarówno, zaczynając od zera. Migawki pusty tekst zawiera znaki zero i jeden pusty wiersz. Wiersz jest rozdzielane przy żadnych prawidłową sekwencją znaku Unicode podziału wierszy, na początku lub na końcu buforu. Znaki końca wiersza są jawnie reprezentowane w migawce tekstu, a podziały wierszy w migawce tekst nie wszystkie muszą być takie same.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat znaków podziału wierszy w edytorze programu Visual Studio, zobacz [kodowania i podziały](../ide/encodings-and-line-breaks.md).  
  
 Wiersz tekstu jest reprezentowana przez <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> obiektu, który można uzyskać z migawki tekst numer określonego wiersza lub pozycji określonego znaku.  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans i NormalizedSnapshotSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> reprezentuje pozycji znaku w migawce. Pozycja jest gwarantowane znajdować się między zero a długość migawki. A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> reprezentuje fragment tekstu w migawce. Jego pozycja końcowa jest gwarantowane znajdować się między zero a długość migawki. <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> Składa się z zestawem <xref:Microsoft.VisualStudio.Text.SnapshotSpan> obiekty z tym samym migawki.  
  
#### <a name="spans-and-normalizedspancollections"></a>Zakresy i NormalizedSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.Span> reprezentuje interwału, który można zastosować do fragment tekstu w migawce tekstu. Pozycje migawki są liczony od zera, więc zakresy można uruchomić w dowolnym miejscu w tym zero. `End` Właściwości zakresu jest równa sumie jego `Start` właściwość i jej `Length` właściwości. A `Span` nie zawiera znak, który jest indeksowany przez `End` właściwości. Na przykład zakres zawierający Start = 5, a długość = 3 ma zakończenia = 8, i zawiera znaki w miejscach, 5, 6 i 7. Ten zakres jest 5..8).  
  
 Dwa zakresy intersect, jeśli mają wszystkie pozycje, w tym pozycja końcowa. W związku z tym przecięcie [3, 5) i [2, 7) jest [3, 5) i [3, 5) i [5, 7) jest [5, 5). (Zwróć uwagę, że [5, 5) jest pusty zakres.)  
  
 Dwa zakresy nakładają się, jeśli mają one pozycji, z wyjątkiem pozycja końcowa. Pusty zakres nigdy nie nakłada na inne zakresu i nakładanie się dwa zakresy nigdy nie jest pusty.  
  
 A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> znajduje się lista obejmuje według właściwości Start zakresów. Na liście zakresów zachodzącymi na siebie lub zostaną scalone. Na przykład, mając zestaw zakresów [5..9), [0..1), [3..6), i [9..10), jest znormalizowana lista obejmuje [0..1), [3..10).  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit, TextVersion i powiadomień o zmianie tekstu  
 Zawartość buforu tekstu można zmieniać za pomocą <xref:Microsoft.VisualStudio.Text.ITextEdit> obiektu. Tworzenie takiego obiektu (za pomocą jednego z `CreateEdit()` metody <xref:Microsoft.VisualStudio.Text.ITextBuffer>) uruchamia transakcji tekst, który składa się z edytowanych wartości tekstowych. Edytuj co zastępuje niektórych fragment tekstu w buforze przez ciąg. Współrzędne i zawartości co edycji jest wyrażone w odniesieniu migawki buforu rozpoczęcie transakcji. <xref:Microsoft.VisualStudio.Text.ITextEdit> Obiektu dopasowuje współrzędne zmiany, których dotyczy innych zmian w tej samej transakcji.  
  
 Rozważmy na przykład buforu tekstu, który zawiera ten ciąg:  
  
```  
abcdefghij  
```  
  
 Zastosuj transakcji, która zawiera dwa edycji, jeden edycji, który zastępuje zakres na [2..4) za pomocą znaku `X` i drugi edycji, który zastępuje zakres na [6..9) za pomocą znaku `Y`. Wynik jest buforu:  
  
```  
abXefYj  
```  
  
 Współrzędne do edycji drugi zostały obliczana względem zawartości buforu na początku transakcji, przed zastosowaniem pierwsza edycja.  
  
 Wprowadzenia zmian w buforze podczas <xref:Microsoft.VisualStudio.Text.ITextEdit> obiektu zostaje zatwierdzona przez wywołanie jego `Apply()` metody. Jeśli wystąpił co najmniej jeden niepusty edycji, nowy <xref:Microsoft.VisualStudio.Text.ITextVersion> jest tworzony nowy <xref:Microsoft.VisualStudio.Text.ITextSnapshot> jest tworzony i jedną `Changed` zdarzenie jest wywoływane. Każda wersja tekst ma inną migawki tekstu. Migawki tekst reprezentuje pełną stan buforu tekstu po edycji transakcji, ale wersja tekstu w tym artykule opisano tylko zmiany z migawki jeden do następnego. Ogólnie rzecz biorąc migawek tekstu jest przeznaczony do jednorazowego użytku, a następnie zostaje odrzucone, gdy wersje tekst musi pozostać aktywne przez pewien czas.  
  
 Wersja tekst zawiera <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Ta kolekcja zawiera opis zmian, który po zastosowaniu do migawki, utworzy kolejnych migawki. Każdy <xref:Microsoft.VisualStudio.Text.ITextChange> w kolekcji zawiera znaku na pozycji zmian, zastąpionego ciągu i ciąg zastępczy. Zastąpionego ciąg jest pusty dla podstawowego wstawiania, a ciąg zastępczy jest pusta, do usunięcia podstawowej. Kolekcja, znormalizowany jest zawsze `null` do najnowszej wersji buforu tekstowego.  
  
 Tylko jeden <xref:Microsoft.VisualStudio.Text.ITextEdit> obiektu można wdrożyć dla buforu tekstu w dowolnym momencie, a wszystkie edytowanych wartości tekstowych musi zostać wykonana na wątku, który jest właścicielem bufor tekstowy (jeśli została odebrana własność). Edycja tekstu może porzucone przez wywołanie jego `Cancel` — metoda lub jego `Dispose` metody.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> dostępne są także `Insert()`, `Delete()`, i `Replace()` metod, które przypominają te znalezione na <xref:Microsoft.VisualStudio.Text.ITextEdit> interfejsu. Wywoływanie te działa tak samo jak tworzenie <xref:Microsoft.VisualStudio.Text.ITextEdit> obiektu, podobne wywołania, a następnie zastosowaniu edycji.  
  
#### <a name="tracking-points-and-tracking-spans"></a>Śledzenie punktów i śledzenia zakresów  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint> Reprezentuje pozycji znaku w buforze tekstu. W przypadku modyfikacji buforu w taki sposób, który powoduje, że położenie znaku, które mają zostać przesunięte punktu śledzenia przewiduje się z nim. Na przykład jeśli punktu śledzenia odwołuje się do pozycji 10 w buforze, a pięć znaków są wstawiane na początku buforu, punktu śledzenia następnie odwołuje się do pozycji 15. W przypadku wstawiania w dokładnie pozycji wskazywane przez punkt śledzenia, jego zachowanie jest określany przez jego <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, które mogą być `Positive` lub `Negative`. Jeśli tryb śledzenia jest dodatnia, punktu śledzenia odwołuje się do tej samej litery, która jest teraz na końcu wstawiania; Jeśli tryb śledzenia jest ujemna, punktu śledzenia odwołuje się do pierwszego znaku wstawiony z oryginalnej pozycji. Usunięcie znaków od pozycji reprezentowanego przez punkt śledzenia punktu śledzenia przenosi do pierwszego znaku, który następuje usuniętego zakresu. Na przykład jeśli punktu śledzenia odwołuje się do znaku na pozycji 5 znaków w miejscach 3 – 6 są usuwane, punktu śledzenia odwołuje się do znaku na pozycji 3.  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> Reprezentuje zakres znaków, a nie tylko jedną pozycję. Zachowanie zależy od jego <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Jeśli jest tryb śledzenia zakresu <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, zakres śledzenia zwiększania rozmiaru w celu uwzględnienia tekst wstawione w jego krawędzi; Jeśli tryb zakresu śledzenia jest <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, zakres śledzenia nie obejmuje wstawione w jego krawędzi tekstu. Jednak jeśli jest tryb śledzenia zakresu <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, wstawiania wypychanie bieżącej pozycji do początku i jeśli tryb śledzenia zakresu <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, wstawiania wypychanie bieżącej pozycji do końca.  
  
 Możesz też uzyskać położenie punktu śledzenia lub zakres zakres śledzenia wszystkie migawki buforu tekstu, do którego należą. Śledzenie punktów i śledzenie obejmuje odwołania mogą dotyczyć bezpiecznie z dowolnego wątku.  
  
#### <a name="content-types"></a>Typy zawartości  
 Typy zawartości to mechanizm służący do definiowania różnych typów zawartości. Typ zawartości może być typem pliku, takie jak "text", "kod" lub "binary" lub typ technologii, takich jak "xml", "vb" lub "c#". Na przykład wyraz "wykorzystuje" jest słowem kluczowym w języku C# i Visual Basic, ale nie w innych językach programowania. W związku z tym definicji to słowo kluczowe będzie ograniczony do typów zawartości "c#" i "vb".  
  
 Typy zawartości są używane jako filtr dla skojarzenia i innych elementów edytora. Wiele funkcji edytora i punkty rozszerzenia są definiowane dla każdego typu zawartości; na przykład tekstu kolorowania różni się pliki w formacie zwykłego tekstu, pliki XML i pliki kodu źródłowego języka Visual Basic. Tekst buforów zazwyczaj są przypisywane typu zawartości podczas ich tworzenia, a można zmienić typu zawartości buforu tekstu.  
  
 Typy zawartości wielu — dziedziczenie z innych typów zawartości. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Pozwala określić wiele typów podstawowych jako nadrzędne danego typu zawartości.  
  
 Deweloperzy mogą Definiowanie własnych typów zawartości i zarejestruj je przy użyciu <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Można zdefiniować wiele funkcji edytora w odniesieniu do określonego typu zawartości przy użyciu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Na przykład marginesu edytora, skojarzenia i obsługi myszy można zdefiniować, dzięki czemu mają one zastosowanie tylko do edytory zawierające określonych typów zawartości.  
  
###  <a name="textview"></a> Wyświetlanie tekstu  
 Part widok wzorca model widoku kontroler (MVC) definiuje widoku tekstu, formatowanie widoku, graficznych elementów, takich jak pasek przewijania i karetki. Wszystkie elementy prezentacji w edytorze programu Visual Studio są oparte na WPF.  
  
#### <a name="text-views"></a>Widoki tekstowe  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> Interfejs jest niezależne od platformy reprezentację widoku tekstu. Jest używany głównie w celu wyświetlenia dokumentów tekstowych w oknie, ale może również służyć do innych celów, na przykład w etykietce narzędzia.  
  
 Widok tekstu odwołuje się do różnych rodzajów buforów tekstu. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> Właściwość odwołuje się do <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> obiekt, który wskazuje bufory trzy inny tekst: bufor danych, który jest najwyższym buforu poziom danych, bufor edycji, w którym Edycja występuje i visual buforu, który jest buforu, który jest wyświetlane w widoku tekstu.  
  
 Tekst jest formatowany w oparciu o klasyfikatory, które są dołączone do podstawowej buforu tekstu i jest adorned za pomocą dostawców ozdób, które są dołączone do samego widoku tekstu.  
  
#### <a name="the-text-view-coordinate-system"></a>System współrzędnych widoku tekstu  
 System współrzędnych widoku tekstu określa pozycje w widoku tekstu. W tym układzie współrzędnych x wartość 0,0 odpowiada do lewej krawędzi tekstu wyświetlanego i wartości y 0,0 odpowiada górnej krawędzi tekstu wyświetlanego. Współrzędna x zwiększa od lewej do prawej, a współrzędna y zwiększa od góry do dołu.  
  
 Okienko ekranu (część widoczne tekst z okna tekstowego) nie mogą być przewijane w taki sam sposób jak poziomo jak jest przewijane w pionie. Okienko ekranu jest przewijane w poziomie, zmieniając jej lewą współrzędną był przenoszony względem powierzchni do rysowania. Jednak okienko ekranu może być przewijana pionowo zmieniając renderowanego tekstu, co powoduje, że <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> się zdarzenia.  
  
 Odległości w układzie współrzędnych odpowiadają logicznej pikseli. Jeśli powierzchnię renderowania tekst jest wyświetlany bez skalowania transformacji jednostki w układzie współrzędnych renderowanie tekstu odpowiada to jeden piksel na ekranie.  
  
#### <a name="margins"></a>Marginesy  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> Interfejsu reprezentuje margines i umożliwia kontrolę nad widoczność margines i jego rozmiaru. Istnieją cztery wstępnie zdefiniowane marginesy, które są nazywane "Top", "Lewo", "Prawej" i "Bottom" i są dołączone do góry, dół, lewo lub prawej krawędzi widoku. Marginesy te są kontenerami, w których można umieścić inne marginesy. Interfejs definiuje metody, które zwracają rozmiar marginesu i widoczności margines. Marginesy są elementy wizualne, które zawierają dodatkowe informacje o widoku tekstu, do której są dołączone. Na przykład margines numer wiersza Wyświetla numerów wierszy w widoku tekstu. Margines symbolu Wyświetla elementy interfejsu użytkownika.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Interfejs obsługuje tworzenie i umieszczania marginesu. Marginesy może zostać określona względem inne marginesy. Marginesy wyższy priorytet znajdują się bliżej widoku tekstu. Na przykład jeśli istnieją dwie lewego marginesu, A i B margines z niższym priorytetem niż marginesu ma margines B, margines B pojawi się do lewego marginesu A.  
  
#### <a name="the-text-view-host"></a>Host widoku tekstu  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Interfejs zawiera widok tekstu i wszelkie stykających dekoracje dołączone do widoku, na przykład paski przewijania. Host widoku tekstu zawiera również marginesy, które są dołączone do obramowania widoku.  
  
#### <a name="formatted-text"></a>Tekst sformatowany  
 Tekst, który jest wyświetlany w widoku tekstu składa się z <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> obiektów. Każdy wiersz widoku tekstu odnosi się do jednego wiersza w widoku tekstu. Długie wiersze w podstawowej bufor tekstowy można być częściowo przesłaniać (Jeśli nie jest włączone zawijanie) lub podzielony na wiele wierszy widoku tekstu. <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Interfejs zawiera metody i właściwości dla mapowania między współrzędnych i znaków i skojarzenia, które mogą być skojarzone z wiersza.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> obiekty są tworzone za pomocą <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interfejsu. Jeśli właśnie zajmującym się tekst, który jest aktualnie wyświetlany w widoku, możesz zignorować formatowania źródła. Jeśli interesuje Cię w formacie tekstu, który nie jest wyświetlany w widoku (na przykład do obsługi wycinania tekst sformatowany i wkleić), możesz użyć <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> formatowania tekstu w buforze tekstu.  
  
 Formatuje widoku tekstu, co <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> naraz.  
  
## <a name="editor-features"></a>Funkcje edycji  
 Funkcje edytora są zaprojektowane tak, aby definicji funkcji różni się od jego wykonania. Edytor zawiera następujące funkcje:  
  
-   Znaczniki i klasyfikatory  
  
-   Skojarzenia  
  
-   Rzut  
  
-   Tworzenie konspektu  
  
-   Powiązania myszy i klucz  
  
-   Operacje i podstawowych  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> Znaczniki i klasyfikatory  
 Tagi są znaczników, które są skojarzone z zakres tekstu. Były widoczne w różny sposób, na przykład przy użyciu tekstu kolorowania, podkreślenia, grafiki lub wyskakujące okienka. Klasyfikatory są jednego rodzaju znaczników.  
  
 Inne rodzaje tagi są <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> dla wyróżnianie tekstu, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> tworzenia konspektów, i <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> błędy kompilacji.  
  
#### <a name="classification-types"></a>Typy klasyfikacji  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Interfejsu reprezentuje klasy równoważność, która jest abstrakcyjny kategorii tekstu. Typy klasyfikacji wielu — dziedziczenie z innych typów klasyfikacji. Na przykład klasyfikacje języka programowania może obejmować "— słowo kluczowe", "comment" i "identyfikator", które dziedziczą z 'code'. Typy klasyfikacji języka naturalnego może obejmować "rzeczownik", "zlecenie" i "przymiotnik", które dziedziczą z "języka naturalnego".  
  
#### <a name="classifications"></a>Klasyfikacje  
 Klasyfikacja jest wystąpienia typu określonej klasyfikacji, zwykle za pośrednictwem fragment tekstu. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> jest używana do reprezentowania klasyfikacji. Zakres klasyfikacji można traktować jako etykieta obejmuje określonego fragment tekstu, który informuje system, że ten zakres tekstu jest typu określonej klasyfikacji.  
  
#### <a name="classifiers"></a>Klasyfikatory  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> Mechanizm, który dzieli tekst na zestaw klasyfikacji. Klasyfikatory musi być zdefiniowany dla określonych typów zawartości i wystąpienia dla buforów określony tekst. Klienci muszą implementować <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> brać udziału w klasyfikacji tekstu.  
  
#### <a name="classifier-aggregators"></a>Klasyfikator agregatora  
 Agregator klasyfikatora jest mechanizm, który łączy wszystkie klasyfikatory buforu tekstowego w tylko jeden zestaw klasyfikacji. Na przykład zarówno klasyfikatora C# i klasyfikatora języka angielskiego można utworzyć klasyfikacje za pośrednictwem komentarz w pliku języka C#. Ten komentarz należy wziąć pod uwagę:  
  
```  
// This method produces a classifier  
```  
  
 Klasyfikator C# może etykietę cały zakres jako komentarz, a klasyfikatora języka angielskiego mogą klasyfikować "tworzy" jako "zlecenie" i "method" jako "rzeczownik". Agregator tworzy zbiór nienakładających klasyfikacji, a typ zestawu jest oparty na wszystkie udziały.  
  
 Agregator klasyfikatora jest również klasyfikatora, ponieważ przerywa tekstu w zestawie klasyfikacje. Agregator klasyfikatora gwarantuje również, że nie istnieją żadne klasyfikacje nakładających się i że klasyfikacje są sortowane. Poszczególne klasyfikatory są bezpłatne do zwrócenia dowolny zbiór klasyfikacje, w dowolnej kolejności i nakładające się w dowolny sposób.  
  
#### <a name="classification-formatting-and-text-coloring"></a>Kolorowanie tekstu i formatowanie klasyfikacji  
 Formatowanie tekstu jest przykładem funkcja, która jest oparty na klasyfikacji tekstu. Jest on używany przez warstwę widoku tekstu ustalenie wyświetlanie tekstu w aplikacji. Obszar formatowania tekstu jest zależna od WPF, ale nie jest logiczną definicji klasyfikacji.  
  
 Format klasyfikacji to zbiór właściwości dla typu określonej klasyfikacji formatowania. Te formaty dziedziczyć format elementu nadrzędnego typu klasyfikacji.  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> Mapowanie z typu klasyfikacji do zestawu właściwości formatowania tekstu. Implementacja Mapa formatu w edytorze obsługuje eksportu formatów klasyfikacji.  
  
###  <a name="adornments"></a> Skojarzenia  
 Skojarzenia są efektów graficznych, które nie są bezpośrednio związane z czcionek i kolorów znaków w widoku tekstu. Na przykład podkreślenie czerwona falista, który jest używany do oznaczania — kompilowanie kodu w wielu językach programowania jest osadzony ozdób i etykietki narzędzi są wyskakujące skojarzenia. Pochodne skojarzenia <xref:System.Windows.UIElement> i wdrożenie <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Istnieją dwa typy specjalne tagu ozdób <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, dla skojarzenia, które zajmują to samo miejsce jako tekst w widoku i <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, dla wężyk podkreślenie.  
  
 Osadzony skojarzenia są grafiki, które stanowią część widoku tekstu sformatowanego. Są zorganizowane w różnych warstwach porządek osi z. Istnieją trzy warstwy wbudowanych, w następujący sposób: tekst, karetki i zaznaczenia. Jednak deweloperzy można zdefiniować więcej warstwy i umieść je w kolejności względem siebie. Są trzy rodzaje osadzonych skojarzenia skojarzenia względem tekstu, (które przenoszenia po przemieszczeniu tekstu i są usuwane po usunięciu tekst), skojarzenia względem widoku, (które mają z części nietekstowych widoku) i kontrolowane przez właściciela skojarzenia ( Deweloper musi zarządzać ich umieszczania).  
  
 Wyskakujące skojarzenia są grafiki, które są wyświetlane w oknie małych powyżej widoku tekstu, na przykład etykietek narzędzi.  
  
###  <a name="projection"></a> Projekcji  
 Projekcja ma technika konstruowania inny rodzaj buforu tekst, który nie przechowuje tekstu, ale zamiast tego łączą tekstu z innych buforów tekstu. Na przykład buforu projekcji może służyć do Połącz tekst z dwóch innych buforów i przedstawia wynik tak, jakby była w buforze tylko jednego lub ukrywanie fragmenty tekstu w buforze jeden. Bufor projekcji może działać jako bufor źródłowy, do innego buforu projekcji. Zestaw buforów, które są powiązane przez projekcję może zostać zbudowana w celu rozmieszczanie tekstu na wiele sposobów. (Taki zestaw jest także znana jako *wykres buforu*.) Funkcja zwijania tekst programu Visual Studio jest zaimplementowany przy użyciu buforu projekcji, aby ukryć zwiniętego tekstu i edytorze programu Visual Studio dla stron ASP.NET używa projekcji do obsługi osadzony języków, takich jak Visual Basic i C#.  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> Jest tworzona przy użyciu <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Bufor projekcji jest reprezentowana przez uporządkowana sekwencja <xref:Microsoft.VisualStudio.Text.ITrackingSpan> obiektów, które są nazywane *źródła obejmuje*. Zawartość tych zakresów są widoczne jako sekwencja znaków. Bufory tekstu, z których są rysowane zakresów źródła są nazywane *źródła buforów*. Klienci buforu projekcji nie muszą wiedzieć, że różni się od bufora zwykłego tekstu.  
  
 Bufor projekcji nasłuchuje zdarzeń zmiany tekstu w bufory źródła. Gdy tekst w źródle span zmiany, buforu projekcji mapuje współrzędne zmienionego tekstu na jego własnej współrzędne i informuje o zdarzeniach odpowiednie zmiany tekstu. Rozważmy na przykład bufory źródła A i B, których tych zawartości:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Jeśli bufor projekcji P został utworzony z dwa zakresy tekstu, takie, który zawiera wszystkie buforu i innych wszystkie buforu B, P ma następującą zawartość:  
  
```  
P: ABCDEvwxyz  
```  
  
 Jeśli podciąg `xy` , zostaną usunięte z buforu B, a następnie buforu P zgłasza zdarzenie, która wskazuje, czy znaki w miejscach 7 i 8 zostały usunięte.  
  
 Bufor projekcji również można edytować bezpośrednio. Propaguje on edytowanych buforów odpowiedniego źródła. Na przykład jeśli ciąg jest wstawiany do buforu P w pozycji 6 (początkowe położenie znaku "v"), wstawiania jest propagowana do buforu B na pozycji 1.  
  
 Ma ograniczeń dotyczących zakresów źródła, które przyczyniają się do buforu projekcji. Zakresów źródła nie może nakładać się na; lokalizację w buforze projekcji nie można zamapować na więcej niż jedną lokalizację w buforze dowolnego źródła i lokalizację w buforze źródła nie można zamapować na więcej niż jedną lokalizację w buforze projekcji. Circularities nie są dozwolone w relacji bufor źródłowy.  
  
 Zdarzenia są wywoływane, gdy zestaw źródłowy buforuje zmiany buforu projekcji i zestaw źródłowy obejmuje zmiany.  
  
 Bufor elision jest specjalnym rodzajem buforu projekcji. Jest używany głównie dla zwijania i operacji, które rozwijanie i zwijanie bloków tekstu. Bufor elision opiera się na pojedynczy bufor źródłowy, a zakresy w buforze elision muszą być uporządkowane takie same jak są one uporządkowane w bufor źródłowy.  
  
##### <a name="the-buffer-graph"></a>Wykres buforu  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Interfejs umożliwia mapowanie między wykres buforów projekcji. Wszystkie bufory tekstu i projekcji buforów są gromadzone w ukierunkowanego wykresu acyklicznego, podobnie jak w drzewie składni abstrakcyjnej, który jest generowany przez kompilator języka. Wykres jest zdefiniowana przez górny buforu, który może być dowolnym buforu tekstu. Wykres buforu można mapować z punktem w górnym buforu do punktu w buforze źródła lub zakresu w górnym buforu z zestawem zakresów bufor źródłowy. Podobnie możesz mapować punktu lub span z bufora źródłowego do punktu w buforze najwyższego. Wykresy buforu są tworzone za pomocą <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
##### <a name="events-and-projection-buffers"></a>Zdarzenia i buforów projekcji  
 Po zmodyfikowaniu buforu projekcji zmiany są wysyłane z buforu projekcji do buforów, które zależą od niej. Po zmodyfikowaniu są wszystkie bufory pojawienia się zdarzenia zmiany buforu, począwszy od najgłębszym buforu.  
  
###  <a name="outlining"></a> Tworzenie konspektu  
 Tworzenie konspektu jest możliwość rozwiń lub Zwiń różnych bloków tekst w widoku tekstu. Tworzenie konspektu jest zdefiniowany jako typ elementu <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, w taki sam sposób jak skojarzenia są zdefiniowane. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> jest tag, który definiuje obszar tekst, który może zostać rozwinięte lub zwinięte. Aby użyć zwijania, należy zaimportować <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> uzyskanie <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Menedżer zwijania wylicza, zwija i rozwija różnych bloków, które są reprezentowane jako <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> obiekty i odpowiednio informuje o zdarzeniach.  
  
###  <a name="mousebindings"></a> Powiązania myszy  
 Powiązania myszy połączyć ruchów myszy inne polecenia. Powiązania myszy są zdefiniowane przy użyciu <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, i powiązań klucza są zdefiniowane przy użyciu <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Automatycznie tworzy wszystkie powiązania i łączy je z zdarzenia myszy w widoku.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> Interfejs zawiera obsługę zdarzeń procesu przed i po przetwarzaniu zdarzeń myszy. Do realizacji jednej z tych zdarzeń, można zastąpić pewnych metod w <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a> Operacje edytora  
 Operacje Edytor może służyć do automatyzowania interakcji z edytora skryptów lub innych celów. Możesz zaimportować <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> do operacji dostępu na danym <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Można następnie użyć tych obiektów zmodyfikować zaznaczenie, przewiń w widoku lub Przenieś karetkę do różnych części widoku.  
  
###  <a name="intellisense"></a> IntelliSense  
 IntelliSense obsługuje uzupełnianie, podpisu pomocy (nazywany także informacje o parametrach), szybkie informacje i żarówki.  
  
 Uzupełnianie zawiera wyskakujących listę potencjalnych zakończeń nazwy metod, elementy XML i inne elementy programowania lub znaczników. Ogólnie rzecz biorąc gestu użytkownika wywołuje zakończenia sesji. Sesja Wyświetla listę potencjalnych zakończeń, a użytkownik może wybrać jedną lub odrzucić listy. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> Jest odpowiedzialny za tworzenie i wyzwalania <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Oblicza <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> elementów zakończenia sesji.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługa języka i punkty rozszerzenia Edytora](../extensibility/language-service-and-editor-extension-points.md)   
 [Importy edytora](../extensibility/editor-imports.md)