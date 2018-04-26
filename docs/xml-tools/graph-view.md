---
title: Widok wykresu projektanta schematu XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab09bec8f2fc7d75ab21c3635f34069ad613b3e3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="graph-view"></a>Widok wykresu

Widok wykresu zawiera graficzną reprezentację węzłów globalne schematu i relacji między węzłami. Należy pamiętać, że w widoku wykresu nie zezwala na zmienianie układu schematu ustawiony na powierzchni projektu. Widok wykresu zawiera również narzędzi Projektanta schematu XML i na pasku stron nadrzędnych.

 Na poniższej ilustracji przedstawiono widok wykresu z sześciu węzłów globalnych na jego powierzchnię.

 ![Widok wykresu projektanta schematu XML](../xml-tools/media/xsddesigner_graphview.gif "XSDDesigner_GraphView")

## <a name="design-surface"></a>Dzięki powierzchni projektowej

 Obszar projektu w widoku wykresu wyświetla zawartość [obszaru roboczego projektanta schematu XML](../xml-tools/xml-schema-designer-workspace.md). Jeśli obszar roboczy zawiera węzły globalnych z zestawu schematów, węzły są wyświetlane na powierzchni projektowej widok wykresu i strzałki są rysowane między węzłami, które mają relacji.

 Dwukrotne kliknięcie węzła w widoku wykresu pojawią się edytora XML.

 Aby usunąć wybrane węzły z obszaru roboczego, użyj narzędzi Projektanta XSD lub klawisz DELETE.

 Jeśli powierzchnię projektu jest pusta, zostaną wyświetlone edytora XML, Eksploratora schematu XML i znak wodny. *Znaku wodnego* znajduje się lista łącza do widoków projektanta XSD.

 ![Projektant XSD; Widok wykresu](../xml-tools/media/xsdgraphviewwatermark.gif "XSDGraphViewWatermark")

 Jeśli zestaw schemat zawiera błędy, na końcu listy jest wyświetlany następujący tekst: "Użyj listy błędów możesz wyświetlać i naprawiać błędy w zestawie".

## <a name="breadcrumb-bar"></a>Pasek nawigacją

 Na pasku stron nadrzędnych w dolnej części widoku wykresu zawiera położenie wybranego węzła w zestawie schematów. Jeśli wybrano wiele elementów na pasku stron nadrzędnych jest puste.

## <a name="context-menu"></a>Menu kontekstowe

 W poniższej tabeli opisano opcje, które są dostępne dla wszystkich węzłów na powierzchni projektowej widoku wykresu.

|Opcja|Opis|
|------------|-----------------|
|**Pokaż w Eksploratorze schematu XML**|Umieszcza fokus na Eksploratora schematu i zaznacza węzła zestawu schematu.|
|**Pokaż w widoku wykresu**|Przełącza do widoku wykresu (szary).|
|**Generowanie przykładowy kod XML**|Dostępne tylko dla elementów globalnego. Generuje przykładowy plik XML dla elementu globalnego.|
|**Wyczyść obszaru roboczego**|Czyści obszaru roboczego i powierzchnię projektu.|
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i powierzchnię projektu.|
|**Usuń wszystkie oprócz wybór z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i powierzchnię projektu.|
|**Eksportuj Diagram jako obraz...**|Zapisuje plik XPS powierzchnię projektu.|
|**Zaznacz wszystko**|Wybiera wszystkie węzły na powierzchni projektu.|
|**Kod widoku**|Otwiera plik, który zawiera wybrany węzeł w edytorze XML. Element, który wybrano w Eksploratora schematu XML zostaną również wybrane w edytorze XML.|
|**Okno właściwości**|Otwiera **właściwości** okna (Jeśli nie jest jeszcze otwarty). To okno wyświetla informacje o węźle.|

 Oprócz typowe opcje opisane powyżej menu kontekstowe elementów globalnego ma następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Dodawanie definicji typu**|Dodaje typ podstawowy do diagramu.|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie węzły, które odnoszą się do elementu i rysuje strzałki do wskazywania relacji między nimi.|
|**Dodaj elementy członkowskie grupy podstawienia**|Dodaje wszystkich członków grupy podstawienia. Ta opcja jest wyświetlana w widoku, jeśli element jest head lub elementem członkowskim grupy podstawienia.|
|**Generowanie przykładowy kod XML**|Generuje przykładowy plik XML dla elementu globalnego.|

 Menu kontekstowe dla globalnych proste i globalnych typów złożonych, oprócz typowe opcje opisane powyżej, ma również następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Dodaj typ podstawowy**|Jeśli wybrany typ pochodzi z typu globalnego, dodaje typ podstawowy elementu wybranego typu.|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie odwołania do wybranego typu. W tym elementów i atrybutów wybranego typu i typy pochodzące od wybranego typu.|
|**Dodaj wszystkie typy pochodne**|Dodaje wszystkie typy, które są bezpośrednio i pośrednio pochodzi od wybranego typu.|
|**Dodaj wszystkich elementów nadrzędnych**|Dodaje wszystkie typy (podstawowe) nadrzędnego.|

 Oprócz typowe opcje opisane powyżej z menu kontekstowego grupę globalną i grupy atrybutów ma następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie węzły, które odnoszą się do grupy i rysuje strzałki do wskazywania relacji między nimi.|
|**Dodaj wszystkie elementy członkowskie**|Dodaje wszystkich członków grupy i rysuje strzałki do wskazywania relacji między nimi.|

 W addtion do typowe opcje opisane powyżej z menu kontekstowego atrybutami globalnymi ma następujące opcje:

|Opcja|Opis|
|------------|-----------------|
|**Dodaj wszystkie odwołania**|Dodaje wszystkie węzły, które odnoszą się do grupy i rysuje strzałki do wskazywania relacji między nimi.|

## <a name="properties-window"></a>Okno Właściwości

 Użyj menu kontekstowego, aby otworzyć początkowo **właściwości** okna. Domyślnie **właściwości** okno jest wyświetlane w prawym dolnym rogu programu Visual Studio. Po kliknięciu węzła, który jest renderowany w widoku modelu zawartości będzie można wyświetlić właściwości tego węzła w **właściwości** okna.

## <a name="xsd-toolbar"></a>Pasek narzędzi XSD

 Następujące przyciski paska narzędzi XSD są włączone, gdy widok wykresu jest aktywny.

 ![Narzędzi Projektanta schematu XML](../xml-tools/media/xsdgraphviewtoolbar.gif "XSDGraphViewToolbar")

|Opcja|Opis|
|------------|-----------------|
|**Pokaż widok początkowy**|Przełącza do [Start widoku](../xml-tools/start-view.md). Ten widok jest możliwy za pomocą skrótu klawiaturowego: **CTRL + 1**.|
|**Pokaż widok modelu zawartości**|Przełącza do [widok modelu zawartości](../xml-tools/content-model-view.md). Ten widok jest możliwy za pomocą skrótu klawiaturowego: **CTRL + 2**.|
|**Pokaż widok wykresu**|Przełącza do [widoku wykresu](../xml-tools/graph-view.md). Ten widok jest możliwy za pomocą skrótu klawiaturowego: **CTRL + 3**.|
|**Wyczyść obszaru roboczego**|Czyści obszaru roboczego i powierzchnię projektu.|
|**Usuń z obszaru roboczego**|Usuwa wybrane węzły z obszaru roboczego i serface projektu.|
|**Usuń wszystkie oprócz wybór z obszaru roboczego**|Usuwa węzły, które nie są wybrane z obszaru roboczego i serface projektu. Ta opcja jest włączona w widoku modelu zawartości i w widoku wykresu.|
|**Od lewej do prawej**|Zmian układu w widoku wykresu od lewej do prawej hierarchiczną reprezentację węzłów. Ta opcja jest możliwy za pomocą skrótu klawiaturowego: **Alt + Strzałka w prawo**.|
|**Od prawej do lewej**|Zmian układu w widoku wykresu hierarchiczną reprezentację węzłów od prawej do lewej. Ta opcja jest możliwy za pomocą skrótu klawiaturowego: **Alt + Strzałka w lewo**.|
|**Z góry na dół**|Zmienia układ w widoku wykresu do góry do dołu hierarchiczną reprezentację węzłów. Ta opcja jest możliwy za pomocą skrótu klawiaturowego: **Alt + Strzałka w dół**.|
|**Dołu do góry**|Zmienia układ w widoku wykresu do dołu do góry hierarchiczną reprezentację węzłów. Ta opcja jest możliwy za pomocą skrótu klawiaturowego: **Alt + Strzałka w górę**.|

## <a name="panscroll"></a>Przesuwanie/przewijania

 Za pomocą pasków przewijania lub klawisz CTRL podczas kliknij i przeciągnij mysz, można kadrować powierzchnię projektu. W przypadku przesuwania powierzchnię projektu przy użyciu kliknij i przeciągnij kursor zmieni się na czterech krzyżowej strzałki w czterech kierunków.

## <a name="undoredo"></a>Cofnij/ponów

 Możliwość Cofnij/Ponów jest włączona w widoku wykresu następujące akcje:

-   Dodawanie jednego węzła przy przeciągania i upuszczania.

-   Dodawanie wielu węzłów w oknie wyników wyszukiwania w zapytaniach Eksploratora schematu lub uruchomić widoku.

-   Usunięcie jednego lub wielu węzłów.

## <a name="zoom"></a>Powiększenie

 Powiększenia znajduje się w prawym dolnym rogu widoku wykresu.

 Powiększenie mogą być kontrolowane w następujący sposób:

-   Przytrzymując klawisz CTRL i obracać kółko myszy, gdy wskaźnik myszy znajduje się na powierzchni widoku wykresu.

-   Za pomocą suwaka. Suwak pokazuje bieżący poziom powiększenia.

Suwak powiększenia jest nieprzezroczysta, zaznacz go, przesuń kursor myszy, lub użyj kombinacji klawisza CTRL kółko myszy, aby powiększyć; w pozostałych godzinach jest niewidoczny.

## <a name="xml-editor-integration"></a>Integracja edytora XML

 Można przełączać i z powrotem w widoku wykresu i edytora XML klikając węzeł i przy użyciu menu kontekstowe widoku kodu.

 Jeśli wprowadzisz zmiany do schematu w edytorze XML zestawu zmiany będą synchronizowane w widoku wykresu. Aby uzyskać więcej informacji, zobacz [integracji z edytora XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Zobacz też

- [Dzięki powierzchni projektowej](../xml-tools/xml-schema-designer-workspace.md)