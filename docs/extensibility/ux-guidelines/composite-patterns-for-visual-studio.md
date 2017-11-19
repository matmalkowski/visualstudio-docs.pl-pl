---
title: "Wzorce złożone dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6ce0fccf3a957edfdf732ce3ea462bef26c5a0c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="composite-patterns-for-visual-studio"></a>Wzorce złożone dla programu Visual Studio
Wzorce złożone połączyć elementy projektu i interakcji w różnych konfiguracjach. Oto niektóre z najważniejszych wzorce złożone w programie Visual Studio w zakresie spójności:  
  
-   [Wizualizacja danych](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [Interfejs użytkownika i wgląd w obiekcie](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [Wybór modeli](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [Trwałość i zapisywania ustawień](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [Wprowadzania dotykowego](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="BKMK_DataVisualization"></a>Wizualizacja danych  
  
### <a name="overview"></a>Omówienie  
 Wykresy służą visual do agregacji i wizualizacji danych w celu zwiększenia podejmowania decyzji. Pozwalają one użytkowników z dużą ilością danych, ale małego oznacza Zobacz, co wymaga uwagi, i co może wymagać akcji, które muszą ponieść.  
  
 Użytkownik będzie korzystać z wykresu, jeśli spełnione są następujące warunki:  
  
-   Wykres ułatwią użytkownikom identyfikację zadań, które działają na?  
  
-   Wykres umożliwi użytkownikom prognozy skutków potencjalnych zmiany?  
  
-   Wykres ułatwią użytkownikom odnajdywania trendów i wzorców zidentyfikować?  
  
-   Wykres umożliwia użytkownikom podejmowanie lepszych decyzji?  
  
-   Wykres pomoże odpowiedzi na konkretne pytanie, które użytkownicy mogą mieć w danym kontekście?  
  
#### <a name="general-rules-for-charts"></a>Ogólne zasady dla wykresów  
  
-   Wyraźnie Etykieta danych. Ilustracje bez wyjaśnienie są po prostu pretty obrazów.  
  
-   Uruchom osie na zero, aby uniknąć pochylanie proporcji. Rozmiar linii długość i paska są ważne wizualnych do zrozumienia relacje między punktami danych.  
  
-   Tworzenie wykresów, nie infographics. Infographics artystycznego reprezentacje danych, i ich podstawowym celem tworzenia visual scenariuszy. Wykresy mogą powinien być atrakcyjność, a Niech dane mówią same za siebie.  
  
-   Unikaj skeumorphism, wykresy słupkowe obrazkami hashmarks kontrast i inne poprawki infographic.  
  
-   Nie należy używać jako elementu ozdobne efekty 3W. Ich używać tylko wtedy, gdy są naprawdę integralną częścią możliwości zrozumienie informacji.  
  
-   Należy unikać wielu linii i wypełnień, ponieważ więcej niż dwa kolory może utrudnić tego typu wykresu do odczytywania i zinterpretować.  
  
-   Nie należy używać wykresu (lub dowolnego ilustracji) jako jedyny sposób opis koncepcji lub interakcji z danymi. Stwarza problemy dla użytkowników niedowidzących.  
  
-   Nie używaj wykresy kontrolne lub ozdobne elementów na stronie. Innymi słowy Jeśli wykresu nie dodaje się, że wszyscy użytkownicy wartość lub pomocy rozwiązania problemu, nie używaj go.  
  
### <a name="chart-types"></a>Typy wykresów  
 Typy wykresów używane w programie Visual Studio to wykresy słupkowe, wykresy liniowe, modyfikacji wykresu kołowego, znany jako pierścień wykresu lub "wykres pierścieniowy przedstawiający," osi czasu, punktowy powierzchni (zwane również "klastra wykresy") i wykresy Gantta. Każdy typ wykresu jest przydatna do komunikacji z innego typu informacji.  
  
### <a name="other-charting-considerations"></a>Inne zagadnienia wykresów  
  
#### <a name="color"></a>Kolor  
 Brak określonego palety kolorów zdefiniowanych do użytku w programie Visual Studio wykresów. Palecie jest dostępny dla głównych typów ruchu kolorów i mogą być rozróżniane kolory, nawet wtedy, gdy jest używany jako bardzo małym wycinków koloru. Można używać tych kolorów w dowolnej kombinacji dla dowolnego typu wykresu lub schematu w Interfejsie użytkownika. Nie trzeba używać wszystkich siedmiu kolorów, jeśli nie potrzebujesz tak wielu odrębnych kolorów. Kolorów te nie są przeznaczone do użycia z elementów pierwszego planu, więc nie zostanie tekst lub symbole na górze kolorów te. Te barwy powinny być ustalony i widoczne dla użytkownika dostosowania w obszarze **Narzędzia > Opcje** (zobacz [udostępnianie kolorów dla użytkowników końcowych](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  
  
|Próbki|Hex|RGB|  
|------------|---------|---------|  
|![Próbka 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|  
|![Próbka BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Próbka FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Próbka 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Próbka 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Próbka 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Próbka B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  
  
##  <a name="BKMK_OnObjectUI"></a>Interfejs użytkownika i wgląd w obiekcie  
 W tej sekcji przedstawiono kontekst do wybierania, znanej także jako widok peek kodu, typ interfejsu użytkownika na obiekcie unikatowy dla programu Visual Studio.  
  
### <a name="overview"></a>Omówienie  
  
-   Na obiekt interfejsu użytkownika powinien zapewnić użytkownika więcej informacji lub interakcyjności bez szkody dla ich głównym zadaniem.  
  
-   Wzorzec główny dla interfejsu użytkownika na obiekcie w programie Visual Studio jest nazywany "informacje o punkcie uwagi".  
  
-   Interfejsu użytkownika na obiekcie w programie Visual Studio jest albo wbudowanego lub zmiennoprzecinkową i niezawodny lub przejściowy.  
  
    -   Kod peek widok, typ interfejsu użytkownika na obiekcie w programie Visual Studio jest wbudowanym i niezawodny.  
  
    -   CodeLens, typ interfejsu użytkownika na obiekcie w programie Visual Studio jest przejściowy i zmiennoprzecinkowych  
  
 Zrozumienie, jak działa fragment kodu lub znajdowania szczegółowe informacje dotyczące tego kodu, często wymaga dewelopera przełączyć kontekst i przejdź do innej zawartości lub innego okna. Te zmiany kontekstu mogą stanowić zakłócenie, ponieważ użytkownicy mogą utracić fokus na ich oryginalny zadania, jeśli opuszczają ich głównego okna. Ponadto pobieranie, że oryginalna zwrotnego kontekstu może być trudne, zwłaszcza, jeśli przełączanie windows spowodował ich oryginalny kod, aby być zasłonięty przez inne interfejsu użytkownika.  
  
 Na obiekt interfejsu użytkownika jest zgodna ze wzorcem o nazwie "informacje o punkcie uwagi". Te komunikaty, wyskakujące i oknach dialogowych zapewniają użytkownikom dodatkowych, odpowiednie informacje, które dodaje wyjaśnienie lub interakcyjności bez utraci fokus na ich głównym zadaniem. Przykładami interfejsu użytkownika na obiekcie wyskakujące, które są wyświetlane, gdy użytkownik znajduje się wskaźnik myszy nad ikonę w obszarze powiadomień, czerwona falista wyrazu i widoku peek wprowadzone w programie Visual Studio 2013.  
  
### <a name="decision-points"></a>Punkty decyzyjne  
 W programie Visual Studio istnieje kilka sposobów użycia tego wzorca informacji w punkcie uwagi. Wybieranie mechanizmu prawo i wdrażanie go w sposób spójny, przewidywalnych jest niezbędne do obsługi ogólnej. W przeciwnym razie użytkownicy mogą być wyświetlane przy użyciu środowiska mylące lub niespójne źle wpływa fokus z samej zawartości.  
  
#### <a name="relationships-between-master-and-detail-content"></a>Relacje między wzorca i szczegóły zawartości  
 Informacje o punkcie uwagi służy do wyświetlania relacji między zawartości, czy użytkownik jest koncentruje się na (zawartość "główny") i dodatkowe powiązane zawartości (content "szczegóły"). W tym wzorcu zawartość szczegółów jest wyraźnie powiązana zawartość użytkownik pracuje i mogą być wyświetlane blisko wzorca zawartości. Informacje uzupełniające lub informacji nie można podsumować bez przeciążając uda się rozpoznać wzorca zawartości powinien być zgodny innego wzorca, takie jak okna narzędzia.  
  
-   **Zawsze** wyświetlać zawartość szczegółów w pobliżu wzorca zawartości.  
  
-   **Zawsze** upewnij się, że zawartość szczegółów nadal umożliwia użytkownikowi pozostają koncentruje się na głównym zawartości. Często najlepszy sposób, aby osiągnąć ten cel jest do renderowania zawartości szczegółów jako bliski wzorca zawartości, jak to możliwe. Można to zrobić przez renderowania zawartości szczegóły w oknie podręcznym obok głównego zawartości lub renderowania wbudowanej zawartości szczegóły poniżej wzorca zawartości.  
  
-   **Nigdy nie** informacje w punkcie uwagi pobierającej użytkownika od głównego zawartości. Jeśli użytkownicy będą potrzebować do wyświetlania zawartości szczegółów oddzielnie, ujawnia jawnej akcji, który umożliwia użytkownikowi w tym celu.  
  
#### <a name="design-details"></a>Szczegóły projektu  
 Po ustaleniu, że na obiekt interfejsu użytkownika jest właściwie, istnieją cztery główne projektowania:  
  
1.  **Trwałość:** zawartość ma być trwałe lub przejściowej?   
    Zostanie użytkowników powinny być widoczne dla odwoływać się do lub interakcji z informacje? Czy użytkownicy będą szybko przejrzeć informacje o, a następnie kontynuuj ich głównym zadaniem?  
  
2.  **Typ zawartości:** zawartość będzie informacyjny, można wykonać lub nawigacji?   
    Czy użytkownik potrzebuje dodatkowych informacji na temat wzorca zawartości? Czy użytkownik musi ukończyć zadania, które ma wpływ na głównym zawartości? Lub czy użytkownik musi być kierowane do innego zasobu?  
  
3.  **Typ wskaźnika:** ma wskaźnik otoczenia sensu?   
    Informacje można podsumowane w przystępny sposób i wyświetlać bez przeciążając uda się rozpoznać wzorca zawartości?  
  
4.  **Gestów:** co gesty, przy użyciu będzie służyć do wywołania i odrzucić interfejsu użytkownika?   
    Jak będzie użytkownika wyświetlić zawartość szczegółów i wysyłać je do optymalizacji? Występuje wartość Dodawanie gestów, takich jak przypinanie w celu przełączania się między Stanami przejściowych i trwałe?  
  
 Każdy z tych punktów decyzyjnych cztery będą miały wpływ na głównych składników interfejsu użytkownika na obiekcie.  
  
### <a name="on-object-ui-components"></a>Składniki interfejsu użytkownika na obiekcie  
  
1.  Typ kontenera (prezenterze zawartości)  
  
    -   Liczby zmiennoprzecinkowe  
  
    -   Wbudowany  
  
2.  Typ zawartości  
  
    -   Komunikat o charakterze informacyjnym: dane, które mogą być statyczne lub dynamiczne  
  
    -   Można wykonać: poleceń, które zmienia wzorca zawartości  
  
    -   Nawigacyjne: łącza, które prowadzą użytkownika do innego okna lub aplikacji, takie jak MSDN  
  
3.  Gestów  
  
    -   Wywołania  
  
    -   Zwolnienia  
  
    -   Przypinanie  
  
    -   Inne interakcji  
  
4.  Model trwałości i zatwierdzania  
  
    -   Przejściowy  
  
    -   trwałe  
  
    -   Automatyczne  
  
    -   Na żądanie  
  
5.  Wskaźniki otoczenia (opcjonalnie)  
  
    -   Wężyk podkreślenie  
  
    -   Ikona tagów inteligentnych  
  
    -   Inne wskaźniki otoczenia  
  
#### <a name="container-content-presenter-type"></a>Typ kontenera (prezenterze zawartości)  
 Istnieją dwie główne opcje dostępne do prezentowania zawartości w punkcie uwagi:  
  
1.  **Wbudowany:** prezenterze wbudowany, takich jak wprowadzone w programie Visual Studio 2013 edytora kodu, w widoku peek sprawia, że miejsce dla nowej zawartości ustalając istniejącej zawartości.  
  
    -   **Preferowane jest** przedstawia Prezenterzy wbudowany, Jeśli przypuszczasz, że użytkownicy będą chcieli spędzają na znaczną ilość czasu odwołujących się do lub interakcji z zawartością.  
  
    -   **Unikaj** Prezenterzy wbudowany, jeśli użytkownicy będą chcieli Przegląd informacje stanowią, następnie kontynuuj ich zadań głównych z minimalnym przerw w działaniu.  
  
2.  **Liczby zmiennoprzecinkowe:** przestawne prezenterze znajduje się maksymalnie zbliżony wybranej zawartości, jak to możliwe, ale nie zmienia układ istniejącej zawartości. Różne strategie można zastosować, takie jak wyświetlanie przestawne panelu zawartości za pośrednictwem najbliższy dostępny biały znak do wybranego symbolu.  
  
    -   **Preferowane jest** zmiennoprzecinkową Prezenterzy, jeśli użytkownicy będą Przegląd informacje stanowią, następnie kontynuuj ich zadań głównych z minimalnym przerw w działaniu.  
  
    -   **Unikaj** zmiennoprzecinkową Prezenterzy, jeśli użytkownicy będą chcieli spędzają na znaczną ilość czasu odwołujących się do lub interakcji z zawartością można obecny.  
  
#### <a name="content-type"></a>Typ zawartości  
 Istnieją trzy typy zawartości, którą można wyświetlić w dowolnej kontenera interfejsu użytkownika na obiekcie. Można wyświetlić dowolną kombinację tych typów informacji. Są trzy typy:  
  
1.  **Komunikat o charakterze informacyjnym:** kontenery interfejsu użytkownika spowoduje wyświetlenie niektórych rodzaj informacyjną zawartości na obiekt dla większości. Zawartość może reprezentować informacji o stanie środowiska lub może reprezentować informacji na temat potencjalnych przyszły stan środowiska. Na przykład można użyć pokazanie efekt konkretnego polecenia, takich jak refaktoryzacji na istniejący kod.  
  
    -   **Zawsze** Użyj canonical reprezentację informacje, które można wyświetlić. Na przykład kod powinien wyglądać kodu z wyróżnianie składni i należy przestrzegać niezależnie od czcionek i inne ustawienia środowiska, ustawione przez użytkownika.  
  
    -   **Zawsze** należy wziąć pod uwagę obsługi wszystkie akcje, za pośrednictwem informacyjną zawartość, która będzie możliwe, gdy te same informacje są prezentowane jako główny zawartości. Rozważmy na przykład jeśli umożliwienie korzystania z istniejącego kodu wewnątrz kontenera interfejsu użytkownika na obiekcie, silnie obsługi możliwość przeglądania i modyfikowania kodu.  
  
    -   **Zawsze** należy rozważyć użycie inny kolor tła, jeśli prezentacja informacyjną zawartości, która reprezentuje potencjalnych przyszły stan.  
  
2.  Można wykonać: niektóre kontenery interfejsu użytkownika na obiekcie zapewni możliwość wykonywania pewnych akcji wzorca zawartości, takich jak przeprowadzanie operacja refaktoryzacji.  
  
    -   **Zawsze** umieść można wykonać polecenia niezależnie od zawartości informacyjny.  
  
    -   **Zawsze** Włączanie i wyłączanie akcji, gdy jest to konieczne.  
  
    -   **Zawsze** odwoływać się do standardowych wytycznych reprezentujący poleceń w oknach dialogowych.  
  
    -   **Zawsze** zachować minimalną liczbę działań, które są dostępne w kontenerze na obiekt interfejsu użytkownika na poziomie. Interakcja z interfejsu użytkownika na obiekcie powinna być lekkie środowisko szybkie. Użytkownik nie ma do rozwiń energii na zarządzanie sam pojemnik interfejsu użytkownika na obiekcie.  
  
    -   **Zawsze** należy wziąć pod uwagę, jak i kiedy kontener na obiekt interfejsu użytkownika zostanie zamknięty lub odrzucone. Najlepszym rozwiązaniem dowolną akcję, która zawiera okno dialogowe między wzorca i szczegóły zawartości należy również zamknąć kontenera interfejsu użytkownika na obiekcie po wywołaniu tej akcji.  
  
3.  **Nawigacja:** niektóre na obiekcie kontenerów interfejsu użytkownika należą linki prowadzące użytkownika do innego okna lub aplikacji, takie jak otwieranie artykuł w witrynie MSDN w przeglądarce sieci web.  
  
    -   **Zawsze** dołączy żadnych łącze nawigacyjne "Po otwarciu", dzięki czemu użytkownicy będą nie oczekiwano, przez do niektórych innej zawartości.  
  
    -   **Zawsze** oddzielnych łącza nawigacyjne z możliwością wykonania akcji łącza.  
  
#### <a name="ambient-indicators-optional"></a>Wskaźniki otoczenia (opcjonalnie)  
 Wskaźniki otoczenia może być niewielkie, łącznie z tekstem przedstawionych w kolorze kontrastowym od pozostałej części kodu, lub oczywiste, w tym tickler symbole, takie jak podkreślenie wężyk i ikony tagów inteligentnych. Wskaźniki otoczenia komunikacji dostępności odpowiednich dodatkowych informacji. W idealnym przypadku zawierają użyteczne informacje nawet bez konieczności interakcji z użytkownikiem przez użytkownika.  
  
-   **Zawsze** umieść wskaźnik otoczenia rozpraszać uwagę lub nie przeciąży użytkownika. Jeśli nie jest możliwe umieścić wskaźnik otoczenia w taki sposób, należy rozważyć inne rozwiązanie.  
  
-   **Zawsze** możliwie najbliżej do zawartości, która jest powiązana z umieść wskaźnik otoczenia.  
  
-   **Zawsze** spróbuj utworzyć wskaźnika, który zawiera podsumowanie dostępnych informacji. Rozważ podanie liczby liczba dostępnych elementów danych (na przykład, "3 odwołania" zamiast po prostu "informacje") lub traktować inny sposób podsumowywania danych.  
  
    -   W przypadku gdy dane dla wskaźnika nie zawsze być obliczana i wyświetlane natychmiast należy rozważyć przekazywanie opinii progresywnego, jak są obliczane wartości. Rozważmy na przykład animowanie zmian, które odzwierciedlanie aktualizacji dostępnych danych, podobnie jak, którą odświeża Kafelek na żywo poczty e-mail na Windows Phone jako liczba wzrasta nieprzeczytanych wiadomości e-mail.  
  
-   **Nigdy nie** Dodawanie wskaźników więcej niż użytkownik rozsądnych można wykonać dla danego elementu zawartości. Wskaźniki otoczenia powinna być przydatne bez konieczności interakcji użytkownika. Wskaźniki utratę ich otoczenie wymagają przepełnienie i innych kontrolek zarządzania, aby dostosować je do widoku.  
  
#### <a name="gestures"></a>Gestów  
 Kluczowym aspektem umożliwiający użytkownikowi utrzymać fokus na głównym zawartości jest dzięki obsłudze prawo gestów do otwierania i odrzucić zawartość dodatkowych szczegółów.  
  
-   **Zawsze** wymagają od użytkownika do wykonania niektórych jawnej gestu otworzyć dodatkową zawartość. Typowe gestów Otwórz obejmują:  
  
    -   **Umieść:** etykietki narzędzi lub innego nieinteraktywnego informacyjną zawartości  
  
    -   **Polecenie jawne:** prezenterze wbudowany  
  
    -   **Kliknij dwukrotnie pozycję wskaźnika otoczenia:** okno podręczne CodeLens  
  
-   **Zawsze** odrzucić zawartość szczegółów przy każdym naciśnięciu klawisza Esc.  
  
-   **Zawsze** należy wziąć pod uwagę w kontekście interfejsu użytkownika na obiekcie. Dla Prezenterzy zawartości, które umożliwiają interakcję w kontenerze należy rozważyć, czy mają być wyświetlane dodatkowe informacje o aktywacji, czyli może być uciążliwe dla przepływów pracy użytkownika.  
  
-   **Nigdy nie** wyświetlać zawartość na aktywowany, które można edytować lub zaprasza interakcji z użytkownikiem. To zachowanie może frustrować użytkowników, jeśli próby, przesuń kursor nad zawartości szczegółów standardowe zachowanie etykietka narzędzia jest natychmiast zamknąć, gdy kursor znajduje się już wzorca zawartości, który go utworzył.  
  
##  <a name="BKMK_SelectionModels"></a>Wybór modeli  
  
### <a name="overview"></a>Omówienie  
 Model wyboru to mechanizm służący do wskazywania i Potwierdź operacje na co najmniej jeden obiekt zainteresowania interfejsu użytkownika. W tym temacie omówiono wzorców interakcji zaznaczenia w edytory dokumentu programu Visual Studio: edytory tekstów, projektów i modelowania powierzchni.  
  
 Użytkownicy muszą mieć sposób wskazujący dla programu Visual Studio zajmują się oraz programu Visual Studio musi odpowiadać przewidywalnego opinii użytkowników o co działa na. Różnice lub powstanie między użytkownikiem i interfejsu użytkownika może skutkować użytkownika nie po raz pierwszy akcji, który może mieć niezamierzone skutki. Błąd przechodzi często niezauważalnie, dopóki użytkownik zobaczy następujący element nie istnieje lub została zmieniona. Wybór modeli są zatem jedną z najważniejszych części projektu interfejsu użytkownika. Chociaż wybór modeli w Visual Studio są zgodne z systemem Windows, mogą występować niewielkie różnice.  
  
 W programie Visual Studio, jak w systemie Windows wybór modeli różnią się w zależności od kontekstu, w którym występuje interakcji. Opcje mogą występować w cztery typy obiektów:  
  
-   Tekst  
  
-   Obiekty graficzne  
  
-   Listy i drzewa.  
  
-   Siatki  
  
 W tych obiektach istnieją trzy opcje:  
  
-   Ciągły  
  
-   Rozłączne  
  
-   Region  
  
#### <a name="scope"></a>Zakres  
 Składnik najważniejszych zaznaczenia jest zapewnienie użytkownik wie, w jakim oknie działają (aktywacji) i gdzie koncentruje się (wyborów). Visual Studio rozszerza funkcjonalność zarządzania okna w systemie Windows, ale schemat aktywacji jest taka sama: interakcji z oknem Przełącza fokus w oknie. Visual Studio ma dwa wskaźniki aktywacji: jeden dla okna dokumentów i jeden dla narzędzi systemu windows.  
  
 Dla okna dokumentów aktywne okno jest określane przez kartę okno dokumentu do przodu i zmianę koloru tła:  
  
 ![Wybór karty Active w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713 01_ActiveTab")  
  
 **Wybór Active karty**  
  
 Narzędzia systemu Windows aktywne okno jest określane przez zmianę koloru obszar paska tytułu okna narzędzi:  
  
 ![Narzędzie Active okno wyboru w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713 02_ActiveToolWindow")  
  
 **Aktywnego okna narzędzi przedstawiający zaznaczenia głównego węzła**  
  
 ![Wybór okna narzędzia nieaktywne w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713 03_InactiveToolWindow")  
  
 **Okno narzędzia nieaktywne, przedstawiający ukryty wybór węzła**  
  
 Gdy okno jest aktywne, zgodnie z modelami wyboru opisane w tej sekcji wytycznych wskazane jest jego fokus.  
  
#### <a name="context"></a>Kontekst  
 Visual Studio została zaprojektowana w celu zachowania silne koncepcji kontekstu, śledzenia, z których użytkownik pracuje. Tylko jedno okno jest aktywne, czy okno narzędzia lub dokumentu. Okno dokumentu znajdujące się najwyżej zachowuje zawsze ukryty zaznaczenia. Mimo że w oknie narzędzia może być fokus, okno dokumentu, który był ostatni aktywny Wyświetla zaznaczenie, nawet w nieaktywnym stanie. Jest to realizowane do przechowania w kontekście użytkownika w dokumencie, który ich edytowania, przedstawiający Visual Studio zachował ich stan, aby wrócić i bezproblemowo przesunięcia między narzędzia windows i windows dokumentu.  
  
### <a name="text-selection"></a>Zaznaczenie tekstu  
 Edytory wizualne Studio, które są ściśle tekstową, takich jak edytor tekstu wbudowanych, użyj tego samego modelu zaznaczenia tekstu i wyglądu opisanych w [myszą oraz wskaźniki](https://msdn.microsoft.com/en-us/library/dn742466.aspx) Windows User Experience Interaction Guidelines na stronie MSDN. Pionowy pasek o nazwie punkt wstawiania wskazuje fokus wprowadzania w edytorze tekstu. Punkt wstawiania jest piksela grubych i kolorowe jako odwrotność pojawia się niezależnie od za nią. Miga, zgodnie z stawki ustalanej przez **częstotliwość migania kursora** w **szybkości** karcie **klawiatury** apletu w Panelu sterowania.  
  
#### <a name="contiguous-and-disjoint-selection"></a>Wybór ciągły i rozłączne  
 Wybór w edytorze tekstu jest tylko ciągłe. Rozłączne tekst zaznaczenia nie są dozwolone, ale powinny być kierowane w edytorach obiektu graficznego. Wskaźnik myszy użytkownika znajduje się nad obszaru tekstu, kursor zmienia się dwuteownik. Jednym kliknięciem umieszcza kursor w edytorze tekstu w lokalizacji kliknij. Przytrzymując przycisk myszy rozpoczyna się zaznaczenie wyróżnienia i zwolnieniem przycisku myszy kończy się zaznaczenie wyróżnienia.  
  
#### <a name="region-selection-box-selection"></a>Pole Region (pole wyboru)  
 Program Visual Studio obsługuje opcje regionu w edytorze tekstu, a jest to pole wyboru. Pole wyboru umożliwia użytkownikowi wybierz region tekstu, który nie jest zgodna z strumienia zwykły tekst. Podobnie jak w przypadku zaznaczenia tekstu standardowego, wybór musi być ciągłe. Pole wyboru jest inicjowane, przytrzymując klawisz Alt, przeciągając myszą. Pole wyboru może być też inicjowane, przytrzymując klawisz Alt i klawisze Shift podczas używania klawiszy strzałek w celu wskazuje region zaznaczenia. Pole wyboru używa wyróżnienie zaznaczenia normalne i zawiera punkt wstawiania kursora migający na końcu obszaru zaznaczenia.  
  
 ![Regionalne &#40; pole &#41; Zaznaczenie w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713 04_BoxSelection")  
  
 **Pole Region (pole) w programie Visual Studio**  
  
#### <a name="text-selection-appearance"></a>Wygląd zaznaczenia tekstu  
 Można dostosować kolory używane dla aktywnych i nieaktywnych zaznaczenia w edytorze. Aby dostosować wygląd edytora, użytkownik może przejść do **Narzędzia > Opcje**, a następnie sprawdź w obszarze **środowiska > czcionki i kolory > Edytor tekstu**.  
  
### <a name="graphical-selection"></a>Wybór graficznego  
  
#### <a name="interaction"></a>Interakcji  
 Wybieranie obiektu graficznego może być skomplikowane i zależy od wielu czynników:  
  
-   **Edytor zaznaczenia głównego modelu.** Edytory zawierające obiektów graficznych mogą służyć do edycji tekstu lub siatki. Na przykład edytor może być edytorze tekstowym, który również obsługuje rozmieszczenie obiektów graficznych, takich jak projektanta XAML usługi Visual Studio. Obsługa wielu typów obiektów może mieć wpływ na sposób użytkownik wybiera grupy składające się z różnymi typami obiektów.  
  
-   **Obsługa Stany wyboru podstawowego i pomocniczego.** Edytor może zapewnić podstawowe i pomocnicze wybór stanów tak, aby obiekty można edytowane reagowaniu, wyrównane ze sobą, zmiany rozmiaru ze sobą, i tak dalej.  
  
-   **Obsługa edycji w miejscu.** Edytory można także umożliwić zawartość swoich obiektów graficznych do edycji. Na przykład prostokąt może także zawierać tekst wewnątrz, które mogą zostać zmienione przez użytkownika. Ponadto ten tekst może być wyśrodkowany lub uzasadnione. Edycji w miejscu wymaga bardziej szczegółowy poziom interakcji użytkownika i dlatego wymaga odpowiedni zestaw wizualnych prezentacji informacji o stanie dla użytkownika.  
  
#### <a name="mouse-interaction"></a>Interakcja z myszą  
  
|Dane wejściowe|Wynik|  
|-----------|------------|  
|Kliknij obiekt niezaznaczone|Wybiera obiekt i wyświetla linię kropkowaną i uchwytami, jeśli obiekt jest zmieniana.|  
|Kliknij wybranego obiektu|Aktywuje, jeśli obiekt obsługuje edycji w miejscu. Kliknięcie poza obiekt dezaktywuje tryb edycji w miejscu.|  
|Kliknij dwukrotnie plik obiektu|Otwiera kodzie obiekt do edycji i wstawić domyślny program obsługi zdarzeń, w razie potrzeby.|  
|Wskaż obiekt|Zmienia wskaźnik do przeniesienia kursora. Wygląd obiektu, takie jak jego jasność lub kolor, mogą ulec zmianie.|  
|Wskaż uchwyt zaznaczenia|Zmienia wskaźnik myszy znajduje się kursor zmiany rozmiaru. Dla obiektów, które obsługuje obracania niektóre uchwytami może zmienić wskaźnik do obracania kursora jako wskaźnik myszy znajduje się w inny sposób (na przykład przenieść dalej od komputera) względem uchwyt zaznaczenia.|  
|Przeciągnij|Nawet jeśli nie wybrano wcześniej obiektu, zmiany wskaźnik do kursora przenoszenia i przenosi obiekt.|  
|Edytor traci fokus|Dezaktywuje tryb edycji w miejscu, mimo że obiektu zachowuje zawartość i wyglądu, który miał podczas ostatniego stanu operacji/wyboru.|  
|Wybieranie obiektów|Wskazuje obramowanie, linia kropkowana lub innych wizualnie różne przetwarzania, aby wyróżnić granic obiektu.|  
|Zmiana rozmiaru wybranego obiektu|Wskazuje uchwyty zaznaczenia.<br /><br /> Obiekt o zmiennym rozmiarze ma osiem uchwytów reprezentujący każdego kierunek, w którym można zmieniać. Mniejszej liczby dojść mogą być używane, jeśli obiektu można zmieniać tylko w niektórych kierunkach. Gdy użytkownik zmienia rozmiar obiektu, do której osiem uchwytów nie jest interaktywny, można użyć czterech uchwytów. Rozmiary uchwyt powinien ograniczeni do metryki obramowania i krawędź okna z **GetSystemMetrics** funkcja interfejsu API do rozmiaru proporcjonalnie do rozdzielczości ekranu.<br /><br /> ![Uchwyty zmiany rozmiaru](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713 05_ResizeHandles")|  
|Obróć wybranego obiektu|![Uchwyty obracania](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713 06_Rotate")|  
  
#### <a name="keyboard-interaction"></a>Klawiatury  
  
|Dane wejściowe|Wynik|  
|-----------|------------|  
|Tab|Przenosi fokus wskaźnika między logiczną kolejnością obiektów w edytorze. Może to być od lewej do prawej lub góry do dołu w zależności od **TabIndex** (lub równoważnego) wartość właściwości, kolejność tworzenia obiektów i ogólnego przeznaczenia edytora. Shift + Tab odwraca kierunek wskaźnika fokus.|  
|SPACJA|Aktywuje Tryb przesuwania podczas naciśnięcie klawisza jest obsługiwany. Wejście myszy dodatkowe jest wymagana do kadrować pozycji okienka ekranu.|  
|Ctrl+Spacja|Aktywuje tryb powiększenia, gdy utrzymywana jest naciśnięcie klawisza. Wejście myszy dodatkowe jest wymagana, aby zwiększyć lub zmniejszyć współczynnika powiększenia.|  
|Ctrl + Alt + znak Minus|Zmniejsza współczynnika powiększenia o jeden poziom.|  
|Ctrl + Alt + znak Plus|Zwiększa współczynnika powiększenia o jeden poziom.|  
|Ctrl lub SHIFT|Dodaje obiekt do wyboru grupy. CTRL umożliwia również usunąć obiekty osobno z grupy wyboru.|  
|Enter|Wykonuje polecenie domyślne dla obiekt (zazwyczaj Otwórz lub edytować).|  
|F2|Aktywuje edycji w miejscu dla obiekt.|  
|Klawisze strzałek|Przenosi wybrane obiekty w kierunku Strzałka naciśnięty, w małych przyrostów (na przykład 1 piksela naraz)|  
|CTRL + klawisze strzałek|Przenosi wybrane obiekty w kierunku Strzałka wciśnięty większe przyrostów (na przykład 10 pikseli naraz)|  
|Shift + Strzałka w klawisze|Zmienia rozmiar wybrane obiekty w odpowiednich kierunek, w małych przyrostów (na przykład 1 piksela naraz)|  
|Ctrl + Shift + klawisze strzałek|Zmienia rozmiar wybrane obiekty w odpowiednich kierunek większe przyrostów (na przykład 10 pikseli naraz)|  
  
 Gdy użytkownicy edycji kontrolek w miejscu, może być uzasadnione dla obiektów automatycznie zmienić rozmiar przy użyciu danych wejściowych użytkownika. Na przykład jeśli użytkownik edytuje formant etykiety, etykieta powinna rosnąć do wyświetlania tekstu, który użytkownik wpisane. Jeśli nie zostanie to zrobione, użytkownik musi ręcznie rozmiar formantu po edycji tekstu. Jeśli użytkownik ma wiele formantów, staje się on rote i nieproduktywne zadań.  
  
#### <a name="graphical-containers"></a>Kontenery graficznego  
 W niektórych przypadkach edytory graficzne Podaj kontenery innych obiektów graficznych, takich jak kontrolki panelu formularzy systemu Windows albo formantu siatki układu projektanta HTML. Jeśli Edytor zapewnia kontenerami dla innych obiektów graficznych, następującego modelu zaznaczenia należy użyć tylko kontenera (obiektach wykonaj kontenera standardowe modelu w postaci opisane powyżej):  
  
|Dane wejściowe|Wynik|  
|-----------|------------|  
|Jednym kliknięciem w kontenerze|Wybiera obiekt kontenera bez bezpośrednio zaznaczenie wszystkich obiektów zawartych w niej. Kontener może przenieść lub zmiany rozmiaru standardowej myszki i klawiatury (jak opisano powyżej). Zawarte obiekty są przenoszone w odniesieniu do tego kontenera, ale zawarte obiekty nie są rozmiaru, chyba że są one również bezpośrednio wybrane.|  
|Umieść kursor nad region granic kontenera|Włącza wskaźnik myszy do przeniesienia kursora, wskazującą, czy można przenosić kontenera.|  
|Przeciągnij region granic kontenera|Zmiany Przenieś kursor myszy i przenosi kontenera (i zawarte obiekty w ramach). Nie można przenieść kontener bez uprzedniego wybierane za pomocą jednego kliknięcia.|  
|Jednym kliknięciem do obiektu w kontenerze|Odznacza kontenera (jeśli zostały wybrane) i wybiera klikniętej obiektu.|  
|SHIFT + kliknij lub Ctrl + kliknięcie obiekt i/lub kontenera|Dodaje klikniętej obiektu do istniejącego zaznaczenia w grupie zaznaczenia. Jeśli obiekt klikniętej jest już członkiem grupy wyboru, zostanie ono usunięte z grupy wyboru.|  
  
 Zawarte obiekty należy stosować się do modelu zaznaczenia podstawowe, zgodnie z opisem w poprzedniej sekcji. Z użytecznością testowania projektanta formularzy systemu Windows, użytkownicy oczekiwano bezproblemowy dostęp do zawartych obiektów bez pośredniczące kroków (narzucone przez obiekt zawierania).  
  
#### <a name="disjoint-and-region-selections"></a>Rozłączne i regionu  
 Edytory graficzne obiektu powinien obsługiwać rozłącznego wybrane opcje. Należy pamiętać, że grafiki nie są wyświetlane wygląd formantu dla programu Visual Studio. Zobacz [wygląd Wybieranie obiektu graficznego](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) dla szczegółowe specyfikacje visual.  
  
 ![Rozłączne i region selektory](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713 07_DisjointRegionSelectors")  
  
 **Rozłączne zaznaczenia**  
  
 Edytory graficzne określić opcje region ze wskaźnikiem wybór typu ustawiony na marquee. Jeśli edytora graficznego obsługuje innych obiektów (np. tekst), następnie opcje region może nie być możliwe w zależności od ograniczenia te typy obiektów.  
  
 ![Ramki zaznaczenia](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713 08_MarqueeSelection")  
  
 **Ramki zaznaczenia**  
  
#### <a name="primary-and-secondary-selections"></a>Opcje podstawowe i pomocnicze  
 Niektóre edytory graficzne obiektu Zezwalaj użytkownikowi na edytowanie lub Dopasuj obiekty należące do grup. W takim przypadku pojęcie głównych i dodatkowych opcji musi zostać wprowadzony. Podstawowy zaznaczenie jest obiekt, do którego wszystkie inne obiekty odpowiedzi dla operacji grupy. Obiekt, który użytkownik wybiera najpierw staje się podstawowym kontroli, a wybór dodatkowej stają się kolejne zaznaczenia. Zaznaczenie główne ma różne visual sposób postępowania z selection(s) dodatkowej, aby wskazać obiektu, który jest kluczem podstawowym:  
  
 ![Wybór podstawowych i pomocniczych](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713 09_PrimarySecondary")  
  
 **Zaznaczenie główne z dwóch opcji dodatkowej**  
  
####  <a name="BKMK_GraphicalObjectSelectionAppearance"></a>Wygląd Wybieranie obiektu graficznego  
 Uchwyty zaznaczenia są rysowane wokół obwiedni obiektu w układzie prostokątne kwadratów. Poniższej tabeli przedstawiono przykłady różnych stanów, które obiekt graficzny może mieć z uchwyt zmiany rozmiaru i wyglądu edycji w miejscu. Rozmiar dojść powinien powiązane krawędź okna i przy użyciu metryk krawędzi **GetSystemMetrics** interfejsu API.  
  
|Stan|Wygląd|Szczegóły dotyczące programu Visual|  
|-----------|----------------|--------------------|  
|**Niezaznaczony**|Domyślny|![Domyślny stan przycisku](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713 10_DefaultState")||  
|**Zaznaczenie główne**|O zmiennych rozmiarach|![Uchwyty zmiany rozmiaru zaznaczenia głównego z](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713 11_PrimaryResize")|![Zaznaczenie główne z zmienić rozmiar uchwytów &#40; powiększony &#41; ] (../../extensibility/ux-guidelines/media/0713-12_primaryresizezoom.png "0713 12_PrimaryResizeZoom")|  
|**Zaznaczenie główne**|Nie o zmiennych rozmiarach|![Uchwyty zmiany rozmiaru zaznaczenia głównego bez](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713 13_PrimaryNoResize")|![Zaznaczenie główne bez zmiany rozmiaru uchwytów &#40; powiększony &#41; ] (../../extensibility/ux-guidelines/media/0713-14_primarynoresizezoom.png "0713 14_PrimaryNoResizeZoom")|  
|**Zaznaczenie główne**|Zablokowane|![Zaznaczenie główne zablokowane](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713 15_PrimaryLocked")|![Zaznaczenie główne zablokowany &#40; powiększony &#41; ] (../../extensibility/ux-guidelines/media/0713-16_primarylockedzoom.png "0713 16_PrimaryLockedZoom")|  
|**Wybór dodatkowej**|O zmiennych rozmiarach|![Uchwyty zmiany rozmiaru dodatkowej wybór z](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713 17_SecondaryResize")|![Wybór dodatkowej z zmienić rozmiar uchwytów &#40; powiększony &#41; ] (../../extensibility/ux-guidelines/media/0713-18_secondaryresizezoom.png "0713 18_SecondaryResizeZoom")|  
|**Wybór dodatkowej**|Nie o zmiennych rozmiarach|![Uchwyty zmiany rozmiaru wybór dodatkowej bez](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713 19_SecondaryNoResize")|![Wybór dodatkowej bez zmiany rozmiaru &#40; powiększony &#41; ] (../../extensibility/ux-guidelines/media/0713-20_secondarynoresizezoom.png "0713 20_SecondaryNoResizeZoom")|  
|**Wybór dodatkowej**|Zablokowane|![Wybór dodatkowej zablokowane](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713 21_SecondaryLocked")|![Wybór dodatkowej zablokowany &#40; powiększony &#41; ] (../../extensibility/ux-guidelines/media/0713-22_secondarylockedzoom.png "0713 22_SecondaryLockedZoom")|  
|**Aktywne interfejsu użytkownika**|Domyślny|![Stan aktywny UI](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713 23_UIActive")|![Interfejs użytkownika stanu aktywnego &#40; powiększony &#41; ] (../../extensibility/ux-guidelines/media/0713-24_uiactivezoom.png "0713 24_UIActiveZoom")|  
  
### <a name="view-selection-models"></a>Modele wybór widoku  
  
#### <a name="tree-view"></a>Widok drzewa  
 Zaznaczenie w widoku drzewa jest wyświetlana z prostego wyróżnienia. Gdy użytkownik kliknie nazwy węzła lub ikony węzła, staje się wybrany węzeł. Trójkątny symboli na lewo od węzła rozwiń węzeł lub kontraktu do drzewa, ale nie ma wpływu na wybór użytkownika, z jednym wyjątkiem: po Zwijanie węzła nadrzędnego, gdy zaznaczenie ma na element podrzędny tego węzła, Zaznaczenie przesuwa się do obiektu nadrzędnego.  
  
 ![Typowy widok drzewa w programie Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713 25_TreeView")  
  
 **Typowy widok drzewa w programie Visual Studio**  
  
 Widok drzewa może obsługiwać opcje ciągłe i rozłączny, nawet na wielu poziomach drzewa. Ciągłe ani odłączonego wielokrotny przeprowadza się w węzłach drzewa widoczne. Jeśli węzeł jest zwinięte, rozłącznego zaznaczenie zostanie utracone, i węzeł, który zwinięto uzyskuje zaznaczenia. Dzięki temu użytkownik może zobaczyć węzły, które będzie mieć wpływ na działanie. Węzły są zwinięte, staje się jasne węzły, które mogą mieć wpływ na.  
  
 Po wybraniu węzła nadrzędnego operacji należy zastosować do elementu nadrzędnego, chociaż może się zdarzyć, gdy warto operacji stosuje się do obiektu nadrzędnego i wszystkie jego elementy podrzędne. W takim przypadku należy zapewnić dodatkowe interfejsu użytkownika podczas operacji, takich jak pole wyboru lub opcja "Zastosuj do wszystkich obiektów podrzędnych" Udostępnij jawne użytkownikowi okno dialogowe potwierdzenia.  
  
##### <a name="renaming"></a>Zmiana nazwy  
 Jeśli węzłów w drzewie obsługuje zmianę nazwy, zmiana nazwy ma się odbywać w miejscu. Operacja w miejscu powinna być standardowego we wszystkich kontrolek drzewa w programie Visual Studio. Podaj polecenie zmiany nazwy, które natychmiast aktywuje tryb edycji w miejscu z zaznaczenia tekstu obejmujących całą nazwę tego węzła, który może zaakceptować danych wejściowych użytkownika. Jeśli węzeł reprezentuje plik, nazwa pliku powinna mieć rozszerzenie. Zaznaczenie wyróżnienia powinna zawierać tylko treść nazwę pliku i nie rozszerzenia.  
  
|Dane wejściowe|Wynik|  
|-----------|------------|  
|klawisz ENTER|Zatwierdza operacji zmiany nazwy|  
|Klawisz ESC|Anuluje operację zmiany nazwy|  
|Kliknięcie poza region edycji w miejscu|Zatwierdza operacji zmiany nazwy|  
|Cofnij|Podaj łatwe Cofnij, aby anulować operację zmiany nazwy|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>Wybór wewnątrz listy i formanty siatki  
 Klucza koncepcja w opcji wyboru z listy jest, że jest ona oparta na wiersz, co oznacza, że po dokonaniu wyboru cały wiersz został wybrany jako jednostka. Z kolei siatki umożliwiają komórki, aby wybrać bez wpływu na innych aspektów wiersza. Siatki może także zawierać hierarchia zagnieżdżonych wierszy (takie jak kontrolki TreeGrid) umożliwiające gałęzie całej hierarchii, które można wybrać i zostanie usunięte zaznaczenie przez interakcji z wierszy nadrzędnych. Wybór na listach jest wyświetlany przez kolor proste wyróżnienia na cały wiersz danych. Fokus jest wyświetlany przez jednopikselowymi kropkowanej obramowanie bieżącego można edytować wiersza lub komórki (wiersz, jeśli wszystkie komórki są tylko do odczytu).  
  
> [!NOTE]
>  **Fokus** i **wybór** są różne pojęcia. *Fokus* wskazanie, który interfejsu użytkownika elementu jest przeznaczona dla danych wejściowych nie jawnie skierowane na inny obiekt, podczas gdy *wybór* odwołuje się do stanu włączenia obiektu w zestawie obiekty, dla których kolejnych może mieć miejsce operacje.  
  
 Wybrane elementy na listach może być ciągłe, odłączony, lub regionu. Gdy wielokrotny są dozwolone, ciągły i wybór rozłącznego powinny być zawsze obsługiwane, podczas obsługę opcji region (pole) jest opcjonalna. Opcje region są inicjowane przez przeciągnięcie w treści listy biały znak.  
  
|Obiekt|Wybór|  
|------------|---------------|  
|Lista|Ciągły|Zawsze obsługiwane (gdy jest wielokrotny są dozwolone).|  
|Lista|Rozłączne|Zawsze obsługiwane (gdy jest wielokrotny są dozwolone).|  
|Lista|Region|Obsługa opcjonalne. Zainicjowane przez przeciąganie myszy w treści listy biały znak.|  
  
 Kliknij raz na liście zaznacza wiersz, w którym wystąpił kliknij. Jeśli użytkownik kliknij komórkę listy, która obsługuje edycji w miejscu, komórki również natychmiast jest aktywowany do edycji w miejscu. W przeciwnym razie cały wiersz natychmiast jest zaznaczone i przedstawia wyróżnienie.  
  
 Przeciąganie w treści listy wykonuje jedno z trzech zdarzeń:  
  
-   Inicjuje pole region, jeśli je obsługuje listy i w dół wskaźnik myszy znajduje się w biały znak  
  
-   Inicjuje operacji przeciągnij i upuść, gdy lista komórki lub wiersza obsługuje trwa źródła przeciągania  
  
-   Wybiera bieżącego wiersza.  
  
##### <a name="in-place-editing"></a>Edycji w miejscu  
 Podczas edycji w miejscu jest dozwolona, istnieją dwa podstawowe modele: selektora prostego edycji właściwości i kontroli. Za pomocą formantu edycji proste zawartość jest zaznaczony i gotowa do użytkownika danych wejściowych zaraz po aktywowaniu edycji w miejscu. W przypadku, gdy selektor właściwości jest zaimplementowana, przycisku, który wywołuje selektora właściwości jest wyświetlany po aktywowaniu tryb edycji w miejscu, a bieżące zaznaczenie nie jest wyróżniony. Przycisk selektor powinien być wyrównany do prawej w komórce. Przykłady edycji w miejscu, można znaleźć **okna właściwości** i **listy zadań** w programie Visual Studio.  
  
##### <a name="keyboard-support"></a>Obsługa klawiatury  
 Obsługa klawiatury do wyboru w listach i siatki zgodna z konwencjami standardowych systemu Windows:  
  
-   Klawisze strzałek nawigowania na liście, wybierając każdej komórki/wiersza w miarę przenoszenia fokus.  
  
-   Shift + Strzałka w wykonuje wybór ciągły w kierunku klawiszy strzałek.  
  
-   CTRL + Strzałka w następuje Spacja Przełącza między Dodawanie i usuwanie elementów listy z zaznaczenia, tworzenie rozłącznego zaznaczenia.  
  
-   Siatki, zawierających zagnieżdżone hierarchie wiersza nadrzędnego rozszerza Strzałka w prawo i Strzałka w lewo zwija jeden.  
  
-   Klawisz Tab przenosi fokus między komórkami w bieżącym wierszu, jeśli komórki są edytowalne.  
  
-   Klawisz Enter wykonuje polecenie domyślne na element na liście (często **Otwórz**).  
  
-   Klawisz F2 aktywuje edycji w miejscu, w obecnie zaznaczonej komórce.  
  
##  <a name="BKMK_PersistenceAndSavingSettings"></a>Trwałość i zapisywania ustawień  
  
### <a name="overview"></a>Omówienie  
 Mimo że każdego składnika oprogramowania w programie Visual Studio jest zazwyczaj odpowiedzialny stanu i trwałości, Visual Studio automatycznie zapisuje ustawienia w niektórych przypadkach, takich jak z rozmiarów okna i pozycji. W poniższej tabeli jest kombinacją ustawień zapisanych automatycznie i ustawienia, które wymaga jawnego użytkownika lub zaprogramowane podjęcia działania.  
  
|Obiekt|Co należy zachować|Kiedy należy zapisać|Lokalizacji zapisu|  
|------------|------------------|------------------|-------------------|  
|Wybór obiektu (na przykład wiersz kodu)|Punkt przerwania w wierszu kodu<br /><br /> Skrót użytkownika skojarzonego z wierszem kodu|Po zapisaniu projektu|**Opcji użytkownika (.suo)** pliku projektu|  
|Okno dialogowe|Lokalizacja okna dialogowego, jeśli ma on przeniesiony<br /><br /> Widok, który użytkownik ostatnio używana w oknie dialogowym|Po zamknięciu okna dialogowego<br /><br /> Gdy kończy się sesja programu Visual Studio|W pamięci<br /><br /> Rejestr w **HKEY_Current_User**|  
|Okno|Rozmiar i położenie okna|Po zamknięciu okna<br /><br /> Podczas zmiany trybu programu Visual Studio<br /><br /> Gdy kończy się sesja programu Visual Studio|**Opcji użytkownika (.suo)** pliku projektu<br /><br /> Plik opcji niestandardowych ustawień okna|  
|dokument|Bieżące zaznaczenie w dokumencie<br /><br /> Widok dokumentu<br /><br /> Ostatnich kilku miejscach odwiedzoną przez użytkownika|Po zapisaniu dokumentu|**Opcji użytkownika (.suo)** pliku projektu|  
|Project|Odwołania do plików<br /><br /> Odwołania do katalogów znajdujących się na dysku<br /><br /> Odwołania do innego oprogramowania<br /><br /> Składniki<br /><br /> Informacje o stanie o samym projekcie|Po zapisaniu projektu|Plik projektu|  
|Rozwiązanie|Odwołania do projektów<br /><br /> Odwołania do plików|Po zapisaniu projekt lub rozwiązanie|**Solution (.sln)** pliku|  
|Ustawienia w **Narzędzia > Opcje**|Dostosowania klawiatury<br /><br /> Dostosowywanie paska narzędzi<br /><br /> Schematy kolorów|Gdy **Narzędzia > Opcje** zamknięciu okna<br /><br /> Gdy kończy się sesja programu Visual Studio|Rejestr w **HKEY_Current_User**|  
  
 Co użytkownik wykonuje i gdy robią, określa, czy ustawienia są zapisywane w pamięci (podczas sesji), zapisane na dysku (między sesjami jako ustawienie rejestru), w ramach projektu lub rozwiązania do pliku, w ramach **rozwiązania Opcje (.suo)** pliku lub jak niestandardowe ustawienia plików jedynie składnika oprogramowania zna. Powyższej tabeli przedstawiono kilka zdarzeń, w którym można zapisać ustawień. Istnieją jednak pozostałych godzinach, w których można zapisać stanu:  
  
-   Gdy użytkownik zmieni lokalizacji w obrębie okna dialogowego lub okna  
  
-   Gdy użytkownik przenosi fokus do innego okna  
  
-   Gdy użytkownik zmienia z projektu tryb debugowania.  
  
-   Gdy użytkownik się wylogowuje swojego konta  
  
-   Gdy komputer przechodzi w stan hibernacji lub wyłączania  
  
-   Gdy komputer/dysku ma można ponownie sformatowany i ponownie  
  
### <a name="window-configurations"></a>Konfiguracje okien  
 Konfiguracja okna jest przedstawienie podstawowe środowisko projektowe — jest schemat, składające się z listy obecnych okna narzędzi oraz sposób, w którym są uporządkowane. Dla systemu windows zarządza IDE (IDE windows) informacje o układzie dla poszczególnych użytkowników, jest trwały, więc po użytkownika powoduje uruchomienie, IDE, układ okna prawdopodobnie jest taka sama jak podczas ostatniego zakończył działanie programu Visual Studio. Stan i pozycji IDE systemu Windows jest trwały w niestandardowych opcji pliku w formacie XML. Okna narzędzia, które są tworzone przez pakiety załadowana do środowiska IDE utrwalenia informacji o ich stan w rejestrze i może lub nie może być na użytkownika.  
  
#### <a name="profile-specific-layouts"></a>Układy specyficzne dla profilu  
 Każdy profil zawiera narzędzie układów okien, znane osoby określonego dewelopera porządkowanie (Visual C++ deweloperzy powinien pojawić się **Eksploratora rozwiązań** po lewej stronie IDE, gdy deweloperzy C# powinien pojawić się **Eksplorator rozwiązań** po prawej stronie). Załadowano układów okien specyficzne dla profilu po wybraniu profilu podczas uruchamiania. Autor pakietu należy określić układ okna najodpowiedniejsze do obsługi ich klienta, wiedząc, że zmiany wprowadzone przez użytkownika do konfiguracji okna następnie zostaną utrwalone.  
  
##  <a name="BKMK_TouchInput"></a>Wprowadzania dotykowego  
 Użytkownicy są coraz bardziej przy użyciu rozwoju firmy na urządzeniach touch. Istnieją jednak bariery, które utrudnia korzystanie z narzędzi programistycznych na urządzeniach touch. Użytkownicy będą oczekiwać naszych produktów, aby zapewnić środowisko touch niezawodnych i dokładne. Celem wytycznych ma ułatwić podjęcie decyzji o jakie funkcje dotykowe uwzględnienie i zachęca obsługi dotykowej spójne w Visual Studio oraz pokrewnych produktów.  
  
### <a name="levels-of-experience"></a>Poziomy doświadczenia  
 Następujące poziomy środowisko mają służyć jako przewodnik ułatwia zespoły zdecyduj, jakie funkcje dotykowe oferowanie na podstawie ich żądanego poziomu zainteresowania inwestycji w kontakcie.  
  
-   **Podstawowe środowisko** jest dla zespołów, które chcą udostępniać touch możliwości, więc nie ma elementów ends wiadomości w całym ich pracy.  
  
-   **Zoptymalizowanych pod kątem obsługi** jest przeznaczona dla zespołów, które chcą udostępniać najwięcej możliwości touch typowe (na przykład te zwykle dostępne w aplikacji przeglądarki internet).  
  
-   **z podwyższonym poziomem uprawnień środowisko** jest przeznaczona dla zespołów, które chcesz dodać możliwości, takie jak gestów lub innych funkcji opcjonalne, które mogą ułatwić ich aplikacji touch najpierw przyjazna.  
  
||Podstawowe środowisko|Zoptymalizowane środowisko|Środowiska z podniesionymi uprawnieniami|  
|-|----------------------|--------------------------|-------------------------|  
|Umożliwia użytkownikom...|Usuń kod i rozwiązania/projektu-odczytu bez zakończenia wiadomości|Wykonywanie zadań konserwacji, refactors i nawigacji|Działać w środowisku spójne, intuicyjne i płynne bez obaw|  
|Edytor|Przesuwanie dotykowe i zaznaczenia<br /><br /> Pasek przewijania touch do szybkiego dostępu i naciśnij klawisz + przeciągnij|Powiększanie uszczypnięcia<br /><br /> Szybkie przewijania<br /><br /> Wybór<br /><br /> Łatwe korzystanie z menu kontekstowego||  
|Górny narzędzia systemu windows|Przesuwanie listy<br /><br /> Zaznaczanie elementów<br /><br /> Pasek przewijania touch do szybkiego dostępu i naciśnij klawisz + przeciągnij|Element łatwe przewijanie i zaznaczenia||  
|Dostosowywanie okien||Zmień rozmiar okna<br /><br /> Szybki dostęp||  
|Dobrze dokumentu||Nawigację między otwartych plików||  
|Gestów||Upewnij się, że gestów wspólnej pracy w środowisku IDE|Czynności na podstawie gestu<br /><br /> Obsługa przeciągania i upuszczania oraz projektantów|  
|Inne zagadnienia|||Klawiatura ekranowa niestandardowych|  
  
#### <a name="gestures"></a>Gestów  
 Gestów udostępnić użytkownikom skrótów do poleceń, które w przeciwnym razie mogą wymagać interakcji bardziej skomplikowane. Znajduje się wskazówki dotyczące systemu Windows w [powszechnych gestów dotykowych dla aplikacji pulpitu](http://msdn.microsoft.com/en-us/library/windows/desktop/dd940543\(v=vs.85\).aspx)i wykonaj tę wskazówkę dla większości gesty, łącznie z prostych gestów, takich jak przesuwać i powiększać.