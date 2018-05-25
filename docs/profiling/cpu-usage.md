---
title: Analiza użycia procesora CPU w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b372d3d76153b5f5c885a6987d898cf55254b413
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="analyze-cpu-usage"></a>Analiza użycia procesora CPU
Gdy potrzebne do badania problemów z wydajnością w aplikacji, dobrym miejscem do rozpoczęcia jest zrozumienie, jak używa Procesora. **Użycie procesora CPU** narzędzie pokazuje, gdy Procesor spędza czasu wykonywania Visual C++, Visual C# / Visual Basic i kodu JavaScript. Począwszy od programu Visual Studio 2015 Update 1, jest widoczny na funkcja podział użycia procesora CPU bez opuszczania debugera. Włącz profilowanie procesora CPU i wyłączanie podczas debugowania i wyświetlić wyniki podczas wykonywania zostanie zatrzymana, na przykład w punkcie przerwania.  
  
Istnieje kilka możliwości do uruchamiania i zarządzania sesję diagnostyczną. Na przykład można uruchomić **użycie procesora CPU** narzędzia na komputerach lokalnych lub zdalnych, lub w symulatorze lub emulator. Można analizowanie wydajności Otwórz projekt w programie Visual Studio, podłączony do uruchomionej aplikacji, lub uruchomić aplikację, która jest zainstalowana z Microsoft Store. Aby uzyskać więcej informacji, zobacz [uruchomienia narzędzi profilowania z lub bez debuger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

W tym miejscu zostanie przedstawiony zostanie sposób zbieranie i analizowanie użycia procesora CPU z kompilacjami wydania. Do analizy użycia procesora CPU podczas debugowania, zobacz [profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md). 

> [!NOTE]
> Dla platformy .NET Core i ASP.NET Core narzędzia użycie procesora CPU aktualnie nie zawiera prawidłowych wyników z PBDs przenośnej. Zamiast tego użyj pełne pliki PDB.
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> Zbieranie danych o użyciu procesora CPU  
  
1.  W programie Visual Studio, ustaw dla konfiguracji rozwiązania **wersji** i wybierz cel wdrożenia.  
  
     ![Wybierz wersji i komputera lokalnego](../profiling/media/cpuuse_selectreleaselocalmachine.png "CPUUSE_SelectReleaseLocalMachine")  
  
    -   Uruchamianie aplikacji w **wersji** tryb daje lepszego widoku Rzeczywista wydajność aplikacji.  
  
    -   Uruchamianie aplikacji na komputerze lokalnym, najlepiej replikuje wykonywania zainstalowaną aplikację.  
  
    -   Jeśli dane są zbierane z urządzeniem zdalnym, uruchom aplikację bezpośrednio na urządzeniu, a nie za pomocą połączenia pulpitu zdalnego.  
  
    -   Dla aplikacji Windows Phone, zbieranie danych bezpośrednio z **urządzenia** zapewnia najdokładniejszych danych.  
  
2.  Na **debugowania** menu, wybierz **wydajności programu profilującego**.  
  
3.  Wybierz **użycie procesora CPU** , a następnie wybierz **Start**.  
  
     ![Wybierz opcję użycia procesora CPU](../profiling/media/cpuuse_lib_choosecpuusage.png "CPUUSE_LIB_ChooseCpuUsage")  
  
4.  Po uruchomieniu aplikacji, kliknij przycisk **uzyskać maksymalna liczba**. Oczekiwania dotyczące sekundy po danych wyjściowych jest wyświetlany, a następnie wybierz pozycję **uzyskać maksymalny numer Async**. Oczekiwanie między kliknięcia przycisków sprawia, że ułatwiają izolować przycisku kliknij procedury w raport diagnostyczny.  
  
5.  Gdy zostanie wyświetlony drugi wiersz danych wyjściowych, wybierz **zatrzymania zbierania** w Centrum wydajności i diagnostyki.  
  
 ![Zatrzymaj zbieranie danych CpuUsage](../profiling/media/cpu_use_wt_stopcollection.png "CPU_USE_WT_StopCollection")  
  
 Narzędzia użycie procesora CPU analizuje dane i wyświetla raport.  
  
 ![Raport CpuUsage](../profiling/media/cpu_use_wt_report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>Analizowanie raportów użycia procesora CPU  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Użycie procesora CPU drzewo wywołań  
 Aby rozpocząć, zrozumienie informacji o wywołaniu drzewa, wybierz ponownie `GetMaxNumberButton_Click` segmentu i przyjrzyj się szczegóły drzewa wywołań.  
  
####  <a name="BKMK_Call_tree_structure"></a> Struktura drzewa wywołań  
 ![GetMaxNumberButton&#95;kliknij wywołanie drzewa](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Węzeł najwyższego poziomu w drzewach wywołania użycia procesora CPU jest pseudo-węzłem|  
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|W przypadku większości aplikacji gdy **Pokaż kod zewnętrzny** opcja zostanie wyłączona, węzeł drugiego poziomu **[kod zewnętrzny]** węzła, który zawiera kod systemu i platformy, który uruchamiania i zatrzymywania aplikacji rysuje interfejsu użytkownika, Steruje planowania wątków i innymi usługami niskiego poziomu do aplikacji.|  
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Element podrzędny węzła drugiego poziomu są metody kodu użytkownika i procedur asynchroniczne, które wywołuje lub utworzony przez system drugiego poziomu i kod framework.|  
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Węzły podrzędne metody zawierają dane tylko w przypadku wywołania metody nadrzędnej. Gdy **Pokaż kod zewnętrzny** jest wyłączona, metody aplikacja może również zawierać **[kod zewnętrzny]** węzła.|  
  
####  <a name="BKMK_External_Code"></a> Kod zewnętrzny  
 Kod zewnętrzny są funkcje systemu i framework składników, które są wykonywane przez kod zostanie zapisany. Kod zewnętrzny obejmują funkcje, które start i Zatrzymaj aplikację, Rysuj interfejsu użytkownika, kontroli wątków i podaj inne niskiego poziomu usług do aplikacji. W większości przypadków będzie zainteresowana kod zewnętrzny i dlatego użycie procesora CPU Wywołaj gromadzi drzewa funkcji zewnętrznych metody użytkownika do jednego **[kod zewnętrzny]** węzła.  
  
 Umożliwia wyświetlanie ścieżek wywołania z kodu zewnętrznego, wybierz **Pokaż kod zewnętrzny** z **filtrowanie widoku** listy, a następnie wybierz pozycję **Zastosuj**.  
  
 ![Wybierz Widok filtrów, a następnie wyświetlić kod zewnętrzny](../profiling/media/cpu_use_wt_filterview.png "CPU_USE_WT_FilterView")  
  
 Należy pamiętać, że wiele łańcuchów wywołanie kodu zewnętrznego głęboko zagnieżdżone, tak, aby szerokość kolumny nazwy funkcji może być dłuższa niż szerokość wyświetlania wszystkich oprócz największy monitorów komputera. W takim przypadku funkcja nazwy są wyświetlane jako **[...]** :  
  
 ![Zagnieżdżone zewnętrznego kodu w drzewie wywołań](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Użyj pola wyszukiwania można znaleźć węzła, którego szukasz, a następnie przełącz do widoku danych za pomocą paska przewijania w poziomie:  
  
 ![Wyszukaj zagnieżdżonych kod zewnętrzny](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a> Kolumny danych drzewa wywołań  
  
|||  
|-|-|  
|**Całkowita liczba Procesora (%)**|![Łączna liczba % danych równości](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Procent aktywności Procesora aplikacji w wybranym zakresie czasu użytej przez wywołania funkcji i funkcji wywoływanych przez funkcję. Należy pamiętać, że jest inny niż **użycie procesora CPU** oś czasu wykresu, który porównuje łączną aktywność dotyczącą aplikacji w zakresie czasu, aby całkowita pojemność procesora CPU.|  
|**Samodzielnie Procesora (%)**|![Samodzielna % równości](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Procent aktywności Procesora aplikacji w wybranym zakresie czasu użytej przez wywołania funkcji, z wyłączeniem aktywności funkcji wywołanych przez funkcję.|  
|**Całkowita liczba procesora CPU (ms)**|Wyrażony w milisekundach czas spędzony w wywołaniach funkcji w wybranym zakresie czasu i funkcje, które zostały wywołane przez funkcję.|  
|**Samodzielnie procesora CPU (ms)**|Wyrażony w milisekundach czas spędzony w wywołaniach funkcji w wybranym zakresie czasu i funkcje, które zostały wywołane przez funkcję, z wyłączeniem aktywności funkcji wywołanych przez funkcję.|  
|**Module**|Nazwa modułu zawierającego funkcję lub liczba modułów zawierających funkcje w węźle [kod zewnętrzny].|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Funkcje asynchroniczne użycia procesora CPU w drzewie wywołań  
 Gdy kompilator napotka metodę asynchroniczną, tworzy ukryte klasę, aby kontrolować wykonywanie metody. Klasa jest koncepcyjnie, automatu stanów, który zawiera listę funkcji generowane przez kompilator, które asynchroniczne wywoływanie operacji oryginalnej metody i wywołania zwrotne, harmonogram i Iteratory wymagane do poprawnego wykonania. Oryginalny metoda jest wywoływana przez metodę nadrzędną, środowisko uruchomieniowe usuwa metodę z kontekstu wykonywania elementu nadrzędnego i działa metod klasy ukryte w kontekście systemu i framework kodu, który kontrolować wykonywanie aplikacji. Metody asynchroniczne są często, ale nie zawsze wykonywane na co najmniej jeden inny wątek. Ten kod jest wyświetlany w drzewie wywołań użycie procesora CPU jako elementy podrzędne **[kod zewnętrzny]** węzła bezpośrednio pod górny węzeł drzewa.  
  
 Aby wyświetlić to w naszym przykładzie, wybierz ponownie `GetMaxNumberAsyncButton_Click` segment osi czasu.  
  
 ![GetMaxNumberAsyncButton&#95;kliknij element raportu](../profiling/media/cpu_use_wt_getmaxnumberasync_selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Pierwsze dwa węzły pod **[kod zewnętrzny]** są generowane przez kompilator metod klasy maszyny stanu. Trzeci jest wywołanie metody oryginalnego. Rozszerzanie wygenerowane metody pokazuje, co się dzieje.  
  
 ![Rozszerzona GetMaxNumberAsyncButton&#95;kliknij wywołanie drzewa](../profiling/media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` jest bardzo mało; go zarządza listę wartości zadań oblicza maksymalną liczbę wyników i wyświetla dane wyjściowe.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` Pokazuje działania wymagane do planowania i uruchamiać 48 zadań, które otaczają wywołanie `GetNumberAsync`.  
  
-   `MainPage::<GetNumberAsync>b__b` Pokazuje aktywności zadań, które wywołują `GetNumber`.
