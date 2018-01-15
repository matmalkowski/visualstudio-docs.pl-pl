---
title: "Diagramy zależności: Odwołania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d11e02e9218d86e0e971c685ab496a2b85b2be21
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="dependency-diagrams-reference"></a>Diagramy zależności: odwołanie
W programie Visual Studio, można użyć *diagram zależności* do wizualizacji Architektura wysokiego poziomu, logicznych systemu. Diagram zależności organizuje artefakty fizycznych w systemie w grupy logiczne, abstrakcyjny *warstwy*. Te warstwy opisano najważniejsze zadania wykonujące artefakty lub głównych składników systemu. Każda warstwa może również zawierać zagnieżdżone warstwy, które opisano bardziej szczegółowe zadania.  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują tę funkcję, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Można określić przeznaczone lub istniejące zależności między warstwami. Te zależności, które są prezentowane w postaci strzałki, wskazać warstw, które mogą używać lub aktualnie funkcji reprezentowany przez inne warstwy. Poprzez organizowanie systemu do warstwy, których opisano różne role i funkcje, diagram zależności mogą ułatwić go zrozumieć, ponowne użycie i obsługa kodu.  
  
 Diagram zależności służy do ułatwiają wykonywanie następujących zadań:  
  
-   Komunikować się z istniejącą lub przeznaczone architektura logiczna systemu.  
  
-   Wykryj konfliktów między istniejący kod i docelowej architektury.  
  
-   Wizualizuj wpływ zmian na komputerze o architekturze zamierzone podczas Refaktoryzuj, zaktualizować lub rozwijać systemu.  
  
-   Wzmocnienie docelowej architektury podczas projektowanie i utrzymanie kodu poprzez włączenie sprawdzania poprawności z zaewidencjonowania i operacji tworzenia.  
  
 W tym temacie opisano elementy, które można zastosować na diagramie zależności. Aby uzyskać szczegółowe informacje o sposobie tworzenia i Rysowanie diagramów zależności, zobacz [diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md). Aby uzyskać więcej informacji na temat wzorców Tworzenie warstw, odwiedź stronę [lokacji wzorce, praktyki i rozwiązania](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
## <a name="reading-dependency-diagrams"></a>Odczytywanie diagramy zależności  
 ![Elementów na diagramach zależności](../modeling/media/uml_layerrefreading.png "UML_LayerRefReading")  
  
 W poniższej tabeli opisano elementy, które można zastosować na diagramie zależności.  
  
|**Kształt**|**Element**|**Opis**|  
|---------------|-----------------|---------------------|  
|1|**Warstwy**|Grupę logiczną artefaktów fizycznych w systemie. Tych artefaktów może być przestrzeni nazw, projektów, klas, metod i tak dalej.<br /><br /> Aby wyświetlić artefaktów, które są połączone z warstwy, otwórz menu skrótów dla warstwy, a następnie wybierz **Wyświetl łącza** otworzyć **Explorer warstwy**.<br /><br /> Aby uzyskać więcej informacji, zobacz [Explorer warstwy](#Explorer).<br /><br /> -   **Dostęp zabroniony zależności Namespace** — Określa, że artefakty skojarzone z tą warstwą nie może zależeć od określonych przestrzeni nazw.<br />-   **Dostęp zabroniony przestrzenie nazw** — Określa, że artefakty skojarzone z tą warstwą nie mogą należeć do określonych przestrzeni nazw.<br />-   **Wymagane obszary nazw** — Określa, że artefakty skojarzone z tą warstwą muszą należeć do jednej z określonych przestrzeni nazw.|  
|2|**Zależności**|Wskazuje jednej warstwie może używać funkcji w innej warstwie, ale nie odwrotnie.<br /><br /> -   **Kierunek** — Określa kierunek zależności.|  
|3|**Zależności dwukierunkowych**|Wskazuje jednej warstwie może używać funkcji w innej warstwie i na odwrót.<br /><br /> -   **Kierunek** — Określa kierunek zależności.|  
|4|**Komentarz**|Umożliwia dodawanie notatek do diagramu lub elementy na diagramie.|  
|5|**Link komentarza**|Umożliwia połączenie komentarzy z elementami na diagramie.|  
  
##  <a name="Explorer"></a>Explorer do warstwy  
 Każdą warstwę można połączyć z artefaktów w rozwiązaniu, takich jak projekty, klasy, przestrzenie nazw, pliki projektu i innymi częściami pakietu oprogramowania. Numer na warstwie pokazuje liczbę artefaktów, które są połączone z warstwy. Podczas odczytywania liczbę artefaktów na warstwie, pamiętaj, następujące czynności:  
  
-   Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.  
  
     Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.  
  
-   Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.  
  
 Aby uzyskać więcej informacji na temat łączenia warstwy i artefaktów zobacz:  
  
-   [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)  
  
-   [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)  
  
#### <a name="to-examine-the-linked-artifacts"></a>Aby sprawdzić połączonego artefaktów  
  
-   Na diagramie zależności, otwórz menu skrótów dla jednej lub kilku warstw, a następnie wybierz **Wyświetl łącza**.  
  
     **Warstwy Explorer** otwiera i zawiera artefakty, które są połączone z wybranej warstwy. **Warstwy Explorer** ma kolumnę, w której przedstawiono wszystkie właściwości linki artefaktu.  
  
    > [!NOTE]
    >  Jeśli nie widzisz wszystkich właściwości, rozwiń węzeł **Explorer warstwy** okna.  
  
    |**Kolumna w Eksploratorze warstwy**|**Opis**|  
    |----------------------------------|---------------------|  
    |**Kategorie**|Rodzaj artefaktu, takich jak klasy, przestrzeń nazw, plik źródłowy i tak dalej|  
    |**Warstwy**|Warstwa, który stanowi łącze do artefaktu|  
    |**Obsługuje sprawdzanie poprawności**|Jeśli **True**, a następnie warstwy procesu weryfikacji można sprawdzić, czy projekt jest zgodny zależności do lub z tego elementu.<br /><br /> Jeśli **False**, a następnie łącze nie uczestniczą w procesie weryfikacji warstwy.<br /><br /> Aby uzyskać więcej informacji, zobacz [diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md).|  
    |**Identyfikator**|Odwołanie do połączonego artefaktu|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
