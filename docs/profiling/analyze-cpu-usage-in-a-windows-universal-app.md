---
title: "Analiza użycia procesora CPU w aplikacji uniwersalnej systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 59669f0430760bb98dd0cb63e05f433cb3a1fe54
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="analyze-cpu-usage-in-a-universal-windows-app-uwp"></a>Analiza użycia procesora CPU w aplikacji uniwersalnej systemu Windows (UWP)
![Ma zastosowanie do systemu Windows i Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 Gdy potrzebne do badania problemów z wydajnością w aplikacji, dobrym miejscem do rozpoczęcia jest zrozumienie, jak używa Procesora. **Użycie procesora CPU** narzędzie pokazuje, gdy Procesor spędza kodu w czasie wykonywania. Aby skoncentrować się na konkretnych scenariuszy, użycie Procesora może być uruchamiane przy [oś czasu aplikacji](../profiling/application-timeline.md) narzędzia [zużycie energii](../profiling/analyze-energy-use-in-store-apps.md) narzędzia lub obu narzędzi w jednej sesji diagnostycznej.  
  
> [!NOTE]
>  **Użycie procesora CPU** narzędzia nie można używać z aplikacji Windows Phone Silverlight 8.1.  
  
 W tym przewodniku prowadzi użytkownika przez zbieranie i analizowanie danych użycia procesora CPU dla prostej aplikacji Windows Universal XAML.  
  
##  <a name="BKMK_Create_the_CpuUseDemo_project"></a>Utwórz projekt CpuUseDemo  
 **CpuUseDemo** to aplikacja, która została utworzona w celu zademonstrowania zbieranie i analizowanie danych użycia procesora CPU. Przyciski wygenerować liczbę, przez wywołanie metody, która określa maksymalną wartość z wielu wywołań funkcji. Wywoływana funkcja tworzy bardzo dużej liczby losowe wartości, a następnie zwraca ostatnią. Dane są wyświetlane w polu tekstowym.  
  
1.  Utwórz nowy projekt aplikacji C# uniwersalnych systemu Windows o nazwie **CpuUseDemo** przy użyciu **BlankApp** szablonu.  
  
     ![Utwórz CpuUseDemoProject](../profiling/media/cpu_use_newproject.png "CPU_USE_NewProject")  
  
2.  Zastąp MainPage.xaml z [ten kod](#BKMK_MainPage_xaml).  
  
3.  Zastąp MainPage.xaml.cs z [ten kod](#BKMK_MainPage_xaml_cs).  
  
4.  Tworzenie aplikacji i wypróbować jej możliwości. Aplikacja jest proste pokazać, niektóre typowe przypadki użycia procesora CPU analizy danych.  
  
##  <a name="BKMK_Collect_CPU_usage_data"></a>Zbieranie danych o użyciu procesora CPU  
 ![Uruchom kompilację wersji aplikacji w symulatorze](../profiling/media/cpu_use_wt_setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1.  W programie Visual Studio ustawioną cel wdrożenia **symulatora** i konfigurację rozwiązania na **wersji**.  
  
    -   Uruchamianie aplikacji w symulatorze pozwala łatwo przełączać się między aplikacji i środowiska IDE programu Visual Studio.  
  
    -   Uruchamianie tej aplikacji w **wersji** tryb daje lepszego widoku Rzeczywista wydajność aplikacji.  
  
2.  Na **debugowania** menu, wybierz **profilera wydajności...** .  
  
3.  W Centrum diagnostyki i wydajności wybierz **użycie procesora CPU** , a następnie wybierz **Start**.  
  
     ![Rozpocznij sesję diagnostyki CpuUsage](../profiling/media/cpu_use_wt_perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4.  Po uruchomieniu aplikacji, kliknij przycisk **uzyskać maksymalna liczba**. Oczekiwania dotyczące sekundy po danych wyjściowych jest wyświetlany, a następnie wybierz pozycję **uzyskać maksymalny numer Async**. Oczekiwanie między kliknięcia przycisków sprawia, że ułatwiają izolować przycisku kliknij procedury w raport diagnostyczny.  
  
5.  Gdy zostanie wyświetlony drugi wiersz danych wyjściowych, wybierz **zatrzymania zbierania** w Centrum wydajności i diagnostyki.  
  
 ![Zatrzymaj zbieranie danych CpuUsage](../profiling/media/cpu_use_wt_stopcollection.png "CPU_USE_WT_StopCollection")  
  
 Narzędzia użycie procesora CPU analizuje dane i wyświetla raport.  
  
 ![Raport CpuUsage](../profiling/media/cpu_use_wt_report.png "CPU_USE_WT_Report")  
  
##  <a name="BKMK_Analyze_the_CPU_Usage_report"></a>Analizowanie raportu użycia procesora CPU  
  
###  <a name="BKMK_CPU_utilization_timeline_graph"></a>Wykres wykorzystania procesora CPU na osi czasu  
 ![CpuUtilization &#40; % &#41; oś czasu wykresu](../profiling/media/cpu_use_wt_timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 Wykres wykorzystania CPU pokazuje aktywności Procesora aplikacji jako procent wszystkich czas procesora CPU od wszystkich rdzeni procesora w urządzeniu. Na komputerze dwurdzeniowy zbierania danych tego raportu. Dwie duże wartości szczytowe reprezentują aktywności Procesora kliknięcia przycisków dwa. `GetMaxNumberButton_Click`dokonuje synchronicznie pojedynczego rdzenia, dzięki czemu dobrym rozwiązaniem, że wysokość wykresu metody nigdy nie przekracza 50%. `GetMaxNumberAsycButton_Click`Uruchamia asynchronicznie na obu rdzeni, więc tak, aby ponownie wyglądał prawo który jego kolekcji pobiera bliżej przy użyciu wszystkich zasobów procesora CPU na obu rdzeni.  
  
####  <a name="BKMK_Select_timeline_segments_to_view_details"></a>Wybierz segmentów osi czasu, aby wyświetlić szczegóły  
 Użyj pasków zaznaczenie na **sesji diagnostycznej** osi czasu, aby skupić się na danych GetMaxNumberButton_Click:  
  
 ![GetMaxNumberButton &#95; Kliknij wybrany](../profiling/media/cpu_use_wt_getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 **Sesji diagnostycznej** osi czasu teraz Wyświetla czas w wybranej segmentu (w tym raporcie nieco więcej niż 2 sekundy) i filtry drzewo wywołań do tych metod, którzy uruchomili w zaznaczeniu.  
  
 Teraz wybierz `GetMaxNumberAsyncButton_Click` segmentu.  
  
 ![GetMaxNumberAsyncButton &#95; Kliknij element raportu](../profiling/media/cpu_use_wt_getmaxnumberasync_selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Ta metoda wykonuje o drugiej szybciej niż `GetMaxNumberButton_Click`, znaczenie wpisy drzewa wywołania są mniej oczywista, ale.  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a>Użycie procesora CPU drzewo wywołań  
 Aby rozpocząć, zrozumienie informacji o wywołaniu drzewa, wybierz ponownie `GetMaxNumberButton_Click` segmentu i przyjrzyj się szczegóły drzewa wywołań.  
  
####  <a name="BKMK_Call_tree_structure"></a>Struktura drzewa wywołań  
 ![GetMaxNumberButton &#95; Kliknij przycisk drzewo wywołań](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Węzeł najwyższego poziomu w drzewach wywołania użycia procesora CPU jest pseudo-węzłem|  
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|W przypadku większości aplikacji gdy **Pokaż kod zewnętrzny** opcja zostanie wyłączona, węzeł drugiego poziomu **[kod zewnętrzny]** węzła, który zawiera kod systemu i platformy, który uruchamiania i zatrzymywania aplikacji rysuje interfejsu użytkownika, Steruje planowania wątków i innymi usługami niskiego poziomu do aplikacji.|  
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Element podrzędny węzła drugiego poziomu są metody kodu użytkownika i procedur asynchroniczne, które wywołuje lub utworzony przez system drugiego poziomu i kod framework.|  
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Węzły podrzędne metody zawierają dane tylko w przypadku wywołania metody nadrzędnej. Gdy **Pokaż kod zewnętrzny** jest wyłączona, metody aplikacja może również zawierać **[kod zewnętrzny]** węzła.|  
  
####  <a name="BKMK_External_Code"></a>Kod zewnętrzny  
 Kod zewnętrzny składa się funkcji systemu i framework składników, które są wykonywane przez kod zostanie zapisany. Kod zewnętrzny obejmuje funkcje, które start i Zatrzymaj aplikację, Rysuj interfejsu użytkownika, kontroli wątków i podaj inne niskiego poziomu usług do aplikacji. W większości przypadków będzie zainteresowana kod zewnętrzny i dlatego użycie procesora CPU Wywołaj gromadzi drzewa funkcji zewnętrznych metody użytkownika do jednego **[kod zewnętrzny]** węzła.  
  
 Umożliwia wyświetlanie ścieżek wywołania z kodu zewnętrznego, wybierz **Pokaż kod zewnętrzny** z **filtrowanie widoku** listy, a następnie wybierz pozycję **Zastosuj**.  
  
 ![Wybierz Widok filtrów, a następnie wyświetlić kod zewnętrzny](../profiling/media/cpu_use_wt_filterview.png "CPU_USE_WT_FilterView")  
  
 Należy pamiętać, że wiele łańcuchów wywołanie kodu zewnętrznego głęboko zagnieżdżone, tak, aby szerokość kolumny nazwy funkcji może być dłuższa niż szerokość wyświetlania wszystkich oprócz największy monitorów komputera. W takim przypadku funkcja nazwy są wyświetlane jako **[...]** :  
  
 ![Zagnieżdżone zewnętrznego kodu w drzewie wywołań](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Użyj pola wyszukiwania można znaleźć węzła, którego szukasz, a następnie przełącz do widoku danych za pomocą paska przewijania w poziomie:  
  
 ![Wyszukaj zagnieżdżonych kod zewnętrzny](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a>Kolumny danych drzewa wywołań  
  
|||  
|-|-|  
|**Całkowita liczba Procesora (%)**|![Łączna liczba % danych równości](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Procent aktywności Procesora aplikacji w wybranym zakresie czasu użytej przez wywołania funkcji i funkcji wywoływanych przez funkcję. Należy pamiętać, że jest inny niż **użycie procesora CPU** oś czasu wykresu, który porównuje łączną aktywność dotyczącą aplikacji w zakresie czasu, aby całkowita pojemność procesora CPU.|  
|**Samodzielnie Procesora (%)**|![Samodzielna % równości](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Procent aktywności Procesora aplikacji w wybranym zakresie czasu użytej przez wywołania funkcji, z wyłączeniem aktywności funkcji wywołanych przez funkcję.|  
|**Całkowita liczba procesora CPU (ms)**|Wyrażony w milisekundach czas spędzony w wywołaniach funkcji w wybranym zakresie czasu i funkcje, które zostały wywołane przez funkcję.|  
|**Samodzielnie procesora CPU (ms)**|Wyrażony w milisekundach czas spędzony w wywołaniach funkcji w wybranym zakresie czasu i funkcje, które zostały wywołane przez funkcję.|  
|**Moduł**|Nazwa modułu zawierającego funkcję lub liczba modułów zawierających funkcje w węźle [kod zewnętrzny].|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a>Funkcje asynchroniczne użycia procesora CPU w drzewie wywołań  
 Gdy kompilator napotka metodę asynchroniczną, tworzy ukryte klasę, aby kontrolować wykonywanie metody. Klasa jest koncepcyjnie, zawierający listę generowane przez kompilator funkcje, które asynchroniczne wywoływanie operacji oryginalnej metody i wywołania zwrotne, harmonogram i Iteratory wymagane do nich poprawnie komputera stanu. Oryginalny metoda jest wywoływana przez metodę nadrzędną, środowisko uruchomieniowe usuwa metodę z kontekstu wykonywania elementu nadrzędnego i działa metod klasy ukryte w kontekście systemu i framework kodu, który kontrolować wykonywanie aplikacji. Metody asynchroniczne są często, ale nie zawsze wykonywane na co najmniej jeden inny wątek. Ten kod jest wyświetlany w drzewie wywołań użycie procesora CPU jako elementy podrzędne **[kod zewnętrzny]** węzła bezpośrednio pod górny węzeł drzewa.  
  
 Aby wyświetlić to w naszym przykładzie, wybierz ponownie `GetMaxNumberAsyncButton_Click` segment osi czasu.  
  
 ![GetMaxNumberAsyncButton &#95; Kliknij element raportu](../profiling/media/cpu_use_wt_getmaxnumberasync_selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Pierwsze dwa węzły pod **[kod zewnętrzny]** są generowane przez kompilator metod klasy maszyny stanu. Trzeci jest wywołanie metody oryginalnego. Rozszerzanie wygenerowane metody pokazuje, co się dzieje.  
  
 ![Rozwinięte GetMaxNumberAsyncButton &#95; Kliknij przycisk drzewo wywołań](../profiling/media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click`jest bardzo mało; go zarządza listę wartości zadań oblicza maksymalną liczbę wyników i wyświetla dane wyjściowe.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext`Pokazuje działania wymagane do planowania i uruchamiać 48 zadań, które otaczają wywołanie `GetNumberAsync`.  
  
-   `MainPage::<GetNumberAsync>b__b`Pokazuje aktywności zadań, które wywołują `GetNumber`.  
  
##  <a name="BKMK_Next_steps"></a>Następne kroki  
 Aplikacja CpuUseDemo nie jest najbardziej doskonały aplikacji, ale jego narzędzia można rozszerzyć za pomocą eksperymentowania operację asynchroniczną z innych narzędzi w Centrum wydajności i diagnostyki.  
  
-   Należy pamiętać, że `MainPage::<GetNumberAsync>b__b` zużywa więcej czasu w [kod zewnętrzny] niż wykonania metody GetNumber. Większość tego czasu jest zmniejszenie operacji asynchronicznych. Spróbuj zwiększyć liczbę zadań (w `NUM_TASKS` stała MainPage.xaml.cs) i zmniejszenie liczby iteracji w `GetNumber` (zmiana `MIN_ITERATIONS` wartości). Uruchom scenariusz kolekcji i porównaj aktywności Procesora `MainPage::<GetNumberAsync>b__b`w tym w oryginalnej sesji diagnostyki użycia procesora CPU. Spróbuj zmniejszenie zadań i zwiększenie liczby iteracji.  
  
-   Użytkownicy często nie zależy Ci na zachowaniu rzeczywistą wydajność aplikacji; one interesujących obserwowaną wydajność i szybkość reakcji aplikacji. Narzędzie reakcji interfejsu użytkownika XAML zawiera szczegóły działań w wątku interfejsu użytkownika, że wpływ postrzegany czas odpowiedzi.  
  
     Utwórz nową sesję w Centrum diagnostyki i wydajności i Dodaj zarówno narzędzia reakcji interfejsu użytkownika XAML i użycie procesora CPU. Uruchom scenariusz kolekcji. Jeśli zostały przeczytane to znacznie, raport prawdopodobnie nie informujące wszystkich elementów, które nie zostały już znalezienia, ale różnice w **użycie wątku interfejsu użytkownika** bicie jest oś czasu wykresu dla dwóch metod. W aplikacji złożonych, rzeczywistych kombinację narzędzia może być bardzo przydatne.  
  
##  <a name="BKMK_MainPage_xaml"></a>MainPage.xaml  
  
```xaml  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
##  <a name="BKMK_MainPage_xaml_cs"></a>MainPage.xaml.cs  
  
```CSharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```
## <a name="see-also"></a>Zobacz też
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przegląd funkcji profilowania](../profiling/profiling-feature-tour.md)