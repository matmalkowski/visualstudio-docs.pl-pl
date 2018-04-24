---
title: Analiza ramek grafiki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.frameanalysis
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9fe34c421d06fea1e4eefc064d344727382ca1d8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="graphics-frame-analysis"></a>Analiza klatek grafiki
Użyj analizy ramek grafiki w analizatora grafiki programu Visual Studio do analizowania i zoptymalizować wydajność renderowania Direct3D gier i aplikacji.  

## <a name="frame-analysis"></a>Analiza ramek  
 Analiza ramek używa tych samych informacji, które są przechwytywane w pliku dziennika grafiki w celach diagnostycznych, używa go do podsumowania wydajności renderowania zamiast tego. Informacje o wydajności nie jest rejestrowane w dzienniku podczas przechwytywania. Zamiast tego informacje o wydajności jest generowany później, podczas analizy ramek według czasu zdarzenia i zbieranie statystyk jako odtwarzania ramki. Takie podejście ma kilka zalet w porównaniu do rejestrowania informacji o wydajności podczas przechwytywania:  
  
-   Analiza ramek można średnie wyniki z poszczególnymi wielu odtworzeniami tej samej ramki upewnij się, że podsumowania wydajności jest statystycznie dźwięku.  
  
-   Analiza ramek mogą generować informacji o konfiguracjach sprzętu i urządzenia innego niż ten, na którym zostało przechwycone dane wydajności.  
  
-   Analiza ramek, może spowodować wygenerowanie nowego podsumowania wydajności wcześniej przechwycone informacje — na przykład, jeśli wersji sterowników procesora GPU są zoptymalizowane lub ujawniać dodatkowe funkcje debugowania.  
  
 Oprócz tych korzyści analizy ramek można także wprowadzić zmiany w sposobie prezentacji ramki podczas odtwarzania, dzięki czemu może ona dowiedzieć się, jak te zmiany mogą wpłynąć na wydajność renderowanie aplikacji. Te informacje służy do określania między potencjalnych strategii optymalizacji, bez konieczności ich wszystkich wdrażania, a następnie przechwycić i porównaj wszystkie wyniki samodzielnie.  
  
 Mimo że analizy ramek jest przeznaczone głównie mają pomóc osiągnąć większą wydajność renderowania, jego jednakowo pozwalają osiągnąć lepszą jakość visual dla elementu docelowego wydajności danego lub zmniejszyć zużycie energii procesora GPU.  
  
 Aby wyświetlić pokaz analizy ramek czynności dla aplikacji, możesz obserwować [analiza ramek grafiki programu Visual Studio](http://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) wideo w witrynie Channel 9.  
  
## <a name="using-frame-analysis"></a>Za pomocą analizy ramek  
 Przed użyciem analizy ramek, należy przechwytywanie informacji graficznych z aplikacji podczas jego wykonywania, podobnie jak w przypadku przy użyciu jednej z pozostałych narzędzi analizatora grafiki. Następnie w oknie grafiki dziennika dokumentu (.vsglog) wybierz **analizy ramek** kartę.  
  
 ![Wybierz kartę analizy ramek](media/pix_frame_analysis_select_tab.png "pix_frame_analysis_select_tab")  
  
 Po zakończeniu analizy, wyniki są wyświetlane. W górnej części kartę analizy ramek Wyświetla oś czasu i tabelę podsumowania. W dolnej części Wyświetla tabele Szczegóły. Jeśli błędy lub ostrzeżenia zostały wygenerowane podczas odtwarzania, są podsumowywane powyżej osi czasu; z tego miejsca można użyć łącza, aby dowiedzieć się więcej na temat błędów i ostrzeżeń.  
  
### <a name="interpreting-results"></a>Interpretowanie wyników  
 Przy interpretowaniu wyników każdego Variant, możesz może wnioskować przydatnych informacji o aplikacji do renderowania, wydajności i zachowania. Aby uzyskać więcej informacji na temat renderowanie wariantów, zobacz [wariantów](#Variants) dalszej części tego artykułu.  
  
 Niektóre wyniki wskazują bezpośrednio, wpływ wydajności renderowania wariantu:  
  
-   Wariant dwuliniowa filtrowania tekstury wykazało wzrost wydajności, za pomocą dwuliniowa tekstury filtrowanie w aplikacji wyświetli podobne wzrost wydajności.  
  
-   Jeśli variant okienka ekranu 1 x 1 był wzrost wydajności, następnie zmniejszenie jego rozmiar docelowy renderowania w aplikacji poprawi wydajność jego renderowania.  
  
-   Wariant kompresji tekstury BC wykazało wzrost wydajności, następnie w aplikacji przy użyciu BC tekstury kompresji wyświetli podobne wzrost wydajności.  
  
-   Jeśli 2xMSAA variant niemal tym samym wydajności jako wariant 0xMSAA, można włączyć 2xMSAA w aplikacji, aby poprawić jakość renderowania bez ponoszenia kosztów wydajności.  
  
 Inne wyniki może sugerować głębiej, aspekty wpływ na wydajność aplikacji:  
  
-   Jeśli 1 x 1 wariant okienka ekranu przedstawia bardzo duży wzrost wydajności, fillrate więcej niż dostępna prawdopodobnie jest korzystanie z aplikacji. Jeśli ten typ variant nie wzrost wydajności, aplikacji jest prawdopodobnie przetwarzania zbyt wiele wierzchołków.  
  
-   Jeśli variant Format docelowy renderowania 16bpp znaczący wzrost wydajności, aplikację prawdopodobnie zużywa zbyt dużej ilości pamięci przepustowość.  
  
-   Wariant wymiarów tekstury Half/Quarter pokazuje znaczący wzrost wydajności, Twoje tekstury prawdopodobnie zajmują zbyt dużej ilości pamięci, używać zbyt dużą ilość przepustowości czy Niewydajne obsługi pamięci podręcznej tekstury. Jeśli ten wariant pokazuje żadnych zmian w wydajności, prawdopodobnie można tekstury większych i bardziej szczegółowe bez płatności spadek wydajności.  
  
 Gdy są dostępne liczniki sprzętu, można używać ich bardzo szczegółowych informacji o dlaczego może niewystarczający wydajności renderowanie aplikacji. Wszystkie urządzenia 9.2 i wyższy poziom funkcji obsługuje zapytań zamknięcia głębokość (**pikseli zamknięte** licznika) i sygnatur czasowych. Inne liczników sprzętowych mogą być dostępne, w zależności od tego, czy producenta procesora GPU ma zaimplementowany liczników sprzętowych i widoczne je w jej sterownika. Te liczniki umożliwiają potwierdzić przyczynę precyzyjne wyniki wyświetlane w tabeli podsumowania — na przykład można określić, czy overdraw jest czynnikiem, sprawdzając wartość procentowa pikseli, które zostały zamknięte przez test głębi.  
  
### <a name="timeline-and-summary-table"></a>Oś czasu i tabelę z podsumowaniem  
 Domyślnie osi czasu i podsumowanie tabeli są wyświetlane, a pozostałe sekcje są zwinięte.  
  
#### <a name="timeline"></a>Oś czasu  
 Oś czasu zawiera omówienie chronometrażu wywołanie rysowania względem siebie. Ponieważ paski większych odpowiada wydłużenie czasu rysowania, służy ona odnajdywanie najdroższych wywołań rysowania w ramce. Gdy przechwyconej ramce zawiera dużą liczbę wywołań rysowania, wiele rysowania przez wywołania są połączone w jeden pasek o długości to suma tych Rysuj wywołania.  
  
 ![Oś czasu przedstawia rysowania&#45;wywołać kosztów. ] (media/pix_frame_analysis_timeline.png "pix_frame_analysis_timeline")  
  
 Wskaźnik na pasku zdarzenie wywołanie rysowania, które odpowiada pasku. Na pasku zaznaczenie powoduje, że listy zdarzeń, które mają być synchronizowane tego zdarzenia.  
  
#### <a name="table"></a>tabela  
 Liczby osi czasu przedstawiono względną wydajność każdego wariantu renderowania dla każdego wywołania rysowania względem odwzorowanie domyślne aplikacji. Każda kolumna zawiera wariant różnych renderowania i każdego wiersza reprezentuje wywołanie rysowania różnych, który określono w lewej kolumnie; w tym miejscu możesz wykonać łącze, aby zdarzeń w oknie Lista zdarzeń grafiki.  
  
 ![Podsumowanie tabeli przedstawiono różne varients. ] (media/pix_frame_analysis_summary.png "pix_frame_analysis_summary")  
  
 Z drugiej kolumny lewej tabeli podsumowania Wyświetla czas renderowania linii bazowej aplikacji, oznacza to, czas potrzebny do renderowania domyślnej aplikacji do ukończenia wywołania rysunku. Pozostałe kolumny zawierają względną wydajność każdego wariantu renderowania jako procent linii bazowej, tak, aby lepiej widoczne czy poprawia wydajność. Wartości procentowe przekracza 100 procent trwało dłużej niż linii bazowej — to znaczy wydajności zakończył działanie — i wartości procentowe mniejsze niż 100 procent trwało mniej czasu — wzrosła wydajności.  
  
 Wartości bezwzględne czas wdrożenia linii bazowej i względnego chronometrażu renderowanie wariantów są faktycznie średniej średnie wielu uruchomień — 5 domyślnie. Uśrednianie ta ułatwia danych o chronometrażu niezawodnych i spójnych. Można umieść wskaźnik na każdej komórki w tabeli, aby zbadać minimum, maksymalna, średnia i wartości środkowej chronometrażu, które zaobserwowano wyników w tym rysowania wywołania i renderowania wariant zostały wygenerowane. Wyświetlana jest również czas wdrożenia linii bazowej.  
  
#### <a name="hot-draw-calls"></a>"Gorących" wywołań rysowania  
 Aby zwrócić uwagę na rysowanie wywołania, które zużywać więcej całkowity czas renderowania lub który może być niezwykle powolne przyczyn, które można uniknąć, wiersza, który zawiera te wywołań rysowania "gorących" jest przyciemnione czerwony podczas terminy linii bazowej jest więcej niż jeden Odchylenie standardowe jest dłuższy niż czas linii bazowej średnią wszystkich wywołań rysowania w ramce.  
  
 ![To wywołanie DrawIndexed ma varients gorącego i zimnych. ] (media/pix_frame_analysis_hot_calls.png "pix_frame_analysis_hot_calls")  
  
#### <a name="statistical-significance"></a>Obserwowane  
 Aby zwrócić uwagę na renderowanie zmian, które mają największą zgodność, analiza ramek określa statystyczne znaczenie każdego wariantu renderowania i wyświetla mające duże jako pogrubione. Wyświetla te, które zwiększają wydajność na zielono i te, które zmniejszyć wydajność kolorem czerwonym. Wyświetla wyniki, które nie są statystycznie istotne jako normalne typu.  
  
 ![Statystyczne relevence Variant wywołanie rysowania](media/pix_frame_analysis_summary_stats.png "pix_frame_analysis_summary_stats")  
  
 Ustalenie statystyczne przydatności, analiza ramek używa [t Studenta](http://www.wikipedia.org/wiki/Student%27s_t-test).  
  
### <a name="details-table"></a>Tabela szczegółów  
 Poniżej podsumowania jest tabela Szczegóły, które jest domyślnie zwinięte. Zawartość tabeli Szczegóły zależy od platformy sprzętu maszyny odtwarzania. Informacje o platformach obsługiwanego sprzętu znajdują się w temacie [obsługi sprzętowej](#HardwareSupport).  
  
#### <a name="platforms-that-do-not-support-hardware-counters"></a>Platformy, które nie obsługują liczników sprzętowych  
 Większość platform nie obsługują w pełni liczników sprzętowych procesora GPU — dotyczy to wszystkich procesorów graficznych obecnie oferowane przez firmy Intel, AMD i nVidia. Gdy nie ma żadnych liczników sprzętu do zbierania, jest wyświetlana tylko w jednej tabeli Szczegóły i zawiera średnie bezwzględny czas wszystkich wariantów.  
  
 ![Tabela szczegółów i niektóre varients odtwarzania. ] (media/pix_frame_analysis_details.png "pix_frame_analysis_details")  
  
#### <a name="platforms-that-support-hardware-counters"></a>Platformy, które obsługują liczników sprzętowych  
 Dla platform, które obsługują liczników sprzętowych procesora GPU — na przykład nVidia T40 SOC i wszystkie SOCs Qualcomm — kilku tabel szczegóły są wyświetlane, po jednej dla każdego wariantu. Licznik każdego dostępnego sprzętu są zbierane dla każdego wariantu renderowania i wyświetlane w tabeli Szczegóły.  
  
 ![Liczniki sprzętu są wyświetlane, jeśli są obsługiwane. ] (media/pix_frame.png "pix_frame")  
  
 Informacje o liczniku sprzętu zapewnia bardzo szczegółowy widok zachowanie określonej platformy sprzętu dla każdego wywołania rysowania, co może pomóc w zidentyfikowaniu przyczyny wąskich gardeł wydajności bardzo dokładnie.  
  
> [!NOTE]
>  Sprzętowe platformy obsługują różne liczników; nie istnieje standard. Liczniki i ich znaczenie są określane wyłącznie przez każdego producenta procesora GPU.  
  
### <a name="marker-regions-and-events"></a>Regiony znacznika i zdarzenia  
 Analiza ramek obsługuje znaczniki zdarzeń zdefiniowanych przez użytkownika i liczba grup zdarzeń. Są one wyświetlane w tabeli podsumowania i tabele szczegółów.  
  
 Interfejsy API ID3DUserDefinedAnnotation lub starszego rodziny D3DPERF_ interfejsów API umożliwia tworzenie grup i znaczników. Korzystając z interfejsu API D3DPERF_ rodziny, można przypisać każdego znacznika i grupy kolor, który wyświetla analizy ramek jako kolorowe poza pasmem w wiersze zawierające znacznika zdarzenia lub znaczników rozpoczęcia/zakończenia grupy zdarzeń i ich zawartość. Ta funkcja może pomóc można szybko zidentyfikować ważne renderowania zdarzenia lub grup zdarzeń.  
  
### <a name="warnings-and-errors"></a>Ostrzeżenia i błędy  
 Analiza ramek czasami kończy wystąpiły ostrzeżenia i błędy, które są podsumowywane powyżej osi czasu i szczegółowe u dołu kartę analizy ramek.  
  
 Zwykle ostrzeżenia i błędy są tylko do celów informacyjnych i nie wymaga żadnej interwencji.  
  
 Ostrzeżenia zwykle oznaczają, że braku obsługi sprzętowej, ale można pracować wokół, nie można zebrać liczników sprzętowych lub niektóre dane dotyczące wydajności może nie być prawidłowe — na przykład gdy obejście negatywny wpływ na jego.  
  
 Błędy zwykle wskazywać, że implementacja analizy ramek ma usterki, sterownik ma usterki, obsługi sprzętowej braku i nie może być działał wokół, lub aplikacja próbuje coś, co nie jest obsługiwana przez odtwarzanie.  
  
### <a name="retries"></a>Ponowne próby  
 Jeśli procesora GPU podlega przejściu stan zasilania podczas analizy ramek, przebiegu dotyczy analizy należy ponowić próbę ponieważ szybkość zegara procesora GPU zmienione, a tym samym unieważnienie wyniki względnego chronometrażu.  
  
 Analiza ramek ogranicza liczbę ponownych prób do 10. Jeśli platformy zarządzania energii lub bramkowanie zegara, może spowodować analizy ramek zakończyć się niepowodzeniem i zgłoś błąd, ponieważ został przekroczony limit ponownych prób. Można ograniczyć ten problem, resetując danej platformy zarządzania energią i zegara szybkości ograniczania się mniej aktywnego, jeśli umożliwia platformie.  
  
##  <a name="HardwareSupport"></a> Obsługa sprzętu  
  
### <a name="timestamps-and-occlusion-queries"></a>Sygnatury czasowe i zamknięcia.  
 Sygnatury czasowe są obsługiwane na wszystkich platformach, które obsługują analizy ramek. Głębokość okluzji zapytania — wymagane dla pikseli zamknięte liczników — są obsługiwane na platformach, które obsługuje funkcji na poziomie 9.2 lub nowszej.  
  
> [!NOTE]
>  Sygnatury czasowe są obsługiwane na wszystkich platformach, które obsługują analizy ramek, dokładność i spójność sygnatury czasowe różni się w zależności od platformy.  
  
### <a name="gpu-counters"></a>Liczniki procesora GPU  
 Obsługa liczników sprzętowych procesora GPU jest zależne od sprzętu.  
  
 Ponieważ żaden komputer aktualnie oferowane przez firmy Intel, AMD lub nVidia GPU niezawodnie obsługuje liczników sprzętowych procesora GPU, analiza ramek nie zebrać liczników z nich. Jednak analizy ramek zbierania liczników sprzętowych z następujących procesora GPU, który niezawodny sposób je obsługuje:  
  
-   nVidia T40 (Tegra4)
  
 Nie inne platformy, która obsługuje analizy ramek zbiera dane liczników sprzętowych procesora GPU.  
  
> [!NOTE]
>  Ponieważ liczników sprzętowych procesora GPU zasobów sprzętowych, może zająć wiele przebiegów, aby zebrać pełny zestaw liczników sprzętowych dla poszczególnych wariantu renderowania. W związku z tym kolejności, w którym procesor GPU liczniki są zbierane jest nieokreślony.  
  
## <a name="unsupported-scenarios"></a>Nieobsługiwane scenariusze  
 Niektóre sposoby używania analiza ramek nie są obsługiwane lub są dobrym pomysłem.  
  
### <a name="playback-of-high-feature-level-captures-on-down-level-devices"></a>Przechwytuje odtwarzania poziomie o wysokim funkcji na urządzeniach niskiego poziomu  
 W analizatorze grafiki podczas odtwarzania pliku dziennika grafiki, która używa wyższego poziomu funkcji nie obsługuje maszyny odtwarzania, on automatycznie powraca do WARP. Analizę ramek go jawnie nie wracały do WARP oraz generuje błąd — WARP przydaje się sprawdzenie poprawności aplikacji Direct3D, ale nie sprawdzenie jego wydajności.  
  
> [!NOTE]
>  Chociaż należy koniecznie pamiętać problemy z poziomu funkcji, można przechwytywać i odtwarzanie się, że pliki na różne konfiguracje sprzętu i urządzeniach dziennika grafiki. Dziennika grafiki można odtwarzać ponownie tak długo, jak w pliku dziennika nie zawiera interfejsy API, lub użyj poziomów funkcji, które nie są obsługiwane na maszynie odtwarzającej.  
  
### <a name="direct3d-10-and-lower"></a>Direct3D 10 lub niższy  
 Jeśli aplikacja wymaga interfejsu API programu Direct3D 10, analiza ramek nie rozpoznaje lub ich profilu, nawet jeśli są rozpoznawane i używane przez inne narzędzia Analizator grafiki.
  
> [!NOTE]
>  Dotyczy to tylko wywołania interfejsu API programu Direct3D, których używasz, nie poziomów funkcji.

### <a name="warp"></a>WARP  
 Analiza ramek jest przeznaczona do użycia profilu i poprawia wydajność renderowania na sprzęcie prawdziwe. Nie uniemożliwia uruchomiony analizy ramek na urządzenia WARP, ale nie jest zazwyczaj zastanowić wykonywania ponieważ WARP systemem wysokiej klasy procesora CPU jest mniejsza niż nawet obsługą najmniej GPU nowoczesnych i WARP wydajność może się znacznie różnić w zależności od określonego Procesora jest on uruchomiony.  
  
##  <a name="Variants"></a> Elementy Variant  
 Każdej zmiany, która sprawia, że analiza ramek na sposób renderowania ramki podczas odtwarzania nosi nazwę *variant*. Wariantów, które sprawdza, czy analiza ramek odpowiadają wspólnego, stosunkowo łatwa zmiany, które można zmienić w celu ulepszenia wydajności renderowania lub visual jakości aplikacji, na przykład, zmniejszenie jego rozmiar tekstury, za pomocą metody kompresji tekstury lub włączenie różne rodzaje wygładzanie. Wariantów zastąpić kontekstu zwykle renderowania i parametrów aplikacji. Poniżej przedstawiono podsumowanie:  
  
|Variant|Opis|  
|-------------|-----------------|  
|**Rozmiaru okienka ekranu 1 x 1**|Zmniejsza wymiary okienka ekranu na wszystkie elementy docelowe renderowania na 1 x 1 pikseli.<br /><br /> Aby uzyskać więcej informacji, zobacz [Variant rozmiaru okienka ekranu 1 x 1](1x1-viewport-size-variant.md)|  
|**0x MSAA**|Wyłącza wielu przykładowa Wygładzanie (MSAA) na wszystkich celów renderowania.<br /><br /> Aby uzyskać więcej informacji, zobacz [0 x / 2 x / 4 x MSAA wariantów](0x-2x-4x-msaa-variants.md)|  
|**2x MSAA**|Umożliwia 2 x wielu przykładowa Wygładzanie (MSAA) na wszystkich celów renderowania.<br /><br /> Aby uzyskać więcej informacji, zobacz [0 x / 2 x / 4 x MSAA wariantów](0x-2x-4x-msaa-variants.md)|  
|**4x MSAA**|Umożliwia 4 x wielu przykładowa Wygładzanie (MSAA) na wszystkich celów renderowania.<br /><br /> Aby uzyskać więcej informacji, zobacz [0 x / 2 x / 4 x MSAA wariantów](0x-2x-4x-msaa-variants.md)|  
|**Filtrowanie punktu tekstury**|Ustawia tryb filtrowania `DXD11_FILTER_MIN_MAG_MIP_POINT` (punkt filtrowania tekstury) dla wszystkich odpowiednich tekstury próbek.<br /><br /> Aby uzyskać więcej informacji, zobacz [punktu, dwuliniowa Trilinear i wariantów filtrowania tekstury anizotropowej](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrowanie dwuliniowa tekstury**|Ustawia tryb filtrowania `DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT` (filtrowanie dwuliniowa tekstury) dla wszystkich odpowiednich tekstury próbek.<br /><br /> Aby uzyskać więcej informacji, zobacz [punktu, dwuliniowa Trilinear i wariantów filtrowania tekstury anizotropowej](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrowanie trilinear tekstury**|Ustawia tryb filtrowania `DXD11_FILTER_MIN_MAG_MIP_LINEAR` (filtrowanie trilinear tekstury) dla wszystkich odpowiednich tekstury próbek.<br /><br /> Aby uzyskać więcej informacji, zobacz [punktu, dwuliniowa Trilinear i wariantów filtrowania tekstury anizotropowej](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtrowanie anizotropowych tekstury**|Ustawia tryb filtrowania `DXD11_FILTER_ANISOTROPIC` i `MaxAnisotropy` do `16` (16 x filtrowania anizotropowej tekstury) dla wszystkich odpowiednich tekstury próbek.<br /><br /> Aby uzyskać więcej informacji, zobacz [punktu, dwuliniowa Trilinear i wariantów filtrowania tekstury anizotropowej](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Format docelowy renderowania 16bpp**|Ustawia format piksela `DXGI_FORMAT_B5G6R5_UNORM` (16bpp, 565 format) dla wszystkich renderowania elementów docelowych i backbuffers.<br /><br /> Aby uzyskać więcej informacji, zobacz [16bpp renderowania docelowy Format typu Variant](16bpp-render-target-format-variant.md)|  
|**Generowanie MCI mapy**|Umożliwia MCI mapy na wszystkich tekstury, które nie są renderowane elementów docelowych.<br /><br /> Aby uzyskać więcej informacji, zobacz [Variant generowania mapy MCI](mip-map-generation-variant.md).|  
|**Wymiary połowa tekstury**|Zmniejsza liczbę wymiarów tekstury wszystkie tekstury, które nie są elementy docelowe renderowania do połowy ich oryginalny rozmiar każdego wymiaru. Na przykład 256 x 128 pikseli tekstury jest ograniczone do tekseli 128 x 64.<br /><br /> Aby uzyskać więcej informacji, zobacz [Variant wymiarów tekstury Half/Quarter](half-quarter-texture-dimensions-variant.md).|  
|**Wymiarów tekstury kwartału**|Zmniejsza liczbę wymiarów tekstury wszystkie tekstury, które nie są renderowane elementy docelowe w celu kwartału ich oryginalny rozmiar każdego wymiaru. Na przykład 256 x 128 pikseli tekstury jest ograniczone do 64 x 32 tekseli.<br /><br /> Aby uzyskać więcej informacji, zobacz [Variant wymiarów tekstury Half/Quarter](half-quarter-texture-dimensions-variant.md).|  
|**Kompresja tekstury BC**|Umożliwia blokowanie kompresji na wszystkie tekstury, których B8G8R8X8, B8G8R8A8 lub R8G8B8A8 wariant formatu piksela. B8G8R8X8 format wariantów są kompresowane przy użyciu BC1; B8G8R8A8 i R8G8B8A8 format wariantów są kompresowane przy użyciu BC3.<br /><br /> Aby uzyskać więcej informacji, zobacz [BC tekstury kompresji Variant](bc-texture-compression-variant.md).|  
  
 Wynik dla większości wariantów jest przetestowanego: "rozmiar tekstury redukujące o połowę jest szybsze 25 procent" lub "Włączenie 2 x MSAA tylko 2 procent wolniej". Inne wariantów może wymagać interpretacji więcej — na przykład jeśli variant, który zmienia rozmiary okienka ekranu do 1 x 1 przedstawiono bardziej wydajne duży, może to wskazywać, czy renderowanie jest wydajność ruchu przez współczynnik wypełnienia niski; Alternatywnie Jeśli nie ma znaczące zmiany w wydajności, może to wskazywać, czy renderowanie jest wydajność ruchu przez przetwarzanie wierzchołka.