---
title: Etapy potoku grafiki | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/09/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 393661fba27341ec858aa5c099ea9d131e42273a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-pipeline-stages"></a>Etapy potoku grafiki
W oknie etapy potoku grafiki pomaga zrozumieć, jak wywołanie rysowania poszczególnych jest przekształcana przez każdy etap potoku grafiki Direct3D.  
  
 Jest to oknie etapy potoku:  
  
 ![Obiekt 3D przechodzi przez kolejne etapy potoku.](media/gfx_diag_demo_pipeline_stages_orientation.png)
  
## <a name="understanding-the-graphics-pipeline-stages-window"></a>Opis oknie etapy potoku grafiki  
 Oknie etapy potoku wizualizuje wynik każdego etapu w potoku grafiki osobno dla każdego wywołania rysowania. Zwykle wyniki etapy środku potoku są ukryte, co utrudnia stwierdzić, gdzie rozpoczynają się problem podczas renderowania. Przez wizualizacja osobno na każdym z etapów, oknie etapy potoku ułatwia Zobacz, w którym rozpoczyna się problem — na przykład łatwo widoczny podczas etapu programu do cieniowania wierzchołków nieoczekiwanie powoduje, że obiekt jest narysowanie ekranem.  
  
 Po wyłaniają etap, w którym występuje problem, można narzędzia Analizator grafiki sprawdzić jak interpretować lub przekształcone dane. Problemy z renderowaniem, które są widoczne w etapy potoku są często wierzchołków związanych z niepoprawny format deskryptory, programów do cieniowania buggy lub stan nieprawidłowo skonfigurowane.  
  
### <a name="links-to-related-graphics-objects"></a>Linki do powiązanych grafikach obiektów  
 Czasami dodatkowy kontekst jest wymagany do ustalenia, dlaczego wywołanie rysowania wchodzi w interakcję w określony sposób z potoku grafiki. Aby ułatwić znajdowanie ten dodatkowy kontekst, łącza oknie etapy potoku grafiki do co najmniej jednego obiektu, które zapewniają dodatkowy kontekst związane z tym, co się dzieje w potoku grafiki.  
  
-   W Direct3D 12 ten obiekt jest zwykle listę poleceń.  
  
-   Programu Direct3D 11 ten obiekt jest zwykle kontekstu urządzenia grafiki.  
  
 Łącza te są częścią bieżącego podpis zdarzeń grafiki, który znajduje się w lewym górnym rogu oknie etapy potoku grafiki. Wykonaj jedną z poniższych linków, aby sprawdzić dodatkowe szczegółowe informacje o obiekcie.  
  
### <a name="viewing-and-debugging-shader-code"></a>Wyświetlanie i debugowanie kodu programu do cieniowania  
 Możesz sprawdzić i debugowania kodu dla wierzchołków, powłoki, domeny, programów do cieniowania geometrycznego i pikseli za pomocą formantów w dolnej części ich odpowiednich etapach w oknie etapy potoku.  
  
#### <a name="to-view-a-shaders-source-code"></a>Aby wyświetlić kod źródłowy programu do cieniowania  
  
-   W **etapy potoku grafiki** okna, zlokalizuj etapu programu do cieniowania, który odpowiada programu do cieniowania do sprawdzenia. Następnie poniżej obrazu podglądu kliknij link tytuł etapu programu do cieniowania — na przykład, kliknij link **obj:30 programu do cieniowania wierzchołków** Aby wyświetlić kod źródłowy programu do cieniowania wierzchołków.  
  
    > [!TIP]
    >  Liczba obiektów **obj:30**, identyfikuje to cieniowanie w interfejsie analizatora grafiki takich jak obiekt tabeli i piksela okno Historia.  
  
#### <a name="to-debug-a-shader"></a>Do debugowania cieniowania  
  
-   W **etapy potoku grafiki** okna, zlokalizuj etapu programu do cieniowania, który odpowiada programu do cieniowania chcesz debugować. Następnie poniżej podglądu, wybierz **Rozpocznij debugowanie**. Ten punkt wejścia do wartości domyślnych debuger HLSL dla pierwszego wywołania funkcji programu do cieniowania dla odpowiedniego etapu, oznacza to, pierwszy pikseli, wierzchołków lub typów pierwotnych przetwarzanego przez programu do cieniowania podczas tego wywołania rysowania. Wywołania tego programu do cieniowania pikseli lub wierzchołek jest możliwy za pośrednictwem **Historia pikseli grafiki**.  
  
### <a name="the-pipeline-stages"></a>Etapy potoku  
 W oknie etapy potoku wizualizuje tylko etapy potoku, które były aktywne podczas wywołania rysunku. Każdy etap potoku grafiki przekształca danych wejściowych z poprzedniego etapu i przekazuje jego wynik do kolejnego etapu. Podczas pierwszego etap — asemblera wejściowego — pobiera indeks i wierzchołków dane z aplikacji jako dane wejściowe; ostatni etap — połączenie danych wyjściowych — łączy nowo renderowane pikseli wraz z bieżącą zawartość obiektu lub elementem docelowym renderowania jako dane wyjściowe, aby utworzyć obraz końcowy zostanie wyświetlony na ekranie.  
  
> [!NOTE]
>  Programów do cieniowania obliczeniowe są nieobsługiwane w **etapy potoku grafiki** okna.  
  
 **Asemblera wejściowego**  
 Asembler danych wejściowych odczytuje dane indeksu i wierzchołka określony przez aplikację i składana go dla sprzętu grafiki.  
  
 W oknie etapy potoku jako model szkielet wizualizacji wynik zestawów danych wejściowych. Aby móc bliższe spojrzenie na wynik, wybierz **asemblera danych wejściowych** w **etapy potoku grafiki** okna, aby wyświetlić złożony wierzchołków w pełnej 3D za pomocą edytora modelu.  
  
> [!NOTE]
>  Jeśli `POSITION` semantycznego nie jest obecny w danych wyjściowych asemblera wejściowego, a następnie nie będą wyświetlane żadne w **asemblera wejściowego** etapu.  
  
 **Program do cieniowania wierzchołków**  
 Etapu programu do cieniowania wierzchołków przetwarza wierzchołków zwykle wykonywania operacji, takich jak przekształcania ujęć i oświetlenia. Programów do cieniowania wierzchołków utworzyć taką samą liczbę wierzchołków, których one przyjmuje jako dane wejściowe.  
  
 W oknie etapy potoku jako obraz szkielet wizualizacji danych wyjściowych programu do cieniowania wierzchołków. Aby móc bliższe spojrzenie na wynik, wybierz **programu do cieniowania wierzchołków** w **etapy potoku grafiki** systemu windows, aby wyświetlić przetworzonych wierzchołki edytor obrazów.  
  
> [!NOTE]
>  Jeśli `POSITION` lub `SV_POSITION` semantyki nie występują w danych wyjściowych programu do cieniowania wierzchołków, a następnie nie będą wyświetlane żadne w **programu do cieniowania wierzchołków** etapu.  
  
 **Program do cieniowania powłoki są** (Direct3D 11 i Direct3D 12 tylko)  
 Procesy etapu programu do cieniowania powłoki są kontrolować punktów definiujące powierzchni znaczącymi bitami, takich jak linii, trójkąt lub quad. Jako dane wyjściowe tworzy poprawki geometrii wyższego rzędu i stałych poprawki, które są przekazywane do etapu tworzenia mozaiki stałej funkcji.  
  
 W oknie etapy potoku nie wizualizacji etapu programu do cieniowania powłoki.  
  
 **Etap tessellator** (Direct3D 11 i Direct3D 12 tylko)  
 Etap tessellator to jednostki sprzętu fixed — funkcja (nieprzewidywalnych), która przetwarza wstępnie domeny reprezentowany przez dane wyjściowe programu do cieniowania powłoki. Jako dane wyjściowe, tworzy wzorca próbkowania domeny i zestaw elementów podstawowych mniejszych — punkty, linii, trójkąty — które łączyć te przykłady.  
  
 Na etapie tessellator nie wizualizacji w oknie etapy potoku.  
  
 **Domeny programu do cieniowania** (Direct3D 11 i Direct3D 12 tylko)  
 Etapu programu do cieniowania domeny przetwarza geometrii wyższego rzędu poprawki z cieniowania powłoki współczynniki mozaikowania razem z etap tworzenia mozaiki. Tworzenia mozaiki, może być czynniki tessellator wejściowych czynniki jak również output czynników. Jako dane wyjściowe jest obliczana położenia wierzchołka punktu poprawki dane wyjściowe, zgodnie z tessellator czynników.  
  
 W oknie etapy potoku nie wizualizacji etapu programu do cieniowania domeny.  
  
 **Cieniowania geometrycznego**  
 Etapu programu do cieniowania geometrycznego przetwarza cały podstawowych — punkty, linie lub trójkąty — wraz z danymi wierzchołków opcjonalne dla krawędzi sąsiadujących elementów podstawowych. W odróżnieniu od programów do cieniowania wierzchołków programów do cieniowania geometrycznego można utworzyć więcej lub mniej elementów podstawowych nie podejmują jako danych wejściowych.  
  
 W oknie etapy potoku dane wyjściowe programu do cieniowania geometrycznego wizualizacji jako obraz szkielet. Aby móc bliższe spojrzenie na wynik, wybierz **cieniowania geometrycznego** w **etapy potoku grafiki** okna, aby wyświetlić podstawowych przetworzonych w edytorze obrazów.  
  
 **Strumień wyjściowy etap**  
 Etap strumienia wyjściowego można przechwytywać przekształcone w nim elementów podstawowych przed rasteryzacji i zapisać je w pamięci; z tego miejsca dane mogą być ponownie skierowany jako dane wejściowe do wcześniejszych etapy potoku grafiki lub odczytywane przez procesor CPU.  
  
 W oknie etapy potoku nie wizualizacji fazie strumienia wyjściowego.  
  
 **Etap rasteryzator**  
 Etap rasteryzator jest jednostką sprzętu (nieprzewidywalnych) fixed — Funkcja konwertująca podstawowych wektor — punkty, linii, trójkąty — do obraz, wykonując konwersji linii skanowania. Podczas rasteryzacji wierzchołków są przekształceniu jednorodnego przestrzeni przycinania i przycięta. Jako dane wyjściowe są mapowane programów do cieniowania pikseli i wierzchołków atrybuty są interpolowane przez element pierwotny i gotowy do programu do cieniowania pikseli.  
  
 Na etapie rasteryzator nie wizualizacji w oknie etapy potoku.  
  
 **Program do cieniowania pikseli**  
 Wartości pikseli programu do cieniowania etap procesy rasteryzacji podstawowych oraz dane interpolowane wierzchołków do generowania każdego piksela np. kolor i głębokość.  
  
 W oknie etapy potoku dane wyjściowe programu do cieniowania pikseli wizualizacji jako obraz pełnego koloru. Aby móc bliższe spojrzenie na wynik, wybierz **programu do cieniowania pikseli** w **etapy potoku grafiki** okna, aby wyświetlić podstawowych przetworzonych w edytorze obrazów.  
  
 **Połączenie danych wyjściowych**  
 Etap połączenia danych wyjściowych łączy efekt renderowania nowo pikseli wraz z istniejącą zawartość elementu ich odpowiednich buforów — kolor, głębi i wzornika — Aby utworzyć nowe wartości na liście bufory.  
  
 W oknie etapy potoku jako obraz pełny kolor wizualizacji danych wyjściowych połączenia danych wyjściowych. Aby móc bliższe spojrzenie na wyniki, wybierz **połączenia danych wyjściowych** w **etapy potoku grafiki** okna, aby wyświetlić scalonych obiektu.  
  
### <a name="vertex-and-geometry-shader-preview"></a>Wierzchołka i programu do cieniowania geometrycznego w wersji zapoznawczej  
 Po wybraniu etapu programu do cieniowania wierzchołków lub geometrii w **etapy potoku** okna, można wyświetlić danych wejściowych w celu i dane wyjściowe programu do cieniowania w panelu poniżej.  W tym miejscu można znaleźć szczegółowe informacje o liście wierzchołków dostarczony do programów do cieniowania po zostały zgromadzone przez etap asemblera wejściowego.  

 ![Podglądu buforu wejściowego etapu programu do cieniowania wierzchołków](media/gfx_diag_vertex_shader_inbuffers.png)  
  
 Aby wyświetlić wynik etapu programu do cieniowania wierzchołków, wybierz miniatur etapu programu do cieniowania wierzchołków do wyświetlenia w pełnym rozmiarze, szkielet rasteryzacji z sieci po jego zostały przekształcone przez program do cieniowania wierzchołków.  
  
 ![Podgląd wyników etapu programu do cieniowania wierzchołków](media/gfx_diag_vertex_shader_preview.png)  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem](walkthrough-debugging-rendering-errors-due-to-shading.md)