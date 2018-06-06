---
title: Edytor obrazów
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
ms.assetid: fc71d502-c548-4863-8afc-12a1d3ec90d4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 92d82cfaf2f06018ce93e6c1fce1abd0b63809f6
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747313"
---
# <a name="image-editor"></a>Edytor obrazów

Ten dokument zawiera opis sposobu pracy z Visual Studio edytor obrazów do wyświetlania i modyfikowania zasobów tekstury i obrazu.

 Edytor obrazów do pracy z rodzajów sformatowanego formatów obrazów i tekstury, używanych do rozwoju aplikacji DirectX — dotyczy to również obsługa formatów plików obrazów popularnych i kolor kodowania, funkcje, takie jak kanałów alfa i mapowanie MCI i wiele formaty wysokiej skompresowany, przyspieszane sprzętowo tekstury, które obsługuje DirectX.

## <a name="supported-formats"></a>Obsługiwane formaty

Edytor obrazów obsługuje następujące formaty obrazów:

|Nazwa formatu|Rozszerzenie nazwy pliku|
|-----------------|-------------------------|
|Portable Network Graphics|.png|
|JPEG|jpg, JPEG, jpe, jfif|
|Bezpośrednie powierzchni rysowania|.DDS|
|Graphics Interchange Format|.gif|
|Mapy bitowej|BMP, dib|
|Format TIF|tif, TIFF|
|TGA (Targa)|.TGA|

## <a name="get-started"></a>Wprowadzenie

W tej sekcji opisano, jak dodać obraz do projektu programu Visual Studio i skonfigurować go do potrzeb.

### <a name="to-add-an-image-to-your-project"></a>Aby dodać obraz do projektu

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, który chcesz dodać obraz do, a następnie wybierz pozycję **Dodaj**, **nowy element**.

2.  W **Dodaj nowy element** okna dialogowego, w obszarze **zainstalowana**, wybierz pozycję **grafiki**, a następnie wybierz odpowiedni format pliku obrazu. Aby uzyskać informacje o wybieraniu format pliku, w zależności od wymagań zobacz sekcję poniżej.

3.  Określ **nazwa** pliku obrazu i **lokalizacji** znajdzie ma zostać utworzony.

4.  Wybierz **Dodaj** przycisku.

### <a name="choose-the-image-format"></a>Wybierz format obrazu

W zależności od tego, jak zamierzasz użyć obrazu może być odpowiedniejsze od innych określonych formatów plików. Na przykład niektóre formaty mogą nie obsługiwać funkcji, które należy — podobnie jak przezroczystość lub format określonego koloru — lub może nie zapewniać kompresji odpowiedniego dla typu zawartości obrazu zaplanowano.

 Poniższe informacje mogą pomóc Ci wybrać format obrazu, który nie spełnia wymagań.

 **Mapa bitowa (bmp)** format obrazu mapy bitowej. Format nieskompresowanych obrazu, który obsługuje 24-bitowe. Mapa bitowa nie obsługuje przezroczystość.

 **Obraz GIF (.gif)** grafiki Interchange Format (GIF) format obrazu. Format obrazu skompresowane LZW, bezstratny, który obsługuje maksymalnie 256 kolorów. Nie nadaje się do fotografii i obrazów, które znaczną ilość szczegóły koloru, ale zapewnia współczynnik dobrą kompresję niski-obrazach wysoki poziom spójności kolorów.

 **JPG obrazu (jpg)** wspólnego fotograficzne ekspertów Group (JPEG) format obrazu. Format obrazu wysokiej skompresowany, stratna, który obsługuje 24-bitowe i nadaje się do ogólnego przeznaczenia kompresji obrazów, które mają wysoki poziom spójności kolorów.

 **Format PNG (.png)** format obrazu Portable Network Graphics (PNG). Format obrazu średnio skompresowany, bezstratny obsługującego 24-bitowe i alfa przezroczystości. Nadaje się do obrazów fizyczne i sztucznych, ale nie zapewnia współczynnik kompresji jak stratnej formatów, np. JPG lub GIF.

 **Obrazu TIFF (tif)** format obrazu Tagged Image File Format (TIFF lub TIF). Format obrazu elastyczne, która obsługuje kilka systemów kompresji.

 **Tekstura DDS (.dds)** format tekstury DirectDraw Surface (DDS). Format tekstury wysokiej skompresowany, stratnej obsługującego 24-bitowe i alfa przezroczystości. Jego stosunek kompresji może być możliwie jak 8:1. Jest on oparty na tekstury S3 kompresji, co można zdekompresować na sprzęcie grafiki.

 **Obraz TGA (.tga)** Truevision grafiki karty (TGA) format obrazu (znanej także jako Targa). Format obrazu skompresowanej RLE, bezstratny obsługuje zarówno mapowanych na kolor (kolorów palety) lub obrazów kolor bezpośrednio z maksymalnie 24-bitowe i alfa przezroczystości. Nie nadaje się do fotografii i obrazów, które znaczną ilość szczegóły koloru, ale zapewnia współczynnik dobrą kompresję obrazów, które mają długi zakresów kolorów identyczne.

### <a name="configure-the-image"></a>Obraz przedstawiający Konfigurowanie programu

Przed rozpoczęciem pracy z obrazu, który został utworzony, można zmienić konfiguracji domyślnej. Na przykład można zmienić jego wymiary lub format koloru, który go używa. Aby uzyskać informacje o sposobie konfigurowania tych i innych właściwości obrazu, zobacz [właściwości obrazu](#ImageProperties).

> [!NOTE]
>  Aby zapisać swoją pracę, należy ustawić **Format koloru** właściwości, jeśli chcesz użyć formatu określonego koloru. Jeśli format pliku obsługuje kompresję, można dostosować ustawienia kompresji podczas zapisywania pliku po raz pierwszy lub po wybraniu **Zapisz jako**.

## <a name="work-with-the-image-editor"></a>Praca z edytor obrazów

W tej sekcji opisuje sposób modyfikowania tekstury i obrazów za pomocą edytora obrazów.

### <a name="image-editor-toolbars"></a>Paski narzędzi edytora obrazów

Edytor obrazów paski narzędzi zawierają polecenia pomagające w pracy z obrazami.

 Polecenia, które mają wpływ na stan edytor obrazów znajdują się na **tryb edytora obrazów** narzędzi oraz zaawansowane polecenia. Pasek narzędzi znajduje się wzdłuż krawędzi znajdujące się najwyżej powierzchni projektowej edytora obrazów. Narzędzia do rysowania znajdują się na **edytor obrazów** narzędzi wzdłuż lewej krawędzi powierzchni projektowej edytora obrazów.

 Oto **tryb edytora obrazów** narzędzi:

 ![Edytor obrazów modalne paska narzędzi.](../designers/media/digit-tre-modal-toolbar.png)

 Poniższa tabela zawiera opis elementów na **tryb edytora obrazów** narzędzi, które są wymienione w kolejności, w jakiej widnieją od lewej do prawej.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Select**|Umożliwia wybór prostokątny obszar obrazu. Po wybraniu regionu, można wycinanie, kopiowanie, przenoszenia, skalowania, Obróć, przerzuć lub go usunąć. W przypadku aktywnego zaznaczenia narzędzi do rysowania dotyczą tylko wybranego regionu.|
|**Nieprawidłowe zaznaczenie**|Umożliwia wybór nieregularne obszaru obrazu. Po wybraniu regionu, można wycinanie, kopiowanie, przenoszenia, skalowania, Obróć, przerzuć lub go usunąć. W przypadku aktywnego zaznaczenia narzędzi do rysowania dotyczą tylko wybranego regionu.|
|**Wybór Różdżka**|Umożliwia wybór obszaru podobnie kolorze obrazu. *Tolerancji*— to znaczy maksymalną różnicę między sąsiadujących ze sobą kolorów, w których są one uznawane za podobne — można skonfigurować, aby uwzględnić mniejszy lub szerszego zakresu kolorów podobne. Po wybraniu regionu, można wycinanie, kopiowanie, przenoszenia, skalowania, Obróć, przerzuć lub go usunąć. W przypadku aktywnego zaznaczenia narzędzi do rysowania dotyczą tylko wybranego regionu.|
|**Przesuwanie**|Umożliwia przenoszenie obrazu względem ramki okna. W **przesuwanie** tryb, wybierz punkt na obrazie, a następnie przenieś.<br /><br /> Możesz tymczasowo aktywować **przesuwanie** tryb, przytrzymując klawisz Ctrl.|
|**Zoom**|Umożliwia wyświetlanie mniej więcej szczegółów obrazu względem ramki okna. W **powiększenie** tryb, wybierz punkt na obrazie i następnie przenieś go do prawej w dół, aby powiększyć lub mieszczą się w lewej lub do powiększenia.<br /><br /> Można powiększanie lub pomniejszanie, przytrzymując klawisz Ctrl podczas możesz użyć kółka myszy lub kliknij znak Plus (+) lub Minus (-).|
|**Powiększ do rzeczywistego rozmiaru**|Wyświetla obraz przy użyciu relacji między piksele obrazu i pikseli ekranu 1:1.|
|**Dopasuj widok do rozmiaru**|Wyświetla pełny obraz ramki okna.|
|**Powiększ do szerokości**|Wyświetla całą szerokość obrazu ramki okna.|
|**Siatka**|Włącza lub wyłącza siatki, który pokazuje pikseli. Siatki mogą nie być wyświetlane, dopóki powiększenie fragmentu obrazu.|
|**Wyświetl poziom Mipmapy dalej**|Aktywuje następny większy poziom Mipmapy w łańcuchu mapy Mipmapy. Aktywne poziom Mipmapy jest wyświetlany na powierzchni projektu. Ten element jest dostępny tylko dla tekstury, które mają poziom Mipmapy.|
|**Wyświetl poziom Mipmapy poprzedniego**|Aktywuje na następny poziom Mipmapy mniejsze w łańcuchu mapy Mipmapy. Aktywne poziom Mipmapy jest wyświetlany na powierzchni projektu. Ten element jest dostępny tylko dla tekstury, które mają poziom Mipmapy.|
|**Kanał czerwony**<br /><br /> **Kanał zielony**<br /><br /> **Kanał niebieski**<br /><br /> **Kanał alfa**|Włącza lub wyłącza określonych kanałów. **Uwaga:** systematycznie włączając lub wyłączając kanałów koloru, można odizolować problemów, które są powiązane z co najmniej jeden z nich. Na przykład można zidentyfikować niepoprawne alfa przezroczystości.|
|**Tła**|Włącza lub wyłącza ekran za pośrednictwem przezroczysty części obrazu tła. Można skonfigurować sposób wyświetlania tła, wybierając następujące opcje:<br /><br /> **Szachownicy**<br /> Używa kolor zielony oraz kolor tła określony do wyświetlenia w tle jako wzorzec szachownicy. Ta opcja umożliwia sprawić, że więcej widocznej części przezroczystego obrazu.<br /><br /> Białe tło<br /> Używa kolor biały do wyświetlenia w tle.<br /><br /> Czarne tło<br /> Używa kolor czarny do wyświetlenia w tle.<br /><br /> Animacja tła<br /> Przesuwa wzorzec szachownicy powoli. Ta opcja umożliwia sprawić, że więcej widocznej części przezroczystego obrazu.|
|**Właściwości**|Alternatywnie otwiera lub zamyka **właściwości** okna.|
|**Zaawansowane**|Zawiera dodatkowe polecenia i opcje.<br /><br /> **Filtry**<br /><br /> Udostępnia kilka typowych filtry obrazów: **białe czarne**, **rozmycia**, **Brighten**, **Ciemniej**, **wykrywania krawędzi**, **Płaskorzeźba**, **Odwróć kolory**, **Ripple**, **sepię**, i **wyostrzania**.<br /><br /> **Aparaty grafiki**<br /><br /> **Renderowanie z D3D11**<br /> Używa Direct3D 11 do renderowania powierzchni projektowej edytora obrazów.<br /><br /> **Renderowanie z D3D11WARP**<br /> Używa Direct3D 11 Windows Advanced rasteryzacji platformy (WARP) do renderowania powierzchni projektowej edytora obrazów.<br /><br /> **Narzędzia**<br /><br /> **Przerzuć poziomej**<br /> Transposes obraz wokół jego osi poziomej lub x.<br /><br /> **Przerzuć w pionie**<br /> Transposes obraz wokół jego osi pionowej lub y.<br /><br /> **Generowanie Mips**<br /> Generuje poziomów Mipmapy dla obrazu. Jeśli istnieje już poziomów Mipmapy, zostaną ponownie utworzone z największych poziom Mipmapy. Wszelkie zmiany dokonane w mniejszych poziomów Mipmapy zostaną utracone. Aby zapisać poziomów Mipmapy, które zostały wygenerowane, należy użyć formatu .dds do zapisania obrazu.<br /><br /> **Widok**<br /><br /> **Szybkość klatek**<br /> Po włączeniu Wyświetla szybkość klatek w prawym górnym rogu powierzchnię projektu. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę. **Porada:** można **zaawansowane** przycisk, aby ponownie uruchomienie ostatniego polecenia.|

 Oto **edytor obrazów** paska narzędzi.

 ![Pasek narzędzi edytora obrazów](../designers/media/digit-tre-toolbar.png)

 W poniższej tabeli opisano elementy na **edytor obrazów** narzędzi, które są wymienione w kolejności, w jakiej widnieją od góry do dołu.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Ołówka**|Używa zaznaczenie aktywnego koloru do rysowania pociągnięcie aliasu. Można ustawić kolor i grubość pociągnięć w **właściwości** okna.|
|**Pędzel**|Używa zaznaczenie aktywnego koloru do rysowania pociągnięcie wygładzanie. Można ustawić kolor i grubość pociągnięć w **właściwości** okna.|
|**Aerografu**|Używa zaznaczenie aktywnego koloru do rysowania pociągnięcie wygładzanie miesza wraz z obrazu, który staje się bardziej nasycenia w funkcji czasu. Można ustawić kolor i grubość pociągnięć w **właściwości** okna.|
|**Kroplomierz**|Ustawia kolor wybranego piksela zaznaczenie aktywnego koloru.|
|**wypełnienia**|Używa wybór kolorów active w celu wypełnienia obszaru obrazu. Dotyczy region jest zdefiniowany jako pikseli, w których stosowane wypełnienia wraz z każdego piksela podłączonego do niego pikseli tego samego koloru, którym jest ten sam kolor sam. W przypadku zastosowania wypełnienie wewnątrz aktywnego zaznaczenia dotyczy region jest ograniczane przez zaznaczenie.<br /><br /> Domyślnie zaznaczenie aktywnego koloru mieszania wraz z odpowiednim region obrazu zgodnie z jego składnika alfa. Aby użyć opcji aktywnego koloru zastąpić dotyczy regionu, naciśnij i przytrzymaj klawisz Shift, korzystając z narzędzia.|
|**Gumka**|Ustawia pikseli całkowicie przezroczysty kolor, jeśli obraz obsługuje kanał alfa. W przeciwnym razie Ustawia kolor tła active pikseli.|
|**Wiersz**, **prostokąt**, **prostokąt zaokrąglony**, **wielokropka**|Rysuje kształt na obrazie. Można ustawić kolor i szerokość konturu w **właściwości** okna.<br /><br /> Aby narysować podstawowy, który ma taki sam, szerokość i wysokość, naciśnij i przytrzymaj klawisz Shift podczas rysowania.|
|**Tekst**|Używa kolor pierwszego planu zaznaczenia do rysowania tekstu. Kolor tła jest określana przez opcję Kolor tła. Przezroczyste tło wartość alfa zaznaczenia kolor tła musi być 0. Gdy obszaru tekstu jest aktywny, można określić, czy tekst jest rysowany z pociągnięcie wygładzanie i można ustawić tekst **wartość**, **czcionki**, **rozmiar**, styl i —**Bold**, **Italics**, lub **podkreślona**— w **właściwości** okna. Zawartość i wyglądu tekstu jest zakończona po obszaru tekstu nie są już aktywne.|
|**Obróć**|Obraca obraz 90 stopni w prawo.|
|**TRIM**|Przycina obraz do aktywnego zaznaczenia.|

### <a name="work-with-mip-levels"></a>Praca z poziomów Mipmapy

Niektóre formaty obrazów — na przykład DirectDraw Surface (.dds) — Obsługa poziomów Mipmapy przestrzeni tekstury elementu szczegóły na poziomie (LOD). Aby uzyskać informacje dotyczące sposobu generowania i pracować z poziomów Mipmapy, zobacz [jak: utworzyć i zmodyfikować poziomów Mipmapy](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Praca z przezroczystości

Niektóre formaty obrazów — na przykład DirectDraw Surface (.dds) — obsługują przezroczystość. Istnieje kilka sposobów, że przezroczystość może być używany, w zależności od narzędzie, że używasz. Aby określić poziom przezroczystości dla wyboru koloru w **właściwości** ustaw **A** (alfa) składnik wybór kolorów. Oto jak różnych rodzajów sposób stosowania przezroczystość kontroli narzędzi:

|Narzędzie|Opis|
|----------|-----------------|
|**Ołówka**, **pędzla**, **aerografu**, **wiersza**, **prostokąt**, **prostokąt zaokrąglony** , **Elipsy**, **tekstu**|Aby dopasować wybór aktywnego koloru wraz z obrazu, w **właściwości** okna, rozwiń węzeł **kanałów** grupa właściwości i zestaw **rysowania** wyboru na  **Alpha** kanału, a następnie narysuj normalnie.<br /><br /> Rysowanie za pomocą wyboru aktywnego koloru i pozostaw wartość alfa obrazu w miejscu, wyczyść **rysowania** wyboru z **alfa** kanału, a następnie narysuj normalnie.|
|**wypełnienia**|Aby dopasować wybór aktywnego koloru wraz z obrazu, wystarczy wybrać obszar, aby wypełnić.<br /><br /> Aby użyć opcji aktywnego koloru — łącznie z wartością kanału alfa — Aby zastąpić obraz, naciśnij i przytrzymaj klawisz Shift, a następnie wybierz obszar, aby wypełnić.|

### <a name="image-properties"></a>Właściwości obrazu

Można użyć **właściwości** okno, aby określić różne właściwości obrazu. Na przykład można ustawić właściwości szerokości i wysokości rozmiaru.

W poniższej tabeli opisano właściwości obrazu.

|Właściwość|Opis|
|--------------|-----------------|
|Szerokość|Szerokość obrazu.|
|Wysokość|Wysokość obrazu.|
|Bity na piksel|Liczba bitów, które reprezentują każdego piksela. Wartość tej właściwości jest zależna od **Format koloru** obrazu.|
|Zaznaczenie przezroczyste|**Wartość true,** mieszania warstwy wybór wraz z głównym obrazu, na podstawie wartości alfa warstwy wybór; w przeciwnym razie **False**. Ten element jest dostępny tylko dla obrazów, które obsługują alfa.|
|Format|Format koloru z obrazu. Można określić różne formaty kolor, w zależności od format obrazu. Format koloru definiuje liczbę i rodzaj kanałów, które są uwzględniane w obrazie i rozmiaru i kodowania dla różnych kanałów.|
|Poziom mipmapy|Aktywne poziom Mipmapy. Ten element jest dostępny tylko dla tekstury, które mają poziom Mipmapy.|
|Liczba poziom mipmapy|Całkowita liczba poziomów Mipmapy w obrazie. Ten element jest dostępny tylko dla tekstury, które mają poziom Mipmapy.|
|Liczba ramek|Całkowita liczba ramek na obrazie. Ten element jest dostępny tylko dla obrazów, które obsługuje tablic tekstury.|
|Klatka|Bieżącej ramki. Można wyświetlić tylko pierwsza ramka; wszystkie ramki zostaną utracone przy zapisywaniu obrazu.|
|Liczba Wycinek głębokości|Całkowita liczba wycinków głębokości w obrazie. Ten element jest dostępny tylko dla obrazów, które obsługują tekstury woluminu.|
|Wycinek głębokości|Bieżący Wycinek głębokości. Tylko pierwszy wycinek jest możliwy; wszystkie inne wycinki zostaną utracone przy zapisywaniu obrazu.|

> [!NOTE]
>  Ponieważ **obrócić** właściwość ma zastosowanie do wszystkich narzędzi i wybranych regionach, zawsze jest wyświetlany w dolnej części **właściwości** okna oraz inne właściwości narzędzia. **Obróć przez** zawsze jest wyświetlany, ponieważ całego obrazu niejawnie zostaje wybrany, gdy nie ma żadnej wybór ani narzędzie active. Aby uzyskać więcej informacji na temat **obrócić** właściwości, zobacz [właściwości narzędzia](#ToolProperties).

#### <a name="resize-images"></a>Zmiana rozmiaru obrazów

Poniżej przedstawiono dwa sposoby zmiany rozmiaru obrazu. W obu przypadkach edytor obrazów używa interpolacji liniowej bi do próbkowania obrazu.

-   W **właściwości** okna, określ nowe wartości dla **szerokość** i **wysokość** właściwości.

-   Wybierz cały obraz był i umożliwia Zmień rozmiar obrazu obramowania znaczników.

### <a name="work-with-tools"></a>Praca z narzędzia

#### <a name="selected-regions"></a>Wybranych regionów

Opcje edytora obrazów zdefiniuj regionów obrazu, które są aktywne — to znaczy region dotyczy narzędzi i przekształcenia. W przypadku aktywnego zaznaczenia poza wybrany region nie dotyczy większości narzędzi i przekształcenia. Jeśli nie jest aktywne zaznaczenie, całego obrazu jest aktywna.

Większość narzędzi —**ołówka**, **pędzla**, **aerografu**, **wypełnienia**, **Gumka**i podstawowych 2D — i przekształcenia —**Obróć**, **Trim**, **Odwróć kolory**, **Przerzuć w poziomie**, i **Przerzuć w pionie** — ograniczone lub zdefiniowany przez aktywnego zaznaczenia. Jednak niektóre narzędzia —**Kroplomierz** i **tekst**— przekształcenia —**Generowanie Mips**— nie dotyczy żadnych aktywnych wyboru; te narzędzia zawsze działają tak, jakby cały Obraz jest aktywne zaznaczenie.

Podczas wybierania region, możesz naciśnij i przytrzymaj klawisz Shift, aby dokonać wyboru proporcjonalne (kwadrat); w przeciwnym razie zaznaczenia nie jest ograniczane.

##### <a name="resize-selections"></a>Zmień rozmiar zaznaczenia

Po wybraniu regionu lub jego zawartość obrazu można zmienić, zmieniając rozmiar znacznika wyboru. Gdy są zmiany rozmiaru wybranego regionu, służy następujące klawisze modyfikujące do zmiany zachowania wybranego regionu podczas zmiany rozmiaru (naciśnij i przytrzymaj klawisz podczas zmiany rozmiaru).

CTRL&mdash;kopiuje zawartość wybranego regionu, przed jego rozmiar jest zmieniany. Spowoduje to pozostawienie oryginalnego obrazu nienaruszone podczas kopiowania rozmiar jest zmieniany.

SHIFT&mdash;zmienia rozmiar proporcjonalnie do oryginalnego rozmiaru wybranego regionu.

ALT&mdash;zmienia rozmiar obszaru zaznaczenia. Spowoduje to pozostawienie niezmienionej postaci obrazu.

Poniżej przedstawiono kombinacje klawiszy Nieprawidłowy modyfikator:

|CTRL|SHIFT|ALT|Opis|
|----------|-----------|---------|-----------------|
||||Zmienia rozmiar zawartości wybranego regionu.|
||SHIFT||Proporcjonalnie zmienia rozmiar zawartości wybranego regionu.|
|||ALT|Zmienia rozmiar wybranego regionu. Definiuje nowy region zaznaczenia.|
||SHIFT|ALT|Proporcjonalnie zmienia rozmiar wybranego regionu. Definiuje nowy region zaznaczenia.|
|CTRL|||Kopiuje, a następnie zmienia rozmiar zawartości wybranego regionu.|
|CTRL|SHIFT||Kopiuje, a następnie proporcjonalnie zmienia rozmiar zawartości wybranego regionu.|

#### <a name="tool-properties"></a>Właściwości narzędzia

Gdy narzędzie jest zaznaczony, można użyć **właściwości** okno, aby określić szczegółowe informacje o jego wpływ na obrazie. Na przykład można ustawić grubość **ołówka** narzędzia lub kolor **pędzla** narzędzia.

Można ustawić zarówno kolor pierwszego planu i kolor tła. Obsługuje zarówno kanału alfa zapewnienie nieprzezroczystość zdefiniowane przez użytkownika. Ustawienia są stosowane do wszystkich narzędzi. Jeśli używasz myszy, lewego przycisku myszy odpowiada kolor pierwszego planu, a następnie prawym przyciskiem myszy odpowiada kolor tła.

W poniższej tabeli opisano właściwości narzędzia.

|Narzędzie|Właściwości|
|----------|----------------|
|Wszystkie wybrane i narzędzi|**Obróć przez**<br /> Określa, w stopniach, że zaznaczenie lub narzędzia efekt jest obracana wskazówek zegara.|
|**Ołówka**, **pędzla**, **aerografu**, **Gumka**|**Grubość**<br /> Określa rozmiar obszaru, którego dotyczy przez narzędzie.|
|**Tekst**|**Wygładzanie**<br /> Rysuje tekst, który ma wygładzanie krawędzi. Tekst daje płynniejszy wyglądu.<br /><br /> **Wartość**<br /> Tekst, który ma być rysowany.<br /><br /> **Czcionki**<br /> Czcionka używana do rysowania tekstu.<br /><br /> **Rozmiar**<br /> Rozmiar tekstu.<br /><br /> **Bold**<br /> Umożliwia pogrubienie czcionki.<br /><br /> **Italics**<br /> Sprawia, że czcionka kursywą.<br /><br /> **Podkreślone**<br /> Sprawia, że czcionka podkreślony.|
|**2D pierwotnego**|**Wygładzanie**<br /> Rysuje podstawowych, które mają wygładzanie krawędzi. Dzięki temu są płynniejszy wyglądu.<br /><br /> **Grubość**<br /> Określa grubość linii, który wchodzi w skład granicy element pierwotny.<br /><br /> **RADIUS X**<br /> (Tylko zaokrąglony prostokąt) Definiuje zaokrąglania radius górnej i dolnej krawędzi element pierwotny.<br /><br /> **RADIUS Y**<br /> (Tylko zaokrąglony prostokąt) Definiuje zaokrąglania radius lewej i prawej krawędzi typów pierwotnych.|
|**Ołówka**, **pędzla**, **aerografu**, **2D pierwotnego**|**Kanały**<br /> Włącza lub wyłącza konkretnych kanałów koloru do przeglądania i rysowania. Jeśli **widoku** ustawiona dla określonego kanału koloru, tym kanale jest widoczna w obrazie; w przeciwnym razie nie jest widoczne. Jeśli **rysowania** ustawiono dla określonego kanału koloru, że kanał jest wykorzystywanych przez operacje rysowania; w przeciwnym razie, nie jest.|
|**Wybór Różdżka**, **wypełnienia**|**Tolerancja**<br /> Określa maksymalną różnicę między sąsiadujących ze sobą kolorów, w których są one uznawane za podobne, dzięki czemu mniej lub bardziej podobne kolorów są obliczane część dotyczy lub wybranego regionu. Domyślna wartość wynosi 32, co oznacza, że sąsiadujących pikseli 32 odcieni koloru oryginalnego (jaśniejsze i ciemniejsze) są traktowane jako część obszaru.|

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------|------------------------|
|Przełącz się do **wybierz** tryb|S|
|Przełącz się do **powiększenie** tryb|Z|
|Przełącz się do **przesuwanie** tryb|K|
|Zaznacz wszystkie|Ctrl+A|
|Usuń bieżące zaznaczenie|Usuwanie|
|Anuluj bieżące zaznaczenie|Escape|
|Powiększanie|Ctrl + obrót kółkiem myszy do przodu<br /><br /> Ctrl+PageUp<br /><br /> Znak plus (+)|
|Pomniejszanie|Kółka myszy CTRL z poprzednimi wersjami<br /><br /> CTRL-PageDown<br /><br /> Znak minusa (-)|
|Przesuwanie obrazu w górę|Obrót kółkiem myszy do tyłu<br /><br /> PageDown|
|Przesuwanie obrazu w dół|Obrót kółkiem myszy do przodu<br /><br /> PageUp|
|Przesuwanie obrazu w lewo|Shift+obrót kółkiem myszy do tyłu<br /><br /> Ruch kółkiem myszy w lewo<br /><br /> SHIFT + PageDown|
|Przesuwanie obrazu w prawo|Shift+obrót kółkiem myszy do przodu<br /><br /> Ruch kółkiem myszy w prawo<br /><br /> SHIFT + PageUp|
|Powiększ do rzeczywistego rozmiaru|CTRL + 0 (zero).|
|Dopasuj obraz do okna|CTRL + G, Ctrl + F|
|Dopasuj obraz do szerokość okna|CTRL + K, Ctrl + I|
|Przełączanie siatki|CTRL + G, klawiszy Ctrl + G|
|Przytnij obraz do bieżącego zaznaczenia|CTRL + G, Ctrl + C|
|Widok dalej (szczegóły wyższy) poziom Mipmapy|CTRL + K, Ctrl + 6|
|Wyświetl poprzednie (szczegóły niższe) poziom Mipmapy|CTRL + K, Ctrl + 7|
|Kanał czerwony przełączania|CTRL + K, Ctrl + 1|
|Przełącz kolor zielony kanału|CTRL + K, Ctrl + 2|
|Kanał niebieski przełączania|CTRL + K, Ctrl + 3|
|Przełącz kanału alfa (przezroczystości)|CTRL + K, Ctrl + 4|
|Toggle — wzorzec szachownicy alfa|CTRL + G, Ctrl + B|
|Przełącz się do narzędzia wyboru nieregularne|L|
|Przełącz się do wyboru Różdżki|M|
|Przełącz do Ołówek narzędzia|P|
|Przełącz do pędzla narzędzia|B|
|Przełącz do Wypełnianie kolorem — narzędzie|F|
|Przełącz się do narzędzia Gumka|E|
|Przełącz się do narzędzia Tekst|T|
|Przełącz się do narzędzia wyboru koloru (Kroplomierz)|I|
|Przenoszenie aktywnego zaznaczenia i jego zawartość.|Klawisze strzałek.|
|Zmień rozmiar aktywnego zaznaczenia i jego zawartość.|CTRL + STRZAŁKA|
|Przenoszenie aktywnego zaznaczenia, ale nie jego zawartość.|Klawiszy SHIFT + STRZAŁKA|
|Zmień rozmiar aktywnego zaznaczenia, ale nie jego zawartość.|Klawiszy Shift + Ctrl + Strzałka|
|Zatwierdź bieżącej warstwy|Zwraca|
|Zmniejsz grubość narzędzia|[|
|Zwiększ grubość narzędzia|]|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z zasobami 3D do gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Omówienie narzędzia, których można użyć w programie Visual Studio do pracy z zasobów graficznych, takich jak tekstury i obrazów, modeli 3D i efektów programu do cieniowania.|
|[Edytor modelu](../designers/model-editor.md)|Informacje dotyczące używania edytora modelu programu Visual Studio do pracy z modeli 3D.|
|[Projektant cieniowania](../designers/shader-designer.md)|Informacje dotyczące używania projektanta programu do cieniowania programu Visual Studio do pracy z programów do cieniowania.|