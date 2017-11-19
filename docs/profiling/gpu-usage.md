---
title: "Użycie procesora GPU | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 957fed3c-4ded-4e05-87c6-ccc33de65349
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2c265fde65ae20012e2846d99b86c71254d5b44
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-usage"></a>Użycie procesora GPU
Użyj narzędzia użycie procesora GPU w Centrum diagnostyki i wydajności usługi Visual Studio, aby lepiej zrozumieć wykorzystanie sprzętu wysokiego poziomu aplikacji Direct3D. Służy on do ustalenia, czy wydajność aplikacji jest powiązane z procesora CPU lub powiązane z procesora GPU i uzyskanie szczegółowe informacje na temat używania platformy sprzętu bardziej efektywnie. Użycie procesora GPU obsługuje aplikacje, które używają Direct3D 12, Direct3D 11 i Direct3D 10; nie obsługuje innych interfejsów API, takich jak Direct2D lub OpenGL grafiki.  
  
 Jest to **raport użycia procesora GPU** okno:  
  
 ![Raport użycia procesora GPU, o osiach czasu procesora CPU i procesora GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")  
  
## <a name="requirements"></a>Wymagania  
 Poniżej przedstawiono wymagania dotyczące korzystania z narzędzia użycie procesora GPU, które są oprócz wymagań dotyczących diagnostyki grafiki.  
  
-   Procesora GPU i sterownik obsługujących Instrumentacji niezbędne chronometrażu.  
  
    > [!NOTE]
    >  Aby uzyskać więcej informacji o obsługiwanych sprzęt i sterowniki, zobacz [sprzętu i obsługi sterowników](#hwsupport) na końcu tego dokumentu.  
  
 Aby uzyskać więcej informacji na temat wymagań dotyczących diagnostyki grafiki, zobacz [wprowadzenie](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).  
  
## <a name="using-the-gpu-usage-tool"></a>Za pomocą narzędzia użycie procesora GPU  
 Po uruchomieniu aplikacji w obszarze narzędzia użycie procesora GPU programu Visual Studio tworzy sesję diagnostyki wykresach ogólne informacje dotyczące renderowania wydajności aplikacji oraz użycie procesora GPU w czasie rzeczywistym.  
  
#### <a name="to-start-the-gpu-usage-tool"></a>Aby uruchomić narzędzie użycie procesora GPU:  
  
1.  W menu głównym wybierz **debugowania**, następnie **wydajności i diagnostyki** (klawiatury: naciśnij klawisze Alt + F2).  
  
2.  W Centrum wydajności i diagnostyki, zaznacz pole wyboru obok pozycji **użycia procesora GPU**. Opcjonalnie zaznacz pola wyboru obok innych narzędzi, które Cię interesują. Można uruchomić kilka wydajności i narzędzi diagnostycznych do jednocześnie uzyskać pełniejsze obraz wydajności aplikacji.  
  
     ![Wybierz narzędzia diagnostyczne, którego chcesz użyć. ] (media/gfx_diag_diagsession_tools.png "gfx_diag_diagsession_tools")  
  
    > [!NOTE]
    >  Nie wszystkie wydajności i narzędzi diagnostycznych można w tym samym czasie.  
  
3.  Wybierz niebieski **Start** znajdujący się u dołu Centrum wydajności i informacji diagnostycznych do uruchamiania aplikacji w obszarze narzędzia wybrane.  
  
 Informacje wysokiego poziomu, która jest wyświetlana w czasie rzeczywistym obejmuje czas ramki, szybkość klatek i użycie procesora GPU. Każdy z tych fragmentów informacji są wyświetlone na wykresie niezależnie, ale użyj przedział czasu typowe, dzięki czemu można łatwo odnoszą się między nimi.  
  
 **Ramki (ms) czas** i **klatek na sekundę Zagregowanych** wykresy zawiera dwa czerwony, poziomych linii, którego celem wydajności reprezentują 60 i 30 klatek na sekundę. W **ramki czasu** wykresu, aplikacji przekracza docelowy wydajności podczas wykres jest poniżej wiersza i brak go po powyżej linii wykresu. Dla ramek na drugi wykresu jest przeciwieństwem — aplikacji jest powyżej docelowego wydajności, gdy wykres jest powyżej linii i brak go, gdy wykres jest poniżej wiersza. Przede wszystkim wykresy te są używane, można pobrać pomysłem wysokiego poziomu wydajności aplikacji oraz do identyfikowania slow-downs, które można zbadać — na przykład, nagłe spadek szybkość klatek lub kolekcji poziom użycia procesora GPU.  
  
 Gdy aplikacja będzie działać w obszarze narzędzia użycie procesora GPU, sesji diagnostycznej zbiera również szczegółowe informacje na temat zdarzeń grafiki, które zostały wykonane na procesorze GPU. Te informacje służy do generowania bardziej szczegółowego raportu dotyczącego jak aplikacja korzysta z sprzętu. Ponieważ ten raport wymaga pewnego czasu wygenerowania na podstawie zebranych informacji, jego jest dostępna tylko po wykonaniu czynności zbieranie informacji o sesji diagnostycznej.  
  
 Jeśli aby przyjrzeć się wydajności lub użycie wystawiania ściślej, zatrzymać zbieranie informacji o wydajności, dzięki czemu można wygenerować raportu.  
  
#### <a name="to-generate-and-view-the-gpu-usage-report"></a>Do generowania i przeglądania raportów użycia procesora GPU:  
  
1.  W dolnej części okna sesji diagnostyki wybierz **zatrzymania zbierania** łączenie lub naciśnij klawisz **zatrzymać** w lewym górnym rogu.  
  
     ![Zbieranie informacji procesora GPU i procesora CPU. ] (media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")  
  
2.  W górnej części raportu wybierz sekcji z jednego z wykresy, które przedstawiono ten problem, które chcesz zbadać. Wybór może być maksymalnie 3 sekundy długie. dłużej sekcje są obcinane na początku.  
  
     ![Po &#45; kolekcji, wybierz zakres, aby wyświetlić szczegóły](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")  
  
3.  W dolnej części raportu, wybierz **wyświetlić szczegóły** łącze w **.. Kliknij przycisk poniżej, aby wyświetlić szczegóły użycia procesora graficznego dla tego zakresu** komunikat, aby wyświetlić szczegółowe osi czasu zaznaczenia.  
  
     ![Po &#45; kolekcji z wybrany zakres](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")  
  
 Zostanie otwarty nowy dokument z kartami zawiera raport. Raport użycia procesora GPU pomaga uruchomienia zdarzeń grafiki na Procesorze, po osiągnięciu procesora GPU i jak długo trwa ją wykonać na procesor GPU. Te informacje mogą pomóc w określeniu wąskich gardeł i możliwości zwiększona równoległości w kodzie.  

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Eksportowanie do GPUView lub Analizator wydajności systemu Windows
Począwszy od programu Visual Studio 2017 tych danych można otworzyć za pomocą [GPUView](/windows-hardware/drivers/display/using-gpuview) i [Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer) klikając **Otwórz w GpuView** lub **Otwórz w WPA** łącza znajdujący się w prawej dolnej części sesji diagnostycznej.

![Otwórz w...](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="using-the-gpu-usage-report"></a>Za pomocą raportów użycia procesora GPU  
 Górna część raportów użycia procesora GPU Wyświetla osiach czasu procesora i przetwarzanie działania, działanie renderowania procesora GPU i działanie kopiowania procesora GPU. Te osiach czasu są podzielone według światła w kolorze szarym, pionowe paski reprezentujących synchronizacji w pionie wyświetlania; częstotliwość pasków odpowiada jednej z wartości częstotliwość odświeżania (wybrane za pomocą **wyświetlania** listy rozwijanej) zostały zebrane danych dotyczących użycia procesora GPU. Ponieważ wyświetlanie może być odświeżania wyższym niż elementu docelowego Twojej aplikacji wydajności może nie być relację 1-do-1 między synchronizacji w pionie i ma swoją aplikację w celu osiągnięcia szybkość klatek. Do swojego docelowego wydajności aplikacji musi ukończyć przetwarzania, wykonywanie renderowania i wywoływania Present() w docelowej szybkość klatek, ale renderowanych ramek nie będą wyświetlane do momentu następnej synchronizacji w pionie po Present().  
  
 W dolnej części wyświetlana lista zdarzeń grafiki, które wystąpiły w czasie raportu.  
  
 Oto **raport użycia procesora GPU** okno:  
  
 ![Raport użycia procesora GPU, o osiach czasu procesora CPU i procesora GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")  
  
 Wybranie jednego ze zdarzeń w dolnej części raportu umieszcza znacznik na pokrewnych zdarzeń w odpowiednich osi czasu, zazwyczaj jedno zdarzenie w wątku procesora CPU, który reprezentuje wywołanie interfejsu API i inne zdarzenie na jednej osi czasu procesora GPU, które reprezentuje kiedy procesora GPU zakończone zadanie. Podobnie wybierając jedną z zdarzenia na osi czasu prezentuje odpowiednie zdarzenie w dolnej części raportu. Po powiększeniu poza osi czasu, w górnej części raportu, najbardziej czasochłonne zdarzenia są widoczne. Aby wyświetlić zdarzenia, które mają krótszy czas trwania, za pomocą urządzenia wskazującego lub skalowania formantu w lewym dolnym rogu górny panel Ctrl + kółka powiększenie fragmentu osi czasu. Możesz także przeciągnąć panelu Oś czasu zawartości można przenieść za pomocą zarejestrowane zdarzenia.  
  
 Ułatwia znajdowanie, czego szukasz, możesz filtrować raport użycia procesora GPU na podstawie nazwy procesu, wątku identyfikatorów i nazwa zdarzenia; Ponadto można wybrać wiersze vysnc określa częstotliwość odświeżania które wyświetlania i sortować zdarzenia hierarchicznie Jeśli aplikacja korzysta z interfejsu ID3DUserDefinedAnnotation do grupy poleceń renderowania.  
  
 Poniżej przedstawiono więcej informacji:  
  
|Formant filtru|Opis|  
|--------------------|-----------------|  
|**Proces**|Nazwa procesu, który chcesz. Wszystkie procesy, które procesora GPU podczas sesji diagnostycznej znajdują się w tej listy rozwijanej. Kolor skojarzonych z procesem w tej listy rozwijanej jest aktywności wątku na osiach czasu poniżej.|  
|**Wątek**|Identyfikator wątku, który chcesz. W aplikacji wielowątkowych może to pomóc izolować określonego wątków, które należą do procesu interesuje Cię. Zdarzenia związane z wybranego wątku wyróżniono każdy osi czasu.|  
|**Wyświetl**|Liczba wyświetlania, w których częstotliwość odświeżania jest wyświetlany **Uwaga:** niektórych sterowników można skonfigurować, aby prezentować wiele fizycznych wyświetla jako pojedynczy, duży ekran wirtualnego. Tylko jeden wyświetlania na liście, może pojawić się nawet wtedy, gdy komputer ma wiele Wyświetla dołączony.|  
|**Filtr**|Słowa kluczowe, które planuje się. Zdarzenia w dolnej części raport obejmuje tylko pasujących — słowo kluczowe w całości lub częściowo. Można określić wiele słów kluczowych, oddzielając je średnikami (;).|  
|**Sortowanie hierarchii**|Pole wyboru, która wskazuje, czy zdarzenie hierarchie — zdefiniowane przez użytkownika znaczniki — są zachowywane lub ignorowane.|  
  
 Na liście zdarzeń znajdujących się w dolnej części raportu użycia procesora GPU zostaną wyświetlone szczegóły każdego zdarzenia.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa zdarzenia**|Nazwa zdarzenia grafiki. Zdarzenie zazwyczaj odpowiada jedno zdarzenie w wątku osi czasu procesora CPU i jedno zdarzenie na osi czasu procesora GPU.<br /><br /> Nazwy zdarzenia może być "unattributed", jeśli użycie procesora GPU nie może określić nazwę zdarzenia. Aby uzyskać więcej informacji zobacz uwagi pod tą tabelą.|  
|**Start procesora CPU (ns)**|Czas, jaki zdarzenia zainicjowano procesora, wywołując interfejs API programu Direct3D. Czas jest mierzony w nanosekundach względem podczas uruchamiania aplikacji.|  
|**Start procesora GPU (ns)**|Czas, jaki zdarzenie zostało zainicjowane na procesorze GPU. Czas jest mierzony w nanosekundach względem podczas uruchamiania aplikacji.|  
|**Czas procesora GPU (ns)**|Czas, jaki zdarzenia miały ukończenie procesora GPU w nanosekundach.|  
|**Nazwa procesu**|Nazwa aplikacji, z której pochodzi zdarzenia.|  
|**Identyfikator wątku**|Identyfikator wątku, z której pochodzi zdarzenia.|  
  
> [!IMPORTANT]
>  Windows 8.1 jest wymagany dla zdarzeń autorstwa. Ponadto jeśli sterownik lub procesora GPU nie obsługuje Instrumentacji niezbędne funkcje, wszystkie zdarzenia będą wyświetlane jako "unattributed". Upewnij się zaktualizować sterownik procesora GPU i spróbuj ponownie, jeśli wystąpi ten problem. Aby uzyskać więcej informacji, zobacz [sprzętu i obsługi sterowników](#hwsupport) poniżej.  
  
## <a name="gpu-usage-settings"></a>Ustawienia użycia procesora GPU  
 Istnieje możliwość skonfigurowania narzędzia użycie procesora GPU odroczenie zbiór informacje dotyczące profilowania, zamiast uruchamiania zbierać informacje, jak najszybciej po uruchomieniu aplikacji. Ponieważ rozmiar danych profilowania mogą być istotne, jest to przydatne, gdy wiesz, że spowolnienie wydajności aplikacji nie będzie dłużej wyświetlane dopiero po pewnym czasie.  
  
#### <a name="to-postpone-profiling-from-the-start-of-the-app"></a>Aby odłożyć profilowania od początku aplikacji:  
  
1.  W menu głównym wybierz **debugowania**, następnie **wydajności i diagnostyki** (klawiatury: naciśnij klawisze Alt + F2).  
  
2.  W Centrum wydajności i diagnostyki, wykonaj **ustawienia** znajdujący się obok podsekcji **użycia procesora GPU**.  
  
3.  W obszarze **konfiguracji profilowania procesora GPU**na **ogólne** strony właściwości, wyczyść **rozpocząć profilowania podczas uruchamiania aplikacji** pole wyboru, aby odłożyć profilowania.  
  
     ![Konfigurowanie podczas uruchamiania zbierania użycia procesora GPU](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")  
  
> [!IMPORTANT]
>  Opóźnienia profilowania nie jest obecnie obsługiwane w przypadku aplikacji Direct3D 12.  
  
 Za pomocą tego ustawienia można odłożyć danych profilowania, dodatkowe łącze staje się dostępna w dolnej części okna narzędzia użycie procesora GPU podczas uruchamiania aplikacji w obszarze narzędzia użycie procesora GPU. Aby rozpocząć zbieranie informacji o profilowania, wybierz polecenie **Start** łącze w **Start zbieranie dodatkowych szczegółowych danych użycia procesora GPU** wiadomości.  
  
##  <a name="hwsupport"></a>Sprzęt i obsłudze sterowników  
 Obsługiwane są następujące GPU sprzęt i sterowniki:  
  
|Dostawcy|Opis elementu procesora GPU|Wymagana wersja sterownika|  
|------------|---------------------|-----------------------------|  
|Intel®|4. Generowanie Intel® rdzenie procesora (Haswell)<br /><br /> -Intel® HD grafiki (GT1)<br />-Intel® HD grafiki 4200 (GT2)<br />-Intel® HD grafiki 4400 (GT2)<br />-Intel® HD grafiki 4600 (GT2)<br />-Intel® HD grafiki P4600 (GT2)<br />-Intel® HD grafiki P4700 (GT2)<br />-Intel® HD grafiki 5000 (GT3)<br />-Grafika Intel® Iris™ 5100 (GT3)<br />-Intel® Iris™ Pro grafiki 5200 (GT3e)|--(użyj najnowszej wersji sterowników)|  
|AMD®|Większość od serii 7000 HD™ AMD Radeon (AMD Radeon™ HD 7350 7670 wyklucza)<br /><br /> AMD Radeon™ GPU, AMD FirePro™ GPU i AMD FirePro GPU akceleratorów, oferujący funkcje architektura grafiki dalej Core (GCN).<br /><br /> Serii E AMD® i AMD A-series przyspieszony przetwarzania jednostki (APU) z architektury grafiki dalej Core (GCN) ("Kaveri", "Kabini", "Temash", "Beema", "Mullins")|14.7 RC3 lub nowszej|  
|NVIDIA®|Najbardziej od 400 serii NVIDIA GeForce®.<br /><br /> NVIDIA® GeForce® GPU, NVIDIA Quadro® GPU i NVIDIA® teslach™ GPU akceleratorów, oferujący funkcje Fermi™, Kepler™ ani Maxwell™ architektury.|343.37 lub nowszej|  
  
 Konfiguracje Multi-GPU, takie jak NVIDIA® SLI™ i AMD Crossfire™ nie są obsługiwane w tej chwili. Ustawienia grafiki hybrydowych, takich jak NVIDIA® Optimus™ i AMD Enduro™ są obsługiwane.  
  
## <a name="see-also"></a>Zobacz także  
  
-   [Rozwiązania trudnych problemów grafiki z gier za pomocą programu DirectX narzędziami (klip wideo)](http://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)  
-   [Narzędzie użycia procesora GPU w programie Visual Studio (klip wideo)](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)  
-   [Narzędzia użycie procesora GPU w Visual Studio 2013 Update 4 CTP1 (blog)](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx)  
-   [Użycie procesora GPU programu DirectX w programie Visual Studio (blog)](http://blogs.msdn.com/b/ianhu/archive/2014/12/16/gpu-usage-for-directx-in-visual-studio.aspx)
- [GPUView](/windows-hardware/drivers/display/using-gpuview) 
- [Analizator wydajności systemu Windows](/windows-hardware/test/wpt/windows-performance-analyzer)