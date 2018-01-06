---
title: Animacji dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a45fd22cce46cb9e43a649fb969980f42b395db2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="animations-for-visual-studio"></a>Animacji dla programu Visual Studio
## <a name="animation-fundamentals"></a>Podstawy animacji  
  
### <a name="animation-best-practices-in-visual-studio"></a>Animacja najlepszych rozwiązań w programie Visual Studio  
Wykonaj te zasady w celu zapewnienia style animacji spójne i przyjazny dla użytkownika w programie Visual Studio IDE.  
  
-   **Należy zachować ostrożność.** Ogranicz animacje do tych, które służą do określonych celów.  
  
-   **Harmonogram i szybkość są ważne** zapewnienie przejścia uznać, szybkie i fizycznych:  
  
    -   Ukończ animowane przejścia w ciągu sekundy połowę (500 ms).  
  
    -   Animacji, które wystąpiłyby często muszą być dostatecznie szybkiego, że ich nie przerwanie przepływu pracy użytkownika. Obejrzyj animacji w pętli i dostosuj czas, dopóki uważa prawo. 
  
    -   Animacji nie powinny być tak szybkiego lub jarring, że jest trudne do zrozumienia, ale nie tak powolne fakt, że jeden będzie cierpliwy przejścia do zakończenia.  
  
    -   Użyć zmiennej czasu w celu wyróżnienia znaczenie. Na przykład podczas nawigowania sekwencję elementów na diagramie klas, szybkości za pośrednictwem przejścia między elementami, a następnie spowolnić skupić się na istotnych elementów.  
  
-   **Użyj stopniowego napięcia z systemem innym niż liniowy** z jednego stanu do innego, podając w pewnym sensie przepływu cicha i fizycznych.  
  
-   Jeśli to możliwe, **Użyj niewielkie animacji przy aktywowaniu** wskazująca interaktywne elementy w obszarze myszy.  
  
-   Jeśli użytkownik korzysta z silnie animacji w funkcje, następnie **stanowić sposób, aby je wyłączyć** lokalnie (dla wszystkich funkcji) jako opcja w **Narzędzia > Opcje** okna dialogowego.  
  
-   **Tylko jeden animacji powinny występować w czasie** i przekazać tylko jeden zestaw informacji. Więcej niż jeden obiekt przenoszenia lub próba przekazania wiele rzeczy może być trudne. 
  
-   **Ważne jest subtlety.** W większości przypadków animacji nie ma żądanie uwagi użytkownika do obsługi jego przeznaczenia. Niewielkie zmiany w przedziałów czasu, sekwencjonowania i zachowanie może mieć znaczący wpływ na wrażenie i wprowadzać różnica między skuteczne i nieskuteczne animacji.  
  
-   W przypadku używania animacji do zwrócić uwagę, **upewnij się, że zaleca się przerywania użytkownika**w pociągu myśl.  
  
-   **Podczas wyświetlania w toku lub stan** za pośrednictwem animacji:  
  
    -   Przestanie być wyświetlana przepływu postępu podczas przesuwania nie jest podstawowym procesie. 
  
    -   Odróżnić nieokreślony procesy z określonej procesów.  
  
    -   Sprawdź, czy animacja ma do zidentyfikowania stanów zakończenia i niepowodzenie.  
  
    -   Zminimalizuj użycie efekt animacji, które informacje o stanie i upewnij się, czy mają one wartość rzeczywista zapewniając dodatkowe informacje rzeczywistego użycia. Przykłady obejmują zmiany stanu przejściowych i zagrożeń  
  
#### <a name="animation-donts"></a>Animacja — ostrzeżenia:
  
-   Nie używaj ruchy (ruch w niewielkie rozmiary). Preferowane jest zanikanie i zmienia się w przenoszenie obiektów.  
  
-   Nie używaj animacji, które odbywają się za pośrednictwem duży obszar nieruchomości ekranu. Niezależnie od rozmiaru ten styl animacji rozprasza dla użytkownika.  
  
-   Nie używaj animacji niezwiązanych ze sobą na obiekt, który użytkownik aktualnie ma fokus w lub interakcji z.  
  
-   Nie używaj animacji, które wymagają interakcji użytkownika, resetowanie stanu, takie jak wymuszanie użytkownika odpowiedzieć miga powiadomienie, aby zatrzymać miga. Powinien być wystarczające, aby je odrzucić interakcji z nimi w dowolny sposób.  
  
Aby uzyskać więcej informacji w aplikacjach dla następujące najlepsze rozwiązania, zobacz [wzorce animacji](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### <a name="animation-metrics"></a>Metryki animacji  
  
-   System powinien widoczny reagować na gestów użytkownika w mniej niż 10 milisekund.  
  
-   Animowane przejścia nie powinien trwać dłużej niż 500 MS, aby zakończyć.  
  
-   Jednym ze sposobów kompensacji przejść, które wymagają wydłużenie czasu ma oddzielić go na dwie części. Na przykład pierwsza część animacji może być pusty kontener zawartości (maksymalnie 500 ms), następuje Znikająca zawartości do kontenera (maksymalnie 500 ms).  
  
-   Czasy ładowania, które mogą być obliczane preferowane jest wskaźnik postępu decydującym (wskaźnik postępu gotowe procent).  
  
-   Czasy ładowania, których nie można obliczyć odpowiednie jest zajęty wskaźnik kursora lub osadzonych Obracająca animacji (ładowania lub wskaźnik pracy).  
  
### <a name="animation-as-communicator"></a>Animacja jako communicator  
W programie Visual Studio interfejsu użytkownika animacji działa tylko w ramach komunikacji.  Jest on używany do komunikowania się różne informacje, takie jak zmian strukturalnych w Interfejsie użytkownika (na przykład, gdy menu powoduje otwarcie lub zamknięcie). Animacja może pomóc wizualizacji zachowanie zależnych od czasu systemów złożonych, takie jak wizualizacji postęp instalacji. Animacji można również Zwróć uwagę z alertów i powiadomień.  
  
 Animacje interfejsu użytkownika zwykle działać w sposób cztery: wizualizacji, zwróć uwagę, symulować, i czasy odpowiedzi/postęp wskaźników.  
  
#### <a name="visualize"></a>Wizualizacja  
Animacji można wyróżnić trójwymiarowy rodzaj obiektów i ułatwiają użytkownikom wizualizacji ich przestrzennych struktury. Można to osiągnąć, animacji może muszą się obiekt w koło, powoli do i z powrotem, Włącz lub Przenieś obiekt bliżej i wydłużyć jego rozmiar, aby wyróżnić przerzucania lub fokus.  
  
Mimo że obiekty trójwymiarowe można przenieść za pomocą formantu użytkownika, Projektant należy określić wcześniej (programowo lub ręcznie) jak do najlepszych animować przeniesienia, która zapewnia optymalną opis obiektu. To może animacji zaprogramowane w taki sposób, a następnie aktywowany przez użytkownika po umieszczeniu kursora na obiekcie, użytkownika zrozumieć sposób modyfikowania obiektu wymagają przeniesień kontrolowane przez użytkownika. Ograniczanie ruchu na jednej osi lub orientacji jednocześnie. albo skalowania, obracanie, lub tłumaczenia, ale nie więcej niż jeden jednocześnie.  
  
Kategoria wizualizacja zawiera aspektów danych relacji, stan, struktury, kolejność i czas.  
  
##### <a name="data"></a>Dane  
Przedstawiono informacje o złożone i zmiennych:  
  
-   Nawigacja po wizualizacje informacje, takie jak wykresy i schematy  
  
-   Krokowe wykonywanie sekwencji, samouczek i stronicowania  
  
-   Wywoływanie szczegółów, wskazując i wyróżnianie określonych informacji  
  
-   Nakładanie szczegóły i dodatkowe informacje na podstawie zaznaczonego elementu
  
-   Przekształcania właściwości z jednego reprezentacji strukturalnych lub organizacji do innego  
  
-   Reprezentujący zmiany w czasie przy użyciu suwaki czasu, koła Wyrównaj wahadłowych i formanty transportu (play, Zatrzymaj i Wstrzymaj) 
  
##### <a name="relationships"></a>Relacje  
  
-   Ilustrują sposób elementy odnoszą się do siebie lub elementy, które odnoszą się do danego elementu
  
-   Wyświetlanie hierarchii i nadrzędny podrzędny lub element równorzędny relacji
  
-   Jeden element spowoduje utworzenie innego
  
-   Minimalizuje jeden element do innego elementu
  
-   Jeden element spętane do innego
  
##### <a name="state"></a>Stan  
  
-   Aktualizacje zawartości
  
-   Wybieranie i fokus  
  
-   Postęp  
  
-   błędy  
  
##### <a name="structure"></a>Struktura  
  
-   Przestawianie struktury w jednym węźle  
  
-   Zmiana orientacji  
  
-   Minimalizowanie i zmaksymalizować, lub rozwijanie i zwijanie  
  
##### <a name="sequence"></a>Sekwencja  
  
-   Pokaz slajdów sekwencji  
  
-   Przerzucanie obrazów  
  
##### <a name="time"></a>Godzina  
  
-   Zmień Pokaż za pośrednictwem czas i czas wygaśnięcia oraz screencast  
  
-   Przenieś do Kosz, Cofnij i wykonaj ponownie  
  
-   Przywróć stan historyczny  
  
#### <a name="attract-attention"></a>Zwróć uwagę  
Jeśli celem jest zwrócenie uwagi użytkownika do pojedynczego elementu poza kilka lub poinformowania użytkownika o zaktualizowane informacje, animacja może być odpowiednie. Na przykład stronę początkową aplikacji może stosować slajdów na miejsce po załadowaniu strony przycisk wprowadzenie.  
  
Zgodnie z zasadą ostatnim elementem przenoszenie na ekranie przyciąga uwagi użytkownika.  W serii animowanych elementów uwagi użytkownika są zgodne z ostatniego przenoszenia obiektu.  
  
##### <a name="alert"></a>Alert  
  
-   Użytkownika, Pobierz uwagi, pokazywania postępu  
  
-   Pokazuje, czy element jest wykonywana prawidłowo lub niepoprawnie lub pokazywania postępu lub zmiany w toku  
  
-   Monituj użytkowników podczas zadania, takie jak wyszukiwanie więcej informacji w trybie online lub poznawania bieżącego zadania  
  
##### <a name="notifications"></a>Powiadomienia  
  
-   Ostrzec użytkownika o warunku błędu  
  
-   Przerwanie użytkownika, aby zobaczyć, czy chce uczestniczyć na inny  
  
-   Ostrożnie informuje użytkownika, który zakończył proces lub zmieniona, takich jak po zakończeniu pobierania.  
  
#### <a name="simulate"></a>Symulowanie  
Ta kategoria obejmuje physicality i wymiary.  
  
-   Ilustrowanie skąd obiektów lub gdy przejdź do  
  
-   Rozwijanie i zwijanie lub otwierania i zamykania  
  
-   Włącza przesuwanie przewijanie i strony  
  
-   Łączenie urządzeń i warstwach  
  
-   Karuzela i accordion  
  
-   Przerzucanie i obracanie interfejsu użytkownika  
  
#### <a name="response-and-progress-indicators"></a>Wskaźniki odpowiedzi i postępu  
Wskaźniki postępu ma kilka istotnych korzyści:  
  
-   Oba wskaźniki postępu określania i nieokreślony przywróceniu zaufania użytkownika, że system nie wystąpiła awaria i działa na problem.  
  
-   Określania wskaźników przyznać użytkownikowi, który postępuje zorientować się, jak daleko wzdłuż akcji, a także wrażenie pobierania zbliżonej do zakończenia.  
  
##  <a name="BKMK_AnimationPatterns"></a>Wzorce animacji  
  
### <a name="overview"></a>Omówienie  
Animacje w programie Visual Studio są przeznaczone do obsługi określonych funkcji bez zakłócały wydajność pracy użytkownika. Ogólnie rzecz biorąc powinny być animacji w programie Visual Studio:  
  
-   Małe i dyskretnego kodu  
  
-   Fizyczne i realistyczne  
  
-   Niewielkie i przytłumionym  
  
-   Szybkie i wydajne  
  
-   Swobodna, nie hurried  
  
Na ilustracji przedstawiono style animacji, zaleca się dla programu Visual Studio. Nie animacji lub niewielkie animacji jak zanikania / zanikania najczęściej są używane. Istnieje ograniczona aplikacji przepływu animacji jak rozwinąć lub zwinąć, X i Y pozycji zmianami i obrotu. 
  
![Zalecane style animacji dla programu Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202 a_VSAnimStyles")<br />Style animacji zalecane dla programu Visual Studio
  
#### <a name="appear-and-disappear"></a>Pojawiają się i znikają  
Z tego wzorca element przełączników z widoczne poza widoku i ponownie bez animacji przejścia.  
  
![Pojawiają się i znikają animacji](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202 b_AppearAndDisappear")<br />Pojawiają się i znikają animacji  
  
##### <a name="correct-usage"></a>Poprawne użycie  
Nowa elementy interfejsu użytkownika, które należy natychmiast lub pojawiania się tak, aby użytkownik nie jest efektów ani zablokowane. Ponadto animacje powolna przenoszenia może być uważane za przeciągania wydajności, które nie występują w przypadku stylu występują i znikają.  
  
##### <a name="incorrect-usage"></a>Nieprawidłowe użycie  
Przypadków, w których interfejsu użytkownika zostanie wyświetlony dlatego nagle użytkownik ma nie wiadomo co się stało, i Dodawanie animacji byłaby pomocna kontekstowe opis.  
  
##### <a name="animation-properties"></a>Właściwości animacji  
Czas opóźnienia wynosi zero sekund.  
  
##### <a name="examples"></a>Przykłady    
-   Automatyczne ukrywanie okna narzędzi  
  
-   Aktywowany klawiatury Edytor interfejsu użytkownika, takie jak IntelliSense i parametr pomocy  
  
-   Regiony rozwijanie i zwijanie kodu  
  
#### <a name="fade-in-and-fade-out"></a>Twierania i fade-out  
Z tego wzorca elementu interfejsu użytkownika przejścia z nie są widoczne (nieprzezroczystość 0%) do widocznych (100% nieprzezroczystości) lub na odwrót.  
  
![Animacja twierania i fade-out](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202 c_FadeInFadeOut")<br />Animacja twierania i fade-out  
  
##### <a name="correct-usage"></a>Poprawne użycie  
Najczęściej jest to zalecane animacji interfejsu użytkownika. Jest Delikatny efekt, który dodaje odsetek bez przerywania przepływu. W niektórych przypadkach użytkownik może nawet nie zauważysz brak animacji odczuwania sprawne i przepływających interfejsu użytkownika systemu.  
  
##### <a name="animation-properties"></a>Właściwości animacji  
  
-   Uruchamianie nieprzezroczystość: 0% dla twierania, 100% fade-out  
  
-   Kończenie nieprzezroczystość: 100% twierania, 0% dla fade-out  
  
-   Czas trwania: autonomiczny 200 MS, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacja  
  
-   Ułatwianie stylu: InOut sinus  
  
##### <a name="examples"></a>Przykłady  
  
-   Automatyczne ukrywanie okna narzędzi  
  
-   Menu otwierających i zamykających  
  
-   Przejścia kartę tła i pierwszego planu  
  
#### <a name="color-blend-from-a-to-b"></a>Program blend koloru z zakresu od A do B  
Z tego wzorca elementu interfejsu użytkownika zmieni się z kolor na kolor B.  
  
![Kolor blend animacji](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202 d_ColorBlend")<br />Kolor blend animacji  
  
##### <a name="correct-usage"></a>Poprawne użycie  
Jako animowany przejścia, gdy element interfejsu użytkownika zmienia kolor z jednego kontekstu lub stanu do innego.  
  
##### <a name="animation-properties"></a>Właściwości animacji  
  
-   Kolor początkowy: specyficzne dla interfejsu użytkownika  
  
-   Końcowy kolor: specyficzne dla interfejsu użytkownika  
  
-   Czas trwania: autonomiczny 200 MS, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacja  
  
-   Ułatwianie stylu: InOut sinus  
  
##### <a name="examples"></a>Przykłady  
  
-   Przejścia stanów polecenie Okno dokumentu (aktywny, ostatni aktywnych i nieaktywnych)  
  
-   Narzędzie przejść stanu okna (ukierunkowanych i bez fokusu)  
  
#### <a name="expand-and-contract"></a>Rozwiń węzeł i kontraktu  
Z tego wzorca elementu interfejsu użytkownika rozszerza w X, Y lub w obu kierunkach.  
  
![Rozwinąć lub zwinąć animacji](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202 e_ExpandContract")<br />Rozwinąć lub zwinąć animacji  
  
##### <a name="correct-usage"></a>Poprawne użycie  
Jako animowany przejścia, gdy element interfejsu użytkownika zmieni się rozmiar z jednego kontekstu na inny.  
  
##### <a name="animation-properties"></a>Właściwości animacji  
  
-   X skali: % lub określonego wymiaru (w pikselach)  
  
-   Skala Y: % lub określonego wymiaru (w pikselach)  
  
-   Pozycji zakotwiczenia: ogólnie lewej górnej (w przypadku języków od lewej do prawej) lub prawego górnego (dla języków od prawej do lewej)  
  
-   Czas trwania: autonomiczny 200 MS, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacja  
  
##### <a name="examples"></a>Przykłady  
  
-   Panel Eksploratora architektury rozwijanie i zwijanie  
  
-   Strona elementu rozwijanie i zwijanie początkowa  
  
#### <a name="x-y-position-change"></a>Zmiana pozycji X i Y  
Z tego wzorca elementu interfejsu użytkownika zmienia jego położenie X i Y lub oba.  
  
![Położenie X i Y zmienić animacji](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202 f_XYPositionChange")<br />Animacja zmiany pozycji X i Y  
  
##### <a name="correct-usage"></a>Poprawne użycie  
Jak przejście animowany, gdy element interfejsu użytkownika zmienia pozycję z jednego kontekstu na inny.  
  
##### <a name="animation-properties"></a>Właściwości animacji  
  
-   Pozycja początkowa X i Y: specyficzne dla interfejsu użytkownika  
  
-   Pozycja końcowa X i Y: specyficzne dla interfejsu użytkownika  
  
-   Ścieżka ruchu: Brak  
  
-   Czas trwania: autonomiczny 200 MS, 100 milisekund, gdy jest używany jako część sekwencji animacji kombinacja  
  
-   Ułatwianie stylu: InOut sinus  
  
##### <a name="example"></a>Przykład  
Zmiana kolejności kart  
  
#### <a name="rotate"></a>Obrót  
Z tego wzorca obraca element interfejsu użytkownika.  
  
![Animacja obrotu elementu interfejsu użytkownika](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202 g_Rotate")<br />Animacja obrotu elementu interfejsu użytkownika  
  
##### <a name="correct-usage"></a>Poprawne użycie  
Tylko w przypadku nieokreślonego Obracająca wskaźnik postępu.  
  
##### <a name="animation-properties"></a>Właściwości animacji  
  
-   Kąt obrotu: 360  
  
-   Centrum obrotu: środkowej obiektu  
  
-   Czas trwania: ciągły  
  
##### <a name="example"></a>Przykład  
Wskaźnik postępu nieokreślony (Obracająca)  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>Typowych akcji interfejsu użytkownika powłoki i zalecane animacji  
  
#### <a name="tab-open"></a>Karta otwarte  
![Karcie Animacja Otwórz](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202 h_TabOpen")<br />Animacja Otwórz kartę  
    
-   Styl: pojawiają się  
  
-   Czas trwania: zero sekund.  

#### <a name="tab-close"></a>Zamknij kartę  
![Karta Zamknij animację](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202 i_TabClose")<br />Zamknij animację kartę  
  
-   Styl: Zmień położenie X  
  
-   Czas trwania: 200 MS  
  
#### <a name="tab-reorder"></a>Zmień kolejność kartę  
![Karcie Animacja zmiany kolejności w programie Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202 j_TabReorder")<br />Karta zmiany kolejności animacji

-   Styl: Zmień położenie X  
  
-   Czas trwania: 200 MS  
    
#### <a name="close-floating-document"></a>Zamknij dokument zmiennoprzecinkowych  
![Zamknij zmiennoprzecinkową animacji dokumentu](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202 k_CloseFloatingDocument")<br />Zamknij przestawne animacji dokumentu  
   
-   Styl: pojawiają się  
  
-   Czas trwania: 200 MS   
 
#### <a name="window-state-transition"></a>Przejście stanu okna  
![Animacja przejścia stanu okna](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202 l_WindowStateTransition")<br />Animacja przejścia stanu okna  
    
-   Styl: być zgodne z innymi oknami, umożliwiają definiowanie animacji Zamknij dokument bieżący system operacyjny.  
  
-   Czas trwania: 200 MS  
  
#### <a name="menu-open"></a>Otwórz menu  
![Animacja Otwórz menu](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202 m_MenuOpen")<br />Animacja Otwórz menu  
    
-   Styl: twierania  
  
-   Czas trwania: 200 MS  
  
#### <a name="menu-close"></a>Zamknij menu  
![Zamknij animację menu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202 n_MenuClose")<br />Zamknij animację menu  
    
-   Styl: fade-out  
  
-   Czas trwania: 200 MS  
  
#### <a name="auto-hide-tool-window-reveal"></a>Automatyczne ukrywanie ujawniania okna narzędzi  
![Automatyczne ukrywanie animacji ujawniania okna narzędzia](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")<br />Automatyczne ukrywanie animacji ujawniania okna narzędzi  

-   Styl: pojawiają się  
  
-   Czas trwania: zero sekund.