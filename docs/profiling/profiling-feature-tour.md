---
title: Profilowanie funkcji samouczek | Dokumentacja firmy Microsoft
ms.custom: H1HackMay2017
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12c10e06d1dcd789212b04b591f0165e118139b1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="profiling-feature-tour"></a>Przegląd funkcji profilowania

Program Visual Studio udostępnia szereg profilowania narzędzia ułatwiające diagnozowanie różne rodzaje problemów z wydajnością w zależności od typu aplikacji.

W oknie narzędzi diagnostycznych dostępnych narzędzi do profilowania, które są dostępne podczas sesji debugowania. Okno narzędzia diagnostyczne pojawiają się automatycznie, jeśli wyłączono go. Aby wyświetlić okno, kliknij przycisk **Debug / Windows / Pokaż narzędzia diagnostyczne**. Po otwarciu okna można wybrać narzędzia, dla których chcesz zbierać dane.

![Okno narzędzia diagnostyczne](../profiling/media/prof-tour-diagnostic-tools.png "narzędzia diagnostyczne")

Podczas debugowania, można użyć **narzędzia diagnostyczne** okna do analizowania procesora CPU i użycie pamięci i można wyświetlić zdarzenia, które zawierają informacje związane z wydajnością.

![Wyświetl podsumowanie narzędzia diagnostyczne](../profiling/media/prof-tour-cpu-and-memory-graph.gif "podsumowanie narzędzia diagnostyczne")

**Narzędzia diagnostyczne** okno często jest preferowany sposób do profilu aplikacji, ale dla wersji kompilacji można również wykonać analizę których post aplikacji zamiast tego. Aby uzyskać więcej informacji na temat różnych metod, zobacz [uruchomione profilowanie narzędzia z lub bez debugera](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Aby wyświetlić profilowania Obsługa narzędzi dla różnych typów aplikacji, zobacz [narzędzie, które należy używać?](#tool_support_info).

## <a name="analyze-cpu-usage"></a>Analiza użycia procesora CPU

Narzędzia użycie procesora CPU jest dobrym miejscem do uruchomienia analizowanie wydajności aplikacji. Wskazane w drugim więcej informacji na temat zasobów Procesora, które jest korzystanie z aplikacji. Aby uzyskać bardziej szczegółowe wskazówki narzędzia użycie procesora CPU, zobacz [profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md).

Z **Podsumowanie** wybierz pozycję Wyświetl narzędzi diagnostycznych **Włącz profilowanie procesora CPU** (musi być w sesji debugowania).

![Włącz użycie procesora CPU w narzędziach diagnostycznych](../profiling/media/prof-tour-enable-cpu-profiling.png "użycie procesora CPU Włącz narzędzia diagnostyczne")

Aby użyć narzędzia najbardziej efektywne, należy ustawić dwa punkty przerwania w kodzie, jeden na początku, a drugi na końcu funkcji lub regionu, kodu, który chcesz przeanalizować. Dane profilowania należy zbadać, gdy jest wstrzymana na drugi punkt przerwania.

**Użycie procesora CPU** widok zawiera listę funkcji uporządkowanych według najdłuższym uruchomiona, za pomocą funkcji najdłużej działających na górze. Może to ułatwić, prowadzące do funkcji gdzie wąskich gardeł wydajności są wykonywane.

![Widok użycie procesora CPU narzędzia diagnostyczne](../profiling/media/prof-tour-cpu-usage.png "użycie procesora CPU narzędzia diagnostyczne")

Funkcja planuje się, czy zostanie wyświetlony bardziej szczegółowy widok okienka trzech "butterfly", za pomocą funkcji wybranych środku okna funkcji wywołującej po lewej stronie i wywołuje się po prawej stronie funkcje kliknij dwukrotnie. **Treści funkcji** sekcji przedstawia łączną ilość czasu (i wartość procentowa czasu) w treści funkcji bez czasu poświęcony na wywołanie i wywołać funkcji. Te dane ułatwiają ocenę, czy ta funkcja jest wąskie gardło.

![Narzędzia diagnostyczne wywołującego wywoływany "butterfly" Widok](../profiling/media/prof-tour-cpu-usage-caller-callee.png "narzędzia diagnostyczne wywołującego wywoływany widok")

## <a name="analyze-memory-usage"></a>Analizowanie użycia pamięci

Okno narzędzia diagnostyczne umożliwia również ocena użycia pamięci w aplikacji. Na przykład można przyjrzeć się liczby i rozmiaru obiektów na stercie. Aby uzyskać szczegółowe instrukcje, aby przeanalizować pamięci, zobacz [Analizowanie użycia pamięci](../profiling/memory-usage.md).

Do analizy użycia pamięci, należy wykonać co najmniej jedną migawkę pamięci podczas debugowania. Często dlatego najlepszym sposobem na analizowanie pamięci jest migawek dwóch; pierwszy prawie przed problem podejrzanych pamięci oraz drugi migawki po wystąpieniu problemu podejrzanych pamięci. Następnie można wyświetlić diff dwóch migawek i dokładnie co zmieniony.

![Utwórz migawkę w narzędziach diagnostycznych](../profiling/media/prof-tour-take-snapshots.gif "migawki zająć narzędzia diagnostyczne")

Wybierając strzałkę łącza są podane różnicowej widok sterty (czerwona strzałka w górę ![zwiększenie użycia pamięci](../profiling/media/prof-tour-mem-usage-up-arrow.png "zwiększenie użycia pamięci") pokazuje zwiększanie liczby obiektów (lewych) lub zwiększenie Rozmiar stosu (po prawej)). Kliknij łącze prawym, otrzymasz widok sterty różnicowej uporządkowanych według obiektów, które zwiększyć maksymalne w rozmiar stosu. Może to pomóc w określeniu problemy z pamięcią. Na przykład na poniższej ilustracji bajtów używane przez `ClassHandlersStore` obiektów wzrosła o 3,492 bajtów w drugim migawki.

![Narzędzia diagnostyczne stercie widoku różnic](../profiling/media/prof-tour-mem-usage-diff-heap.png "diagnostycznych różnicowego sterty narzędzi widoku")

Jeśli zamiast tego kliknij link po lewej stronie w **użycie pamięci** widoku, widok sterty jest zorganizowana według liczby obiektów; obiekty określonego typu przez zwiększone najbardziej w numerze są wyświetlane u góry (posortowane według **różnica liczby** kolumny).

## <a name="examine-performance-events"></a>Zbadanie zdarzeń wydajności

**Zdarzenia** widoku w narzędziach diagnostycznych pokazuje różnych zdarzeń występujących podczas debugowania, takie jak ustawienie punkt przerwania lub operację wykonywania krokowego kod. Możesz sprawdzić informacje, takie jak czas trwania zdarzenia (mierzonego podczas ostatniego debuger został wstrzymany lub podczas uruchamiania aplikacji). Na przykład, jeśli można wykonywać krokowo kodu (F10, F11) **zdarzenia** widok przedstawia czas wykonywania aplikacji z poprzedniej operacji krok do bieżącego etapu.

![Wyświetl zdarzenia narzędzi diagnostycznych](../profiling/media/prof-tour-events.png "zdarzenia narzędzi diagnostycznych w widoku")

 > [!NOTE]
 > Jeśli masz program Visual Studio Enterprise jest również widoczna [zdarzeń funkcji IntelliTrace](../debugger/intellitrace.md) na tej karcie.

Tego samego zdarzenia również wyświetlane w edytorze kodu można wyświetlić jako wskazówek.

![Profilowanie wskazówek samouczek](../profiling/media/prof-tour-perf-tips.png "profilowania wskazówek samouczka")

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Sprawdź, czy interfejsu użytkownika wydajności i dostępności zdarzenia (UWP)

W aplikacjach platformy uniwersalnej systemu Windows, można włączyć **interfejsu użytkownika analizy** w oknie narzędzia diagnostyczne. Narzędzie wyszukuje typowych problemów z wydajnością lub dostępności i wyświetla je w **zdarzenia** wyświetlanie podczas debugowania. Opisy zdarzeń zawierają informacje, które mogą ułatwić rozwiązywanie problemów.

![Wyświetlać zdarzenia interfejsu użytkownika analizy w narzędziach diagnostycznych](../profiling/media/prof-tour-ui-analysis.png "zdarzenia narzędzi diagnostycznych wyświetlanie interfejsu użytkownika analizy")

## <a name="profile-release-builds-without-the-debugger"></a>Kompilacje wydania profilu bez debugera

Profilowanie narzędzi, takich jak użycie procesora CPU i użycie pamięci może być używany z debugera (zobacz wcześniejszej sekcji), lub uruchomić narzędzia przy użyciu profilera wydajności, które mają na celu dostarczenie analizy w celu profilowania **wersji** kompilacji. W profilera wydajności można zbierać informacje diagnostyczne, podczas gdy aplikacja jest uruchomiona i sprawdź zebranych informacji po wyłączeniu aplikacji. Aby uzyskać więcej informacji o tych różne podejścia, zobacz [uruchomione profilowanie narzędzia z lub bez debugera](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

![Profiler wydajności](../profiling/media/prof-tour-performance-profiler.png "wydajności programu profilującego")

Otwórz profilera wydajności, wybierając **Debug / wydajności programu profilującego**.

Okno umożliwi wybranie wielu narzędzi profilowania w niektórych scenariuszach. Narzędzia, takie jak użycie Procesora może zapewnić dodatkowe dane, które służy do pomocy w analizy.

## <a name="analyze-resource-consumption-xaml"></a>Analizowanie zużycia zasobów (XAML)

W aplikacjach XAML, np. aplikacje WPF pulpitu systemu Windows i aplikacji platformy uniwersalnej systemu Windows można przeanalizować zużycia zasobów przy użyciu narzędzia oś czasu aplikacji. Na przykład można analizować czasu poświęconego przez aplikację przygotowywanie ramki interfejsu użytkownika (układu i renderowania), sieci i dysku żądania obsługi i w scenariuszach, takich jak uruchamiania aplikacji, strony obciążenia i zmiany rozmiaru okna. Aby korzystać z narzędzia, wybierz polecenie **oś czasu aplikacji** w profilera wydajności, a następnie wybierz **Start**. W aplikacji, przejdź do scenariusza z podejrzanych problem, a następnie wybierz **zatrzymać zbieranie** do wygenerowania raportu.

Mało framerates w **przepływność wizualną** wykresu może odpowiadać visual problemów, które są wyświetlane podczas uruchamiania aplikacji. Podobnie, dużej liczby w **użycie wątków interfejsu użytkownika** wykresu mogą również odpowiadać problemów czasu odpowiedzi interfejsu użytkownika. W raporcie można wybrać okres z problemu z wydajnością podejrzanych i obejrzyj szczegółowe działania wątku interfejsu użytkownika w widoku szczegółów osi czasu (w dolnym okienku).

![Narzędzia profilowania oś czasu aplikacji](../profiling/media/prof-tour-application-timeline.gif "profilowania samouczek oś czasu aplikacji")

W widoku szczegółów osi czasu można znaleźć informacje, takie jak typ organ (lub zaangażowanych elementu interfejsu użytkownika) oraz czas trwania działania. Na przykład na ilustracji **układu** zdarzenia dla formantu siatki przyjmuje 57.53 ms.

Aby uzyskać więcej informacji, zobacz [oś czasu aplikacji](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analizowanie użycia procesora GPU (Direct3D)

W aplikacjach Direct3D (składniki muszą być w języku C++ Direct3D) można zbadać aktywności procesora GPU i analizować problemy z wydajnością. Aby uzyskać więcej informacji, zobacz [użycia procesora GPU](../debugger/gpu-usage.md). Aby korzystać z narzędzia, wybierz polecenie **użycia procesora GPU** w profilera wydajności, a następnie wybierz **Start**. W aplikacji, przejdź za pośrednictwem tego scenariusza, który chcesz profilowania, a następnie wybierz **zatrzymać zbieranie** do wygenerowania raportu.

Po wybraniu w czasie na wykresach i **wyświetlić szczegóły**, widok szczegółowy pojawia się w dolnym okienku. W widoku szczegółowym można sprawdzić, ile działania wykonywane na każdym procesora CPU i procesora GPU. Wybierz zdarzenia w okienku najniższy uzyskanie wyskakujące okienka na osi czasu. Na przykład wybierz **obecny** zdarzeń, aby wyświetlić **obecny** wywołać wyskakujące okienka. (Światła szarego pionowych linii synchronizacji w pionie może służyć jako odwołanie do zrozumienia czy niektóre **obecny** wywołania pominąć synchronizacji w pionie. Musi istnieć jedna **obecny** wywołań między każdym dwa Vsyncs w kolejności aplikacji stopniowo trafienie 60 klatek na Sekundę.)

![Narzędzia profilowania użycia procesora GPU](../profiling/media/prof-tour-gpu-usage.png "Diag użycie procesora GPU")

Umożliwia także wykresy do sprawdzenia, czy istnieją powiązane Procesora GPU powiązany wąskich gardeł wydajności.

## <a name="analyze-performance-javascript"></a>Analizowanie wydajności (JavaScript)

W przypadku aplikacji platformy uniwersalnej systemu Windows można użyć narzędzi pamięć języka JavaScript i HTML czasu odpowiedzi interfejsu użytkownika.

Narzędzi pamięć języka JavaScript jest podobny do narzędzia do użycia pamięci dostępne dla innych typów aplikacji. Za pomocą tego narzędzia, aby określić sposób użycia pamięci i znaleźć przecieki pamięci w aplikacji. Aby uzyskać więcej informacji o tym narzędziu, zobacz [pamięci JavaScript](../profiling/javascript-memory.md).

![Narzędzia profilowania pamięci JavaScript](../profiling/media/diagjsmemory.png "DiagJSMemory")

Aby zdiagnozować czasu odpowiedzi interfejsu użytkownika, powolne ładowanie czasu i powolne aktualizacji visual w aplikacji platformy uniwersalnej systemu Windows, narzędzie czasu odpowiedzi interfejsu użytkownika HTML. Użycie jest podobny do narzędzia osi czasu aplikacji dla innych typów aplikacji. Aby uzyskać więcej informacji, zobacz [czasu odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md).

![Narzędzia profilowania czasu odpowiedzi interfejsu użytkownika HTML](../profiling/media/diaghtmlresp.png "DiagHTMLResp")

## <a name="analyze-network-usage-uwp"></a>Analizowanie użycia sieci (UWP)

W aplikacjach platformy uniwersalnej systemu Windows można analizować operacje sieciowe wykonywane przy użyciu `Windows.Web.Http` interfejsu API. To narzędzie może pomóc rozwiązać problemy, takie jak problemy dotyczące dostępu i uwierzytelniania, nieprawidłowe użycie pamięci podręcznej i wyświetlania jest niska i Pobierz wydajności. Aby korzystać z narzędzia, wybierz polecenie **sieci** w profilera wydajności, a następnie wybierz **Start**. W aplikacji, przejdź przez scenariusz, który używa `Windows.Web.Http`, a następnie wybierz pozycję **zatrzymać zbieranie** do wygenerowania raportu.

![Narzędzia profilowania użycie sieci](../profiling/media/prof-tour-network-usage.png "Diag użycia sieci")

Wybierz operację w Podsumowanie widoku, aby wyświetlić więcej szczegółów.

![Szczegółowe informacje o w narzędziu użycie sieci](../profiling/media/prof-tour-network-usage-details.png "szczegóły użycia sieci Diag")

Aby uzyskać więcej informacji, zobacz [użycie sieci](../profiling/network-usage.md).

## <a name="analyze-performance-legacy-tools"></a>Analizowanie wydajności (starsza wersja narzędzi)

Jeśli potrzebne funkcje, takie jak instrumentacji, które nie są aktualnie dostępne w menu Narzędzia użycie procesora CPU i użycie pamięci i korzystasz z pulpitu lub aplikacji ASP.NET, służy Eksplorator wydajności dla profilowania. (Nieobsługiwane w aplikacji platformy uniwersalnej systemu Windows). Aby uzyskać więcej informacji, zobacz [Eksplorator wydajności](../profiling/performance-explorer.md).

![Narzędzia Eksplorator wydajności](../profiling/media/prof-tour-performance-explorer.png "Eksplorator wydajności")

## <a name="tool_support_info"></a>Narzędzie, które powinny używać?  

Poniżej przedstawiono listę różnych narzędzi, których program Visual Studio oferuje i projekty różnych typów można używać ich z:
  
|Narzędzia wydajności|System Windows desktop|Platforma UWP|ASP.NET/ASP.NET Core| 
|----------------------|---------------------|-------------|-------------|  
|[Użycie pamięci](../profiling/memory-usage.md)|Tak|Tak|Tak| 
|[Użycie procesora CPU](../profiling/cpu-usage.md)|Tak (patrz uwaga)|Tak|Tak (patrz uwaga)|
|[Użycie procesora GPU](../debugger/gpu-usage.md)|Tak|Tak|Brak| 
|[Oś czasu aplikacji](../profiling/application-timeline.md)|Tak|Tak|Brak|
|[PerfTips](../profiling/perftips.md)|Tak|tak w języku XAML, nie dla HTML|Tak|
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Tak|Brak|Tak|
|[IntelliTrace](../debugger/intellitrace.md)|.NET z Visual Studio Enterprise|.NET z Visual Studio Enterprise|.NET z Visual Studio Enterprise|
|[Użycie sieci](../profiling/network-usage.md)|Brak|Tak|Brak|
|[Czas odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md)|Brak|tak, aby HTML, nie dla XAML|Brak| 
|[Pamięć języka JavaScript](../profiling/javascript-memory.md)|Brak|tak, aby HTML, nie dla XAML|Brak|

> [!NOTE]
> Dla platformy .NET Core i ASP.NET Core narzędzia użycie procesora CPU aktualnie nie zawiera prawidłowych wyników z PBDs przenośnej. Zamiast tego użyj pełne pliki PDB.

## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)