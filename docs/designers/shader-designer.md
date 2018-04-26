---
title: Shader Designer
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.effectdesigner
- vs.graphics.shaderdesigner
ms.assetid: 5db09a16-b82c-4ba3-8ec9-630cdc109397
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09bb6e746c0ace5892dae7db014125c7e6dba92f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="shader-designer"></a>Shader Designer

W tym dokumencie opisano sposób pracy z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] programu do cieniowania Designer do tworzenia, modyfikowania i eksportowanie niestandardowych efektów wizualnych, które są nazywane *programów do cieniowania*.

Projektant programu do cieniowania można użyć do tworzenia niestandardowych efektów wizualnych gry lub aplikacji, nawet jeśli nie znasz programowania w języku HLSL. Można utworzyć programu do cieniowania w projektancie programu do cieniowania, można tylko określić go jako wykresu; oznacza to, Dodaj na powierzchnię projektu *węzłów* które reprezentują danych i operacje, a następnie wprowadź połączenia między nimi, aby zdefiniować sposób operacje przetwarzania danych. W każdym węźle operacji Podgląd obowiązywać do tego punktu podano, dzięki czemu można zwizualizować wyniku. Dane przepływają przez węzły kierunku ostatni węzeł, który reprezentuje dane wyjściowe programu do cieniowania.

## <a name="supported-formats"></a>Obsługiwane formaty

Projektant programu do cieniowania obsługuje tych formatów programu do cieniowania:

|Nazwa formatu|Rozszerzenie pliku|Obsługiwane operacje (w widoku, Edycja, eksportowanie)|
|-----------------|--------------------|-------------------------------------------------|
|Język programu do cieniowania ukierunkowanego wykresu|dgsl|Wyświetl i Edytuj|
|Cieniowania HLSL (kodu źródłowego)|.hlsl|Eksportuj|
|Cieniowania HLSL (kodu bajtowego)|.CSO|Eksportuj|
|Nagłówek C++ (HLSL kodu bajtowego tablica)|.h|Eksportuj|

## <a name="get-started"></a>Rozpocznij

W tej sekcji opisano sposób dodawania DGSL programu do cieniowania do Twojej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu i zawiera podstawowe informacje ułatwiające rozpoczęcie pracy.

### <a name="to-add-a-dgsl-shader-to-your-project"></a>Aby dodać do cieniowania DGSL do projektu

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, który chcesz dodać program do cieniowania, a następnie wybierz **Dodaj**, **nowy element**.

2.  W **Dodaj nowy element** okna dialogowego, w obszarze **zainstalowana**, wybierz pozycję **grafiki**, a następnie wybierz **Visual wykres programu do cieniowania (dgsl)**.

3.  Określ **nazwa** pliku programu do cieniowania i **lokalizacji** znajdzie ma zostać utworzony.

4.  Wybierz **Dodaj** przycisku.

### <a name="the-default-shader"></a>Domyślnego programu do cieniowania

Za każdym razem utworzyć DGSL programu do cieniowania zaczyna się jako minimalny programu do cieniowania, który został właśnie **kolor punktu** węzła, który jest połączony z **ostateczny kolor** węzła. Chociaż ten program do cieniowania jest pełny i funkcjonalności, nie znacznie. W związku z tym pierwszym krokiem tworzenia cieniowania pracy jest często można usunąć **kolor punktu** węzła lub Rozłącz z **ostateczny kolor** węzeł, aby zwolnić miejsce na innych węzłach.

## <a name="work-with-the-shader-designer"></a>Praca z programem Designer programu do cieniowania

W poniższych sekcjach opisano sposób pracy z programów do cieniowania niestandardowych za pomocą projektanta programu do cieniowania.

### <a name="shader-designer-toolbars"></a>Paski narzędzi projektanta programu do cieniowania

Projektant programu do cieniowania, które paski narzędzi zawierają polecenia ułatwiające pracę z DGSL wykresy programu do cieniowania.

Polecenia, które mają wpływ na stan projektanta programu do cieniowania znajdują się na **trybu projektanta programu do cieniowania** paska narzędzi w głównym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] okna. Narzędzia do projektowania i polecenia znajdują się na **Designer programu do cieniowania** narzędzi na powierzchnię projektanta programu do cieniowania.

Oto **trybu projektanta programu do cieniowania** narzędzi:

![Projektant programu do cieniowania modalne paska narzędzi. ] (../designers/media/digit-dsd-modal-toolbar.png "Cyfrę DSD-modalne — pasek narzędzi")

Poniższa tabela zawiera opis elementów na **trybu projektanta programu do cieniowania** narzędzi, które są wymienione w kolejności, w jakiej widnieją od lewej do prawej:

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Wybierz**|Umożliwia interakcję z węzłów i krawędzi na wykresie. W tym trybie można wybierz węzeł i Przenieś lub usuń je, a można ustanowienia krawędzi lub podziel je.|
|**Przesuwanie**|Umożliwia przenoszenie wykres programu do cieniowania względem ramki okna. Aby kadrować, wybierz punkt na powierzchni projektu i przenosić.<br /><br /> W **wybierz** trybie można naciśnij i przytrzymaj klawisz Ctrl, aby aktywować **przesuwanie** tymczasowo w trybie.|
|**Zoom**|Umożliwia wyświetlanie bardziej lub mniej wykres programu do cieniowania szczegółów względem ramki okna. W **powiększenie** tryb, wybierz punkt na powierzchni projektu i następnie przenieś go do prawej w dół, aby powiększyć lub mieszczą się w lewej lub do powiększenia.<br /><br /> W **wybierz** trybie można naciśnij i przytrzymaj klawisz Ctrl, aby powiększyć lub pomniejszyć za pomocą kółka myszy.|
|**Dopasuj widok do rozmiaru**|Wyświetla wykres pełnego programu do cieniowania ramki okna.|
|**Tryb renderowania w czasie rzeczywistym**|Po włączeniu renderowania w czasie rzeczywistym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ponownie rysuje powierzchnię projektu nawet wtedy, gdy jest wykonywana żadna akcja użytkownika. Ten tryb jest przydatny podczas pracy z cieniowaniami zmieniającymi się w czasie.|
|**Podgląd z kuli**|Po włączeniu modelu kuli jest używany do podglądu programu do cieniowania. Można włączyć podgląd tylko jeden kształt naraz.|
|**Podgląd z modułu**|Po włączeniu modelu modułu jest używany do podglądu programu do cieniowania. Można włączyć podgląd tylko jeden kształt naraz.|
|**Wersja zapoznawcza z Cylinder**|Po włączeniu modelu cylinder jest używany do podglądu programu do cieniowania. Można włączyć podgląd tylko jeden kształt naraz.|
|**Podgląd z stożkowy**|Po włączeniu modelu stożek jest używany do podglądu programu do cieniowania. Można włączyć podgląd tylko jeden kształt naraz.|
|**Podgląd z teapot**|Po włączeniu modelu teapot jest używany do podglądu programu do cieniowania. Można włączyć podgląd tylko jeden kształt naraz.|
|**Wyświetl podgląd płaszczyzny**|Po włączeniu modelu płaszczyzny jest używany do podglądu programu do cieniowania. Można włączyć podgląd tylko jeden kształt naraz.|
|**Przybornik**|Alternatywnie pokazuje lub ukrywa **przybornika**.|
|**Właściwości**|Możesz też pokazuje lub ukrywa **właściwości** okna.|
|**Zaawansowane**|Zawiera zaawansowane polecenia i opcje.<br /><br /> **Eksportuj**: włącza eksportu cieniowania w wielu formatach.<br /><br /> **Eksportowanie jako**: eksportuje programu do cieniowania jako albo HLSL kodu źródłowego lub kodu bajtowego cieniowania skompilowany. Aby uzyskać więcej informacji na temat eksportowania programów do cieniowania, zobacz [porady: eksportowanie programu do cieniowania](../designers/how-to-export-a-shader.md).<br /><br /> **Aparaty grafiki**: Umożliwia wybór renderowania, służący do wyświetlania powierzchnię projektu.<br /><br /> **Renderowanie z D3D11**: używa Direct3D 11 do renderowania powierzchnię projektanta programu do cieniowania.<br /><br /> **Renderowanie z D3D11WARP**: używa Direct3D 11 Windows Advanced rasteryzacji platformy (WARP) do renderowania powierzchnię projektanta programu do cieniowania.<br /><br /> **Widok**: włącza zaznaczenie dodatkowe informacje o projektancie programu do cieniowania.<br /><br /> **Szybkość klatek**: po włączeniu Wyświetla bieżąca szybkość klatek w prawym górnym rogu powierzchnię projektu. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę.  Ta opcja jest przydatna podczas włączania **tryb renderowania w czasie rzeczywistym** opcji.|

> [!TIP]
> Możesz wybrać **zaawansowane** przycisk, aby ponownie uruchomienie ostatniego polecenia.

### <a name="work-with-nodes-and-connections"></a>Praca z węzłów i połączeń

Użyj **wybierz** tryb w celu dodawania, usuwania, zmiany położenia, Połącz i skonfiguruj węzłów. Poniżej przedstawiono sposób wykonywania tych podstawowych operacji:

#### <a name="to-perform-basic-operations-in-select-mode"></a>Do wykonywania podstawowych operacji w trybie Select

-   Oto jak:

    -   Aby dodać węzła do wykresu, wybierz je w **przybornika** i przenieść ją na powierzchnię projektu.

    -   Aby usunąć węzeł z wykresu, zaznacz go, a następnie naciśnij klawisz Delete.

    -   Aby zmienić położenie węzła, zaznacz ją, a następnie przenieś go do nowej lokalizacji.

    -   Aby połączyć się z dwóch węzłów, przesuń terminal danych wyjściowych z jednym węzłem do terminal wejścia innego węzła. Mogą być połączone tylko terminale, które mają niezgodne typy. Linii między terminali pokazuje połączenie.

    -   Aby usunąć połączenie, w menu skrótów jedną połączonych terminali, wybierz **przerwanie łączy**.

    -   Aby skonfigurować właściwości węzła, wybierz węzeł, a następnie w **właściwości** okna, określ nowe wartości dla właściwości.

### <a name="preview-shaders"></a>Podgląd programów do cieniowania

Aby ułatwić zrozumienie, jak cieniowania będzie wyświetlana w aplikacji, można skonfigurować, jak jest przeglądany Twoje mocą. Zbliżenie aplikacji, wybierz jeden z kilku kształtów renderowania, skonfiguruj tekstury i innych istotnych parametrach, Włącz animacji skutków na podstawie czasu i Sprawdź Podgląd pod różnymi kątami.

#### <a name="shapes"></a>Kształty

Projektant programu do cieniowania zawiera kształty sześciu — kuli, moduł cylinder, stożek, teapot i płaszczyźnie — której można wyświetlić podgląd programu do cieniowania. W zależności od tego programu do cieniowania niektórych kształtów może ułatwić lepsze podglądu.

Aby wybrać kształt Podgląd na **tryby projektanta programu do cieniowania** narzędzi, wybierz kształt, który ma.

#### <a name="textures-and-material-parameters"></a>Parametry materiału i tekstury
 Wiele programów do cieniowania polegają na tekstury i właściwości materiału, aby wygenerować unikatowego wyglądu dla każdego rodzaju obiektów w aplikacji. Aby wyświetlić programu do cieniowania wyglądu w aplikacji, należy ustawić tekstury i właściwości materiału, które są używane do renderowania w wersji zapoznawczej odpowiadające tekstury i parametrów, których można użyć w aplikacji.

##### <a name="to-bind-a-different-texture-to-a-texture-register-or-to-modify-other-material-parameters"></a>Aby powiązać różnych tekstury rejestr tekstury lub zmodyfikować innych istotnych parametrów

1.  W **wybierz** tryb, wybierz pustym obszarem powierzchnię projektu. Powoduje to **właściwości** okno, aby wyświetlić właściwości globalnego programu do cieniowania.

2.  W **właściwości** okna, określ nowe wartości dla właściwości tekstury i parametrów, które chcesz zmienić.

Poniżej przedstawiono parametry programu do cieniowania, które można modyfikować:

|Parametr|Właściwości|
|---------------|----------------|
|**Texture 1** - **Texture 8**|**Dostęp**: **publicznego** umożliwia właściwości należy ustawić w edytorze modeli; w przeciwnym razie **prywatnej**.<br /><br /> **Nazwa pliku**: Pełna ścieżka pliku tekstury skojarzonego z tym rejestrem tekstury.|
|**Materiał otoczenia**|**Dostęp**: **publicznego** umożliwia właściwości należy ustawić w edytorze modeli; w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**: kolor rozpraszania bieżącego piksela z powodu oświetlenia pośredniego — lub otoczenia —.|
|**Rozpraszania materiału**|**Dostęp**: **publicznego** umożliwia właściwości należy ustawić w edytorze modeli; w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**: kolor opisujący sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego.|
|**Materiał emisji**|**Dostęp**: **publicznego** umożliwia właściwości należy ustawić w edytorze modeli; w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**: udział koloru materiału bieżącego piksela ze względu na własnym podana oświetlenia.|
|**Materiał odblasków**|**Dostęp**: **publicznego** umożliwia właściwości należy ustawić w edytorze modeli; w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**: kolor opisujący sposób odbijania przez bieżący piksel oświetlenia bezpośredniego.|
|**Materiał odblasków zasilania**|**Dostęp**: **publicznego** umożliwia właściwości należy ustawić w edytorze modeli; w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**: wykładnik definiujący intensywność światła odblasków na bieżącego piksela.|

#### <a name="time-based-effects"></a>Wpływ na podstawie czasu

Niektóre programów do cieniowania ma składnik oparte na czasie animuje efekt. Aby pokazać, jak wygląda skutki działania, podglądu musi zostać zaktualizowane na sekundę. Domyślnie podgląd jest aktualizowana tylko w przypadku zmiany programu do cieniowania; Aby zmienić to zachowanie, dzięki czemu można wyświetlić wyniki na podstawie czasu, należy włączyć renderowania w czasie rzeczywistym.

Aby umożliwić renderowanie w czasie rzeczywistym, na pasku narzędzi programu do cieniowania projektanta, wybierz **renderowania w czasie rzeczywistym**.

#### <a name="examine-the-effect"></a>Sprawdź efekt

Wiele programów do cieniowania dotyczy zmiennych, takich jak wyświetlanie kąt lub kierunkową oświetlenia. Aby sprawdzić, jak wpływ reaguje po zmianie tych zmiennych, można swobodnie Obróć kształt Podgląd i sprawdź, zachowania programu do cieniowania.

Obracanie kształtu, naciśnij i przytrzymaj klawisz **Alt**, a następnie wybierz dowolnego punktu na powierzchni projektu i przenieść go.

### <a name="export-shaders"></a>Eksportowanie programów do cieniowania

Przed użyciem programu do cieniowania w aplikacji, należy go wyeksportować w formacie, który obsługuje usługę DirectX.

Programów do cieniowania można wyeksportować jako HLSL kodu źródłowego lub kodu bajtowego cieniowania skompilowany. Kod źródłowy HLSL wyeksportowany do pliku tekstowego, który ma rozszerzenie nazwy pliku .hlsl. Kod bajtowy programu do cieniowania można wyeksportować do pliku binarnego raw, który ma rozszerzenie nazwy pliku .cso lub do pliku nagłówków (.h) C++, który koduje kodu bajtowego cieniowania w tablicy.

Aby uzyskać więcej informacji na temat eksportowania programów do cieniowania, zobacz [porady: eksportowanie programu do cieniowania](../designers/how-to-export-a-shader.md).

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------|------------------------|
|Przełącz się do **wybierz** tryb|Ctrl+G, Gtrl+Q<br /><br /> S|
|Przełącz się do **powiększenie** tryb|Ctrl+G, Ctrl+Z<br /><br /> Z|
|Przełącz się do **przesuwanie** tryb|Ctrl+G, Ctrl+P<br /><br /> K|
|Zaznacz wszystkie|Ctrl+A|
|Usuń bieżące zaznaczenie|Usuwanie|
|Anuluj bieżące zaznaczenie|Escape|
|Powiększanie|Ctrl + obrót kółkiem myszy do przodu<br /><br /> Znak plus (+)|
|Pomniejszanie|Kółka myszy CTRL z poprzednimi wersjami<br /><br /> Znak minusa (-)|
|Kadrować powierzchnię projektu w górę|Obrót kółkiem myszy do tyłu<br /><br /> PageDown|
|Kadrować powierzchnię projektu w dół|Obrót kółkiem myszy do przodu<br /><br /> PageUp|
|Kadrować powierzchni projektu do lewej|Shift+obrót kółkiem myszy do tyłu<br /><br /> Ruch kółkiem myszy w lewo<br /><br /> SHIFT + PageDown|
|Przesuwanie prawo powierzchni projektowej|Shift+obrót kółkiem myszy do przodu<br /><br /> Ruch kółkiem myszy w prawo<br /><br /> SHIFT + PageUp|
|Przenieś fokus klawiatury do innego węzła|Klawisze strzałek|
|Wybierz węzeł, który ma fokus klawiatury (dodaje węzeł do wyboru grupy)|SHIFT + SPACJA|
|Zaznaczenie lub usunięcie zaznaczenia węzła, który ma fokus klawiatury|Ctrl+Spacja|
|Przełącz bieżącym zaznaczeniu (Jeśli nie wybrano żadnych węzłów, wybierz węzeł, który ma fokus klawiatury)|SPACJA|
|Przenieś w górę bieżącego zaznaczenia|Shift+Strzałka w górę|
|Przenieś w dół bieżącego zaznaczenia|Shift+Strzałka w dół|
|Bieżące zaznaczenie w lewo|Shift+Strzałka w lewo|
|Przenieś bieżącego zaznaczenia po prawej|Shift + Strzałka w prawo.|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z zasobami 3D do gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Zawiera omówienie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia służące do pracy z tekstury i obrazów, modeli 3D i efektów programu do cieniowania.|
|[Edytor obrazów](../designers/image-editor.md)|Informacje dotyczące używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytor obrazów do pracy z tekstury i obrazów.|
|[Edytor modelu](../designers/model-editor.md)|Informacje dotyczące używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytorze modeli do pracy z modeli 3D.|