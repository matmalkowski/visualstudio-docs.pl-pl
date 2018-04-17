---
title: Edytor kodu
ms.date: 04/12/2018
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ea9217e0b7025c2c802d1a632e16ca30d99336a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="model-editor"></a>Edytor modelu

Tym dokumencie opisano sposób pracy z wyświetlanie, tworzenie i modyfikowanie modeli 3-w edytorze programu Visual Studio modelu.

Edytor modelu może być użyty do tworzenia podstawowych modeli trójwymiarowych od początku lub do wyświetlania i modyfikowania bardziej złożonych modeli trójwymiarowych, utworzonych przy użyciu profesjonalnych narzędzi do modelowania trójwymiarowego. Edytor modelu obsługuje kilka formatów modeli 3-W, które są używane w rozwoju aplikacji DirectX.

## <a name="supported-formats"></a>Obsługiwane formaty

W edytorze modeli obsługiwanych formatach modelu:

|Nazwa formatu|Rozszerzenie pliku|Obsługiwane operacje (Wyświetl, Edytuj, Utwórz)|
|-----------------|--------------------|-------------------------------------------------|
|Plik wymiany AutoDesk FBX|.fbx|Wyświetl, edytuj, utwórz|
|Plik w formacie Collada DAE|.dae|Wyświetl, edytuj (modyfikacje plików Collada DAE są zapisywane przy użyciu formatu FBX).|
|OBJ|.obj|Wyświetl, edytuj (modyfikacje plików OBJ są zapisywane przy użyciu formatu FBX).|

## <a name="get-started"></a>Wprowadzenie

Ta sekcja zawiera opis sposobu dodawania 3-w modelu do projektu programu Visual Studio i przedstawiono podstawowe informacje wymagane do rozpoczęcia pracy.

### <a name="to-add-a-3-d-model-to-your-project"></a>Aby dodać model 3-W do projektu

1. W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, który chcesz dodać obraz do, a następnie wybierz pozycję **Dodaj** > **nowy element**.

2. W **Dodaj nowy element** okna dialogowego, w obszarze **grafiki** kategorii, wybierz opcję **scenę 3D (fbx)**.

   ![Dodaj nowy element w oknie dialogowym z wybrane scenę 3D](media/add-new-3d-scene.png)

3. Wprowadź **nazwa** z pliku modelu, a następnie wybierz **Dodaj**.

> [!NOTE]
> Jeśli nie widzisz **grafiki** kategorii w **Dodaj nowy element** okna dialogowego, należy zainstalować **obrazu i 3W modelu edytory** składnika. Zamknij okno dialogowe, a następnie wybierz **narzędzia** > **Pobierz narzędzia i funkcje** na pasku menu, aby otworzyć **Instalator programu Visual Studio**. Wybierz **pojedynczych składników** , a następnie wybierz **obrazu i 3W modelu edytory** składnika w obszarze **gier i grafiki** kategorii. Wybierz **zmodyfikować**.
>
> ![Składnik edytory modelu obrazu i 3D](media/image-3d-model-editors-component.png)
>
> Jeśli masz **obrazu i 3W modelu edytory** składnika zainstalowana i nadal nie widzisz **grafiki** kategorii szablonów, należy pamiętać, że ta kategoria jest wyświetlana tylko dla określonych typów projektu, na przykład konsoli aplikacje.

### <a name="axis-orientation"></a>Orientacja osi

Visual Studio obsługuje co orientacji 3-osi i ładuje informacje orientacji osi z modelu formatów plików, które obsługują tę. Jeśli nie orientacji osi jest określony, domyślnie Visual Studio używa praworęczny układ współrzędnych. **Wskaźnik osi** zawiera bieżącej orientacji osi w prawym dolnym rogu powierzchnię projektu. Na **wskaźnik osi**, red reprezentuje osi x zielony reprezentuje osi y i niebieski reprezentuje osi z.

### <a name="begin-your-3-d-model"></a>Rozpocznij modelu 3-w

W edytorze modeli każdego nowego obiektu zawsze zaczyna się jako jeden z podstawowych kształtów 3-w — lub *podstawowych*— wbudowanych w edytorze modeli. Aby utworzyć nowe i wyjątkowe obiekty, dodaj prymityw do sceny, a następnie zmień jego kształt, modyfikując jego wierzchołki. W przypadku złożonych kształtów dodaj dodatkowe wierzchołki za pomocą wyciągnięcia lub podpodziału, a następnie zmodyfikuj je. Aby uzyskać informacje o sposobie dodawania obiektu podstawowego do sceny, zobacz [tworzenie i importowanie obiektów 3-](#Adding3DObjects). Aby uzyskać informacje o tym, jak dodać więcej wierzchołków do obiektu, zobacz [modyfikowanie obiektów](#ModifyingObjects).

## <a name="work-with-the-model-editor"></a>Praca z edytorze modeli

W poniższych sekcjach opisano sposób używania Edytora modelu do pracy z modelami trójwymiarowymi.

### <a name="model-editor-toolbars"></a>Paski narzędzi Edytora modelu

Na paskach narzędzi Edytora modelu są dostępne polecenia ułatwiające pracę z modelami 3-W.

Polecenia, które mają wpływ na stan edytorze modeli znajdują się na **tryb edytorze modeli** paska narzędzi w oknie głównym programu Visual Studio. Przy użyciu skryptu polecenia i narzędzia do modelowania znajdują się na **edytorze modeli** narzędzi na powierzchni projektowej edytorze modeli.

Oto **tryb edytorze modeli** narzędzi:

![Podgląd modelu modalne paska narzędzi.](../designers/media/digit-mre-modal-toolbar.png)

Poniższa tabela zawiera opis elementów na **tryb edytorze modeli** narzędzi, które są wymienione w kolejności, w jakiej widnieją od lewej do prawej.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Wybierz**|Umożliwia wybór punktów, krawędzi, powierzchni lub obiektów w scenie, w zależności od aktywnego trybu zaznaczenia.|
|**Przesuwanie**|Umożliwia ruch sceny 3-W względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W **wybierz** trybie można naciśnij i przytrzymaj klawisz Ctrl, aby aktywować **przesuwanie** tymczasowo w trybie.|
|**Zoom**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W **powiększenie** tryb, wybierz punkt sceny i następnie przenieś go do prawej w dół, aby powiększyć lub mieszczą się w lewej lub do powiększenia.<br /><br /> W **wybierz** tryb, możesz można powiększyć lub pomniejszyć za pomocą kółka myszy, gdy naciśnij i przytrzymaj klawisz Ctrl.|
|**Orbita**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:** w tym trybie nie ma efektu, jeśli **rzutowanie** projekcji jest włączona.|
|**Świecie lokalnych**|Po włączeniu tego elementu przekształcenia wybranego obiektu występują w przestrzeni kuli ziemskiej. W przeciwnym razie przekształcenia na zaznaczonym obiekcie występują w przestrzeni lokalnej.|
|**Tryb PIVOT**|Po włączeniu tego elementu przekształcenia mają wpływ na lokalizację i orientację *punktu przestawnego* wybranego obiektu (punktu obrotu definiuje Centrum tłumaczenia, skalowanie i obrót działania). W przeciwnym razie przekształcenia wpływają na położenie i orientację geometrii obiektu względem punktu obrotu.|
|**Oś X blokady**|Ogranicza możliwość manipulacji obiektem tylko do osi x. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Oś Y blokady**|Ogranicza możliwość manipulacji obiektem tylko do osi y. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Blokady Z osi**|Ogranicza możliwość manipulacji obiektem tylko do osi z. Stosuje się tylko w przypadku użycia środkowej części widżetu manipulatora.|
|**Obiekt ramki**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|
|**Widok**|Ustawienie orientacji widoku. Oto dostępne orientacje:<br /><br /> **Front**<br /> Umieszcza widok przed sceną.<br /><br /> **Wstecz**<br /> Umieszcza widok za sceną.<br /><br /> **Po lewej**<br /> Umieszcza widok z lewej strony sceny.<br /><br /> **Prawo**<br /> Umieszcza widok z prawej strony sceny.<br /><br /> **Do góry**<br /> Umieszcza widok nad sceną.<br /><br /> **Dolny**<br /> Umieszcza widok pod sceną. **Uwaga:** jest jedynym sposobem na zmianę kierunku widoku po **rzutowanie** projekcji jest włączona.|
|**Projekcja**|Określa rodzaj rzutowania, który służy do rysowania sceny. Oto dostępne rzuty:<br /><br /> **Perspektywa**<br /> W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.<br /><br /> **Ortogonalnym**<br /> W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Gdy **rzutowanie** projekcji włączone, nie można użyć **orbicie** tryb na pozycji widok.|
|**Styl rysowania**|Określa sposób renderowania obiektów w scenie. Oto dostępne style:<br /><br /> **Szkielety**<br /> Po włączeniu obiekty są renderowane jako szkieletowe.<br /><br /> **Overdraw**<br /> Po włączeniu obiekty są renderowane przy użyciu mieszania sumującego. Umożliwia to wizualizację ilości overdrawingu pojawiającego się w scenie.<br /><br /> **Płaskim cieniowaniem**<br /> Po włączeniu obiekty są renderowane przy użyciu podstawowego, płaskiego zacieniowanego modelu oświetlenia. Umożliwia to łatwiejsze obejrzenie powierzchni obiektu.<br /><br /> Jeśli żadna z tych opcji nie jest włączona, każdy obiekt jest renderowany przy użyciu materiału, który jest do niego stosowany.|
|**Tryb renderowania w czasie rzeczywistym**|Po włączeniu renderowania w czasie rzeczywistym programu Visual Studio ponownie rysuje powierzchnię projektu nawet wtedy, gdy jest wykonywana żadna akcja użytkownika. Ten tryb jest przydatny podczas pracy z cieniowaniami zmieniającymi się w czasie.|
|**Przełączanie siatki**|Po włączeniu tego elementu wyświetlana jest siatka. W przeciwnym razie siatka nie jest wyświetlana.|
|**Przybornik**|Alternatywnie pokazuje lub ukrywa **przybornika**.|
|**Konspekt dokumentu**|Alternatywnie pokazuje lub ukrywa **konspekt dokumentu** okna.|
|**Właściwości**|Alternatywnie pokazuje lub ukrywa **właściwości** okna.|
|**Zaawansowane**|Zawiera zaawansowane polecenia i opcje.<br /><br /> **Aparaty grafiki**<br /><br /> **Renderowanie z D3D11**<br /> Używa programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Renderowanie z D3D11WARP**<br /> Używa platformy WARP (Windows Advanced Rasterization Platform) programu Direct3D 11 do renderowania powierzchni projektowania Edytora modelu.<br /><br /> **Zarządzanie sceny**<br /><br /> **Importujuj**<br /> Importuje obiekty z innego pliku modelu 3-W do bieżącej sceny.<br /><br /> **Dołącz do elementu nadrzędnego**<br /> Ustanawia pierwszy z wielu zaznaczonych obiektów jako nadrzędny dla pozostałych zaznaczonych obiektów.<br /><br /> **Odłącz od elementu nadrzędnego**<br /> Odłącza zaznaczony obiekt od jego obiektu nadrzędnego. Wybrany obiekt staje się *główny obiekt* sceny. Obiekt główny nie ma obiektu nadrzędnego.<br /><br /> **Tworzenie grupy**<br /> Grupuje zaznaczone obiekty jako obiekty równorzędne.<br /><br /> **Scalanie obiektów**<br /> Łączy zaznaczone obiekty w jeden obiekt.<br /><br /> **Utwórz nowy obiekt z wybranej części wielokąta**<br /> Usuwa z bieżącego obiektu wybrane powierzchnie i dodaje do sceny nowy obiekt zawierający te powierzchnie.<br /><br /> **Narzędzia**<br /><br /> **Przerzuć rozwiązanie wielokąta**<br /> Przerzuca wybrane wielokąty, tak że kolejność ich wierzchołków i normalnych powierzchni jest odwrócona.<br /><br /> **Usuń wszystkie animacji**<br /> Usuwa dane animacji z obiektów.<br /><br /> **Przeprowadzić triangulację**<br /> Konwertuje zaznaczony obiekt na trójkąty.<br /><br /> **Widok**<br /><br /> Odrzucanie tylnych ścian<br /> Włącza lub wyłącza odrzucanie tylnych ścian.<br /><br /> **Szybkość klatek**<br /> Wyświetla szybkość klatek w prawym górnym rogu powierzchni projektowej. Szybkość odtwarzania to liczba ramek wyświetlanych na sekundę.<br /><br /> Ta opcja jest przydatna podczas włączania **tryb renderowania w czasie rzeczywistym** opcji.<br /><br /> **Pokaż wszystko**<br /> Pokazuje wszystkie obiekty w scenie. Spowoduje to zresetowanie **Hidden** właściwości obiektu do **False**.<br /><br /> **Pokaż wektorów Face**<br /> Pokazuje normalną każdej powierzchni.<br /><br /> **Pokaż brak materiałów**<br /> Wyświetla specjalną teksturę na obiektach, które nie mają przypisanych materiałów.<br /><br /> **Pokaż Pivot**<br /> Włącza lub wyłącza wyświetlanie znacznika osi 3-W w punkcie obrotu aktywnego zaznaczenia.<br /><br /> **Wyświetlanie węzłów symbolu zastępczego**<br /> Pokazuje węzły zastępcze. Węzeł zastępczy jest tworzony podczas grupowania obiektów.<br /><br /> **Pokaż wierzchołka zwykłego**<br /> Pokazuje normalną każdego wierzchołka. **Porada:** można **skryptów** przycisk, aby ponownie uruchomić skrypt ostatni.|

Oto **edytorze modeli** narzędzi:

![Pasek narzędzi podglądu modelu](../designers/media/digit-mre-toolbar.png)

W następnej tabeli opisano elementy na **edytorze modeli** narzędzi, które są wymienione w kolejności, w jakiej widnieją od góry do dołu.

|Element paska narzędzi|Opis|
|------------------|-----------------|
|**Przetłumacz**|Przenosi zaznaczenie.|
|**Skali**|Zmienia rozmiar zaznaczenia.|
|**Obróć**|Obraca zaznaczenie.|
|**Wybierz punkt**|Ustawia **tryb zaznaczania** aby wybrać poszczególne punkty obiektu.|
|**Wybierz krawędzi**|Ustawia **tryb zaznaczania** aby zaznaczyć krawędź (linii między dwiema wierzchołków) do obiektu.|
|**Wybierz krój**|Ustawia **tryb zaznaczania** wybierz krój obiektu.|
|**Wybierz obiekt**|Ustawia **tryb zaznaczania** Zaznaczanie całego obiektu.|
|**Wyciągnięcie**|Tworzy dodatkową powierzchnię i łączy ją z wybraną powierzchnią.|
|**Podziału**|Dzieli każdą wybraną powierzchnię na wiele powierzchni. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni.|

### <a name="control-the-view"></a>Kontrolki widoku

Scena 3-W jest renderowana zgodnie z widokiem. Można go traktować jako wirtualną kamerę, która ma pozycję i orientację. Aby zmienić położenie i ukierunkowanie, użyj elementów sterujących widok na **tryb edytorze modeli** paska narzędzi.

W poniższej tabeli opisano formanty widoku podstawowego.

|Formant widoku|Opis|
|------------------|-----------------|
|**Przesuwanie**|Umożliwia ruch sceny 3-W względem ramki okna. Aby panoramować, wybierz punkt na scenie i przesuwaj go.<br /><br /> W **wybierz** trybie można naciśnij i przytrzymaj klawisz Ctrl, aby aktywować **przesuwanie** tymczasowo w trybie.|
|**Zoom**|Umożliwia wyświetlanie większej lub mniejszej ilości szczegółów sceny względem ramki okna. W **powiększenie** tryb, wybierz punkt sceny i następnie przenieś go do prawej w dół, aby powiększyć lub mieszczą się w lewej lub do powiększenia.<br /><br /> W **wybierz** tryb, możesz można powiększyć lub pomniejszyć za pomocą kółka myszy, gdy naciśnij i przytrzymaj klawisz Ctrl.|
|**Orbita**|Pozycjonuje wyświetlanie na kolistej ścieżce wokół zaznaczonego obiektu. Jeśli żaden obiekt nie jest zaznaczony, ścieżka zostanie wyśrodkowana na punkt źródłowy sceny. **Uwaga:** w tym trybie nie ma efektu, jeśli **rzutowanie** projekcji jest włączona.|
|**Obiekt ramki**|Umieszcza zaznaczony obiekt w ramce, tak aby znajdował się w środku widoku.|

Widok jest ustanowiony przez wirtualną kamerę, ale jest również określony przez rzutowanie. Rzut definiuje sposób translacji kształtów i obiektów w widoku na piksele na powierzchni projektowej. Na **edytorze modeli** narzędzi, można wybrać jedną **perspektywy** lub **rzutowanie** projekcji.

|Rzut|Opis|
|----------------|-----------------|
|**Perspektywa**|W rzutowaniu perspektywicznym obiekty, które są oddalone od punktu obserwacji, wyglądają na mniejsze, i ostatecznie zbiegają się do jednego punktu w odległości.|
|**Ortogonalnym**|W rzutowaniu prostopadłym obiekty wydają się mieć taki sam rozmiar, niezależnie od ich odległości od punktu obserwacji. Nie są wyświetlane żadne zbieżności. Gdy **rzutowanie** projekcji włączone, nie można użyć **orbicie** trybu arbitralnie pozycji widok.|

Przydatne może okazać się wyświetlenie sceny trójwymiarowej ze znanego położenia i kąta, na przykład, gdy chcesz porównać dwie podobne sceny. W tym scenariuszu Edytor modelu zawiera kilka wstępnie zdefiniowanych widoków. Aby użyć wstępnie zdefiniowanego widoku na **tryb edytorze modeli** narzędzi wybierz **widoku**, a następnie wybierz wstępnie zdefiniowanego widoku mają — przodu Wstecz, lewo, prawo, top lub bottom. W tych widokach kamera wirtualna patrzy bezpośrednio na źródło sceny. Na przykład, jeśli wybierzesz **góry widoku**, aparat wirtualnego analizuje pochodzenia sceny z bezpośrednio nad nim.

### <a name="view-additional-geometry-details"></a>Wyświetl geometrii dodatkowe szczegóły

Aby lepiej zrozumieć obiekt lub scenę 3-W, można wyświetlić dodatkowe szczegóły geometrii, np. normalne wierzchołka, normalne powierzchni, punkty obrotu aktywnego zaznaczenia i inne szczegóły. Aby włączyć lub wyłączyć je na **edytorze modeli** narzędzi wybierz **skryptów**, **widoku**, a następnie wybierz odpowiedni.

### <a name="create-and-import-3-d-objects"></a>Tworzenie i importowanie obiektów 3-w

Aby dodać wstępnie zdefiniowany kształt 3-sceny w **przybornika**, wybierz jedną, a następnie przenieś go do powierzchni projektu. Nowe kształty są umieszczane w źródle sceny. Edytor modelu udostępnia siedmiu kształtów: **stożkowy**, **modułu**, **Cylinder**, **dysku**, **płaszczyzny**,  **Kuli**, i **Teapot**.

Do zaimportowania 3-obiekt z pliku, na **edytorze modeli** narzędzi wybierz **zaawansowane**, **zarządzania sceny**, **zaimportować**, a następnie określ plik, który chcesz zaimportować.

### <a name="transform-objects"></a>obiekty przekształceń

Możesz *przekształcenie* obiektu przez zmianę jego **obrotu**, **skali**, i **tłumaczenia** właściwości. *Obracanie* kieruje użytkowników obiektu przez zastosowanie kolejnych obrotów wokół osi x, y i zdefiniowanych przez punktu obrotu osi z. Każda specyfikacja obrotu ma trzy składniki — x, y i z, w tej kolejności — i składniki te określone są w stopniach. **Skalowanie** zmienia rozmiar obiektu rozciągnięty przez określony współczynnik wzdłuż osi co najmniej jeden skupia się na punktu obrotu. *Tłumaczenie* lokalizuje obiektu przestrzeni 3-wymiarową względem jego elementu nadrzędnego, a nie punktu obrotu.

Można przekształcić obiekt za pomocą narzędzi do modelowania lub przez ustawienie właściwości.

#### <a name="to-transform-an-object-by-using-modeling-tools"></a>Aby przekształcić obiekt za pomocą narzędzi do modelowania

1. W **wybierz** tryb, wybierz obiekt, którego chcesz transformacji. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.

2. Na **edytorze modeli** narzędzi wybierz **Przetłumacz**, **skali**, lub **Obróć** narzędzia. Dla wybranego obiektu pojawia się manipulator przesunięcia, skalowania lub obrotu.

3. Użyj manipulatora do wykonania przekształcenia. Dla przekształceń przesunięcia i skalowania manipulator jest wskaźnikiem osi. Jednocześnie można zmienić jedną oś lub można zmienić wszystkie osie jednocześnie przy użyciu białego sześcianu w środku wskaźnika. Dla obrotu manipulator to sfera wykonana z kolorowych okręgów, które odpowiadają osi x (czerwony), osi y (zielony) i osi z (niebieski). Należy zmienić każdą z osi osobno, aby utworzyć żądany obrót.

#### <a name="to-transform-an-object-by-setting-its-properties"></a>Aby przekształcić obiekt przez ustawienie jego właściwości

1. W **wybierz** tryb, wybierz obiekt, który ma być transformacji. Nakładka szkieletowa wskazuje, że obiekt jest wybrany.

2. W **właściwości** okna, określ wartości dla **obrotu**, **skali**, i **tłumaczenia** właściwości.

    > [!IMPORTANT]
    > Dla **obrotu** właściwości, określić stopień obrót wokół każdego z trzech osi. Obroty są stosowane w określonej kolejności, należy zapewnić, że odbywają się najpierw względem osi x, a następnie osi y i osi z.

Za pomocą narzędzi modelowania, przekształcenia można tworzyć szybko, ale nie precyzyjnie. Za pomocą ustawiania właściwości obiektu przekształcenia można określić precyzyjnie, ale nie szybko. Zalecane jest używanie narzędzi do modelowania, aby uzyskać „wystarczająco bliskie” przekształcenia, a następnie dostosować wartości właściwości.

Jeśli nie chcesz używać manipulatorów, można włączyć tryb dowolnego kształtu. Na **edytorze modeli** narzędzi wybierz **skryptów**, **narzędzia**, **manipulowania dowolne** włączyć (lub wyłączyć) dowolnych tryb. W trybie dowolnego kształtu można rozpocząć manipulowanie w dowolnym punkcie powierzchni projektowej zamiast w punkcie na manipulatorze. W trybie dowolnego kształtu możesz ograniczyć zmiany do niektórych osi, blokując te, których nie chcesz zmienić. Na **tryb edytorze modeli** narzędzi wybrać dowolną kombinację **X blokady**, **Y blokady**, i **blokady Z** przycisków.

Może się to okazać przydatne w pracy z obiektami za pomocą przyciągania do siatki. Na **tryb edytorze modeli** narzędzi wybierz **przyciąganie** włączyć (lub wyłączyć) przyciąganie do siatki. Po włączeniu przyciągania do siatki, przekształcenia przesunięcia, obrotu i skalowania są ograniczone do wstępnie zdefiniowanych przyrostów.

### <a name="work-with-the-pivot-point"></a>Praca z punktu przestawnego

Punkt obrotu obiektu definiuje środek obrotu i skalowania. Można zmienić punkt obrotu obiektu, aby zmienić wpływ przekształceń obrotu i skalowania na obiekt. Na **tryb edytorze modeli** narzędzi wybierz **tryb Pivot** do trybu pivot Włącz (lub wyłączona). Po włączeniu trybu obrotu, w punkcie obrotu wybranego obiektu pojawia się mały wskaźnik osi. Następnie można użyć **tłumaczenia** i **obrotu** narzędzi do manipulacji punktu obrotu.

Aby demonstracyjne, który przedstawia sposób użycia punktu obrotu, zobacz [porady: modyfikowanie punktu obrotu 3-w modelu](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).

### <a name="world-and-local-modes"></a>Tryby lokalne i świata

Translacja i obrotu może wystąpić w jednym współrzędnych lokalnych (lub *lokalnego ramki z odwołania*) obiektu lub w układzie współrzędnych świata (lub *world ramki z odwołania*). Światowa ramka odniesienia nie zależy od obrotu obiektu. Tryb lokalny jest opcją domyślną. Aby włączyć (lub wyłączyć) world trybie, na **tryb edytorze modeli** narzędzi wybierz **WorldLocal** przycisku.

### <a name="modify-objects"></a>Modyfikowanie obiektów

Kształt obiektu 3-W można zmienić, przenosząc lub usuwając jego wierzchołki, krawędzie i powierzchnie. Domyślnie w edytorze modeli jest w *tryb obiektu*, dzięki czemu można wybrać i Przekształć całą obiektów. Aby wybrać punkty, krawędzie lub powierzchnie, wybierz odpowiedni tryb wyboru. Na **tryb edytorze modeli** narzędzi wybierz **tryby wyboru**, a następnie wybierz żądany tryb.

 Dodatkowe wierzchołki można utworzyć za pomocą wyciągnięcia lub podpodziału. Wyciągnięcie duplikuje wierzchołki powierzchni (zestaw współpłaszczyznowych wierzchołków), które pozostają połączone przez zduplikowane wierzchołki. Podpodział dodaje wierzchołki, aby utworzyć wiele płaszczyzn tam, gdzie do tej pory była jedna. Aby utworzyć nowe powierzchnie, dodawane są nowe wierzchołki — jeden w środku oryginalnej powierzchni i jeden w połowie każdej krawędzi — które następnie są łączone z oryginalnymi wierzchołkami. Liczba dodanych powierzchni jest równa liczbie krawędzi oryginalnej powierzchni. W obu przypadkach można przesuwać, obracać i skalować nowe wierzchołki, aby zmienić geometrię obiektu.

#### <a name="to-extrude-a-face-from-an-object"></a>Aby wyciągnąć powierzchnię z obiektu

1. W trybie zaznaczania powierzchni zaznacz powierzchnię, którą chcesz wyciągnąć.

2. Na **edytorze modeli** narzędzi wybierz **skryptów**, **narzędzia**, **wyciągnięcie**.

#### <a name="to-subdivide-faces"></a>Aby podpodzielić twarze

1. W trybie zaznaczania powierzchni zaznacz powierzchnie, które chcesz podzielić na mniejsze. Ponieważ podpodział tworzy nowe dane krawędzi, podpodział jednocześnie wszystkich powierzchni zapewnia bardziej spójne wyniki, gdy powierzchnie sąsiadują.

2. Na **edytorze modeli** narzędzi wybierz **skryptów**, **narzędzia**, **Subdivide**.

 Można również przeprowadzać triangulację powierzchni, scalać obiekty i konwertować wielokątne zaznaczenia na nowe obiekty. Triangulacja tworzy dodatkowe krawędzie, w taki sposób, że powierzchnia nietrójkątna jest konwertowana na optymalną liczbę trójkątów; jednak nie zapewnia to dodatkowych szczegółów geometrycznych. Scalanie łączy zaznaczone obiekty w jeden obiekt. Nowe obiekty można tworzyć z zaznaczenia wielokątnego.

#### <a name="to-triangulate-a-face"></a>Aby przeprowadzić triangulację powierzchni

1. W trybie zaznaczania powierzchni zaznacz powierzchnię, dla której chcesz dokonać triangulacji.

2. Na **edytorze modeli** narzędzi wybierz **skryptów**, **narzędzia**, **Triangulate**.

#### <a name="to-merge-objects"></a>Aby scalić obiekty

1. W trybie zaznaczania obiektów zaznacz obiekty, które chcesz scalić.

2. Na **edytorze modeli** narzędzi wybierz **skryptów**, **narzędzia**, **scalania obiektów**.

#### <a name="to-create-an-object-from-a-polygon-selection"></a>Aby utworzyć obiekt z zaznaczenia wielokątnego

1. W trybie zaznaczania powierzchni zaznacz powierzchnie, z których chcesz utworzyć nowy obiekt.

2. Na **edytorze modeli** narzędzi wybierz **skryptów**, **narzędzia**, **utworzyć nowy obiekt z wybranej części wielokąta**.

### <a name="work-with-materials-and-shaders"></a>Praca z materiałami i programów do cieniowania

Wygląd obiektu zależy od interakcji oświetlenia i materiału obiektu w scenie. Materiały są definiowane przez właściwości, które opisują, jak powierzchnia reaguje na różne typy światła, oraz przez program do cieniowania, który oblicza końcowy kolor każdego piksela na powierzchni obiektu na podstawie informacji o oświetleniu, map tekstur, map normalnych i innych danych.

Edytor modelu zawiera następujące materiały domyślne:

|Materiał|Opis|
|--------------|-----------------|
|Nieoświetlona|Renderuje powierzchnię bez żadnego symulowanego oświetlenia.|
|Lambert|Renderuje powierzchnię z symulowanym oświetleniem otoczenia i oświetleniem rozproszonym.|
|Phong|Renderuje powierzchnię z symulowanym oświetleniem otoczenia, oświetleniem rozproszonym i światłem odbitym.|

Każdy z tych materiałów stosuje jedną teksturę na powierzchni obiektu. Można ustawić różne tekstury dla każdego obiektu, który używa materiału.

Aby zmodyfikować sposób reakcji określonego obiektu na różne źródła światła w scenie, możesz zmienić właściwości oświetlenia materiału niezależnie od innych obiektów używających materiału. W tej tabeli opisano typowe właściwości oświetlenia:

|Właściwość oświetlenia|Opis|
|-----------------------|-----------------|
|Otoczenie|Opisuje wpływ oświetlenia otoczenia na powierzchnię.|
|Rozproszone|Opisuje wpływ światła kierunkowego i punktowego na powierzchnię.|
|Emisyjne|W tym artykule opisano, jak powierzchnia emituje światło niezależne od innego oświetlenia.|
|Odbite|Opisuje odbijanie światła kierunkowego i punktowego przez powierzchnię.|
|Siła odbicia|Opisuje szerokość i natężenie odbitego światła.|

W zależności od tego, co obsługuje materiał, można zmienić jego właściwości oświetlenia, tekstury i inne dane. W **wybierz** tryb, wybierz obiekt materiałów, których chcesz zmienić, a następnie w **właściwości** Zmień **MaterialAmbient**,  **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower**, lub innych dostępnych właściwości. Materiał mogą uwidaczniać maksymalnie osiem tekstury, którego właściwości są nazywane sekwencyjnie od **Texture1** do **Texture8**.

Aby usunąć wszystkie materiały z obiektu na **edytorze modeli** narzędzi wybierz **skryptów**, **materiałów**, **Usuń materiałów**.

Można użyć **Designer programu do cieniowania** można utworzyć niestandardowego programu do cieniowania materiały, które można zastosować do obiekty sceny 3. Aby uzyskać informacje o sposobie tworzenia niestandardowych programu do cieniowania materiałów, zobacz [Designer programu do cieniowania](../designers/shader-designer.md). Informacji dotyczących sposobu stosowania niestandardowego programu do cieniowania materiały do obiektu, zobacz [porady: dotyczą programu do cieniowania 3-w modelu](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

### <a name="scene-management"></a>Zarządzanie sceną

Scenami można zarządzać jako hierarchią obiektów. Gdy wiele obiektów jest rozmieszczonych w hierarchii, każde przesunięcie, skalowanie lub obrót węzła nadrzędnego wpływa również na jego elementy podrzędne. Jest to przydatne w celu konstruowania złożonych obiektów lub scen z bardziej podstawowych obiektów.

Można użyć **konspekt dokumentu** okno, aby wyświetlić hierarchii sceny i wybierz węzeł sceny. Po wybraniu węzła w konspekcie można użyć **właściwości** okno, aby zmodyfikować jego właściwości.

Hierarchię obiektów można utworzyć albo poprzez określenie jednego z nich jako element nadrzędny wobec innych, albo grupując je jako elementy równorzędne w obszarze węzła zastępczego działającego jako nadrzędny.

#### <a name="to-create-a-hierarchy-that-has-a-parent-object"></a>Aby utworzyć hierarchię zawierającą obiekt nadrzędny

1. W **wybierz** tryb, wybierz co najmniej dwa obiekty. Pierwszy wybrany będzie obiektem nadrzędnym.

2. Na **edytorze modeli** narzędzi wybierz **skryptów**, **zarządzania sceny**, **dołączyć do elementu nadrzędnego**.

#### <a name="to-create-a-hierarchy-of-sibling-objects"></a>Aby utworzyć obiekty hierarchii elementów równorzędnych

1. W **wybierz** tryb, wybierz co najmniej dwa obiekty. Obiekt zastępczy jest tworzony i staje się ich obiektem nadrzędnym.

2. Na **edytorze modeli** narzędzi wybierz **skryptów**, **zarządzania sceny**, **Utwórz grupę**.

Edytor modelu używa białego szkieletu do identyfikacji pierwszego wybranego obiektu, który staje się nadrzędny. Inne obiekty w zaznaczeniu mają niebieski szkielet. Domyślnie węzły zastępcze nie są wyświetlane. Do wyświetlania węzłów symbolu zastępczego na **edytorze modeli** narzędzi wybierz **skryptów**, **zarządzania sceny**, **Pokaż węzłów symbolu zastępczego**. Z węzłami zastępczymi można pracować tak samo, jak z obiektami bez obiektu zastępczego.

Aby usunąć skojarzenie nadrzędny podrzędny między dwoma obiektami, wybierz obiekt podrzędny, a następnie na **edytorze modeli** narzędzi wybierz **skryptów**, **zarządzania sceny**, **Odłączyć od nadrzędnego**. Po odłączeniu elementu nadrzędnego od obiektu podrzędnego obiekt podrzędny staje się obiektem głównym w scenie.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

|Polecenie|Skróty klawiaturowe|
|-------------|------------------------|
|Przełącz się do **wybierz** tryb|Ctrl+G, Gtrl+Q<br /><br /> S|
|Przełącz się do **powiększenie** tryb|Ctrl+G, Ctrl+Z<br /><br /> Z|
|Przełącz się do **przesuwanie** tryb|Ctrl+G, Ctrl+P<br /><br /> K|
|Zaznacz wszystkie|Ctrl+A|
|Usuń bieżące zaznaczenie|Usuwanie|
|Anuluj bieżące zaznaczenie|Escape|
|Powiększanie|Obrót kółkiem myszy do przodu<br /><br /> Ctrl + obrót kółkiem myszy do przodu<br /><br /> Shift+obrót kółkiem myszy do przodu<br /><br /> Ctrl+PageUp<br /><br /> Znak plus (+)|
|Pomniejszanie|Obrót kółkiem myszy do tyłu<br /><br /> CTRL + obrót kółkiem myszy do tyłu<br /><br /> Shift+obrót kółkiem myszy do tyłu<br /><br /> Ctrl+PageDown<br /><br /> Znak minusa (-)|
|Przesunięcie kamery do góry|PageDown|
|Przesunięcie kamery w dół|PageUp|
|Przesunięcie kamery w lewo|Ruch kółkiem myszy w lewo<br /><br /> Ctrl+PageDown|
|Przesunięcie kamery w prawo|Ruch kółkiem myszy w prawo<br /><br /> Ctrl+PageDown|
|Widok góry modelu|Ctrl+L, Ctrl+T<br /><br /> T|
|Widok dołu modelu|Ctrl+L, Ctrl+U|
|Widok lewej strony modelu|Ctrl+L, Ctrl+L|
|Widok prawej strony modelu|Ctrl+L, Ctrl+R|
|Widok przodu modelu|Ctrl+L, Ctrl+F|
|Widok tyłu modelu|Ctrl+L, Ctrl+B|
|Umieść obiekt w ramce w oknie|F|
|Przełącz tryb szkieletowy|Ctrl+L, Ctrl+W|
|Przełącz przyciąganie do siatki|Ctrl+G, Ctrl+N|
|Przełącz tryb obracania|Ctrl+G, Ctrl+V|
|Przełącz ograniczenie osi x|Ctrl+L, Ctrl+X|
|Przełącz ograniczenie osi y|Ctrl+L, Ctrl+Y|
|Przełącz ograniczenie osi z|Ctrl+L, Ctrl+Z|
|Przełącz do trybu przesunięcia|Ctrl+G, Ctrl+W<br /><br /> W|
|Przełącz do trybu skalowania|Ctrl+G, Ctrl+E<br /><br /> E|
|Przełącz do trybu obrotu|Ctrl+G, Ctrl+R<br /><br /> R|
|Przełącz do trybu zaznaczania punktu|Ctrl+L, Ctrl+1|
|Przełącz do trybu zaznaczania krawędzi|Ctrl+L, Ctrl+2|
|Przełącz do trybu zaznaczania powierzchni|Ctrl+L, Ctrl+3|
|Przełącz do trybu zaznaczania obiektu|Ctrl+L, Ctrl+4|
|Przełącz do trybu orbity (kamery)|Ctrl+G, Ctrl+O|
|Wybierz następny obiekt w scenie|Tab|
|Wybierz poprzedni obiekt w scenie|Shift+Tab|
|Manipuluj zaznaczonym obiektem za pomocą bieżącego narzędzia.|Klawisze strzałek|
|Dezaktywuj bieżący manipulator|Q|
|Obracanie kamery|Alt + przeciągnięcie lewym przyciskiem myszy|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z obiektami 3-D do gier i aplikacji](../designers/working-with-3-d-assets-for-games-and-apps.md)|Omówienie narzędzia programu Visual Studio, które służą do pracy z zasobów graficznych, takich jak tekstury i obrazów, 3-modele i programu do cieniowania efekty.|
|[Edytor obrazów](../designers/image-editor.md)|Informacje dotyczące używania edytora obrazów programu Visual Studio do pracy z tekstury i obrazów.|
|[Projektant cieniowania](../designers/shader-designer.md)|Informacje dotyczące używania projektanta programu do cieniowania programu Visual Studio do pracy z programów do cieniowania.|