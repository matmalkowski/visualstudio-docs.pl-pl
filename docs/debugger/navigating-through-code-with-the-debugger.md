---
title: Przejdź do kodu za pomocą debugera programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae96b360620a58fa323d080e6262c7f2966fa160
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479748"
---
# <a name="navigate-code-with-the-visual-studio-debugger"></a>Przejdź do kodu za pomocą debugera programu Visual Studio
Zapoznaj się z poleceń i skrótów, przejdź do kodu w debugerze i który ułatwi szybsze i łatwiejsze do znalezienia i rozwiąż problemy w aplikacji. Podczas nawigacji kodu w debugerze, można sprawdzić stan aplikacji lub Dowiedz się więcej o przepływ wykonania.  
  
## <a name="start-debugging"></a>Rozpocznij debugowanie  
 Często, można uruchomić debugowania przy użyciu sesji **F5** (**debugowania** > **Rozpocznij debugowanie**). To polecenie uruchamia aplikację w debugerze.  
  
 Zieloną strzałkę również uruchomienie debugera (taki sam jak **F5**).  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")  
  
 Obejmują kilka innych sposobów, że można uruchomić aplikację w debugerze **F11** ([Wkrocz do kodu](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([Przekrocz kod](#BKMK_Step_over_Step_out)), lub przy użyciu **Uruchom do kursora**.  Zobacz pozostałe sekcje w tym temacie, aby uzyskać informacje na czy te opcje.  
  
 Podczas debugowania, żółty wiersz zawiera kod, który zostanie wykonany następny.  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg_basics_break_mode.png "DBG_Basics_Break_Mode")  
  
 Podczas debugowania, można przełączać się między poleceń, takich jak **F5**, **F11** i korzystanie z innych funkcji opisanych w tym temacie (np. punkty przerwania), aby szybko uzyskać dostęp do kodu, aby przyjrzeć się.  
  
 Większość funkcji debugera, takie jak wyświetlanie wartości zmiennych w oknie zmienne lokalne lub obliczenia wyrażenia w oknie wyrażeń kontrolnych są dostępne tylko wtedy, gdy debuger został wstrzymany (nazywane również *tryb przerwania*). Gdy debuger jest wstrzymana, swój stan aplikacji jest wstrzymana podczas zmienne, funkcje i obiekty pozostają w pamięci. Podczas pracy w trybie przerwania należy zbadać położenia elementów członkowskich i stanów szukać naruszenia lub usterki. Dla niektórych typów projektów może również wprowadzać zmiany do aplikacji w trybie przerwania. Aby obejrzeć film przedstawiający tych funkcji, zobacz [wprowadzenie do debugera](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Wykonywanie kodu, wiersz po wierszu  
 Aby zatrzymać w każdym wierszu kodu (każda instrukcja) podczas debugowania, użyj **F11** skrót klawiaturowy (lub **debugowania** > **Step Into** menu).  
  
> [!TIP]
>  Jak wykonać każdego wiersza kodu, można umieść kursor nad zmienne, aby wyświetlić ich wartości, lub użyj [zmiennych lokalnych](../debugger/autos-and-locals-windows.md) i [czujki](../debugger/autos-and-locals-windows.md) systemu windows, aby obejrzeć zmiany wartości.  
  
 Poniżej przedstawiono niektóre szczegóły na temat zachowania **Step Into**:  
  
-   W wywołaniu funkcji zagnieżdżonej **Step Into** kroków w najbardziej głęboko zagnieżdżone, funkcja. Jeśli używasz **Step Into** na wywołanie, takich jak `Func1(Func2())`, debuger kroki do funkcji `Func2`.  
  
-   Debuger faktycznie przechodzi przez instrukcje kodu zamiast fizycznej wierszy. Na przykład `if` klauzuli mogą być zapisywane w jednym wierszu:  
  
    ```csharp  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```VB  
    Dim x As Integer = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     Podczas wykonywania kroków w tym wierszu debuger traktuje warunek jako jeden krok i konsekwencji jak inny (w tym przykładzie warunku jest PRAWDA).  
  
 Wizualne śledzenie stosu wywołań podczas Wkraczanie do funkcji, zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Step_over_Step_out"></a> Krokowo kodu, pomijanie funkcji  
 Podczas uruchamiania kodu w debugerze, często będą okazuje się, że nie chcesz wyświetlać, co dzieje się w określonej funkcji (nie zależy Ci na jego temat lub znasz jej działania, takie jak kod biblioteki dobrze przetestowany). Używać tych poleceń, aby przejść przez kod (funkcje nadal wykonywać, oczywiście, ale debuger nakłada się na nich).  
  
|Polecenie klawiatury|Polecenia menu|Opis|  
|----------------------|------------------|-----------------|  
|**F10**|**Przekrocz**|Jeśli bieżący wiersz zawiera wywołanie funkcji **Step Over** uruchamia kod, a następnie wstrzymuje wykonywanie w pierwszym wierszu kodu po powrocie wywołanej funkcji.|  
|**Shift+F11**|**Wyjdź**|**Step Out** kontynuuje wykonywanie kodu i wstrzymuje wykonywanie, gdy bieżąca funkcja zwraca (pomija debugera za pomocą funkcji current).|  
  
> [!TIP]
>  Aby znaleźć punkt wejścia w aplikacji należy uruchomić z **F10** lub **F11**. Polecenia te często są przydatne podczas sprawdzania stanu Twojej aplikacji i dowiedzieć się więcej o przepływie jej wykonanie w trakcie.  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Uruchom w określonej lokalizacji lub funkcji  
 Często preferowaną metodą debugowania kodu, te metody są przydatne, gdy wiesz dokładnie kodu, które chcesz sprawdzić lub co najmniej wiadomo, które chcesz rozpocząć debugowania.  
  
-   **Ustaw punkty przerwania w kodzie**  
  
     Aby ustawić proste punktu przerwania w kodzie, otwórz plik źródłowy w edytorze programu Visual Studio. Ustaw kursor w wierszu kodu, w którym chcesz wstrzymać wykonywania, a następnie kliknij prawym przyciskiem myszy w oknie Kod, aby wyświetlić menu kontekstowe i wybrać **punktu przerwania > Wstaw punktu przerwania** (lub naciśnij klawisz **F9**). Debuger wstrzymuje prawa do wykonania przed wykonaniem wiersza.  
  
     ![Ustaw punkt przerwania](../debugger/media/dbg_basics_setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Punkty przerwania w programie Visual Studio zapewniają bogaty zestaw dodatkowe funkcje, takie jak warunkowych punktów przerwania i tracepoints. Zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md).  
  
-   **Uruchom w lokalizacji kursora**  
  
     Aby uruchomić w lokalizacji kursora, umieść kursor w pliku wykonywalnego wiersza kodu w oknie źródła. W menu kontekstowym edytora (kliknij prawym przyciskiem myszy w edytorze), wybierz **Uruchom do kursora**. Jest to takie jak ustawienie tymczasowego punktu przerwania.

-   **Uruchom kliknięcie** 

    Aby uruchomić do punktu w kodzie, podczas gdy wstrzymaniu w debugerze, zaznacz **uruchomienia wykonania dotąd** ikona zieloną strzałkę (pojawi się ikona podczas kursora myszy nad wiersz kodu). Eliminuje to potrzebę ustawienia tymczasowych punktów przerwania.

    ![Debuger do uruchomienia kliknij](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

    > [!NOTE]
    > **Uruchom kliknięcie** jest nowa w programie [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].
  
-   **Ręcznie podzielić kodu**  
  
     Przerwanie i przejście do następnego wiersza kodu w aplikację wykonującego dostępne, wybierz **debugowania**, **podziału wszystkich** (klawiatury: **Ctrl + Alt + Break**). 
  
     Jeśli możesz przerwać podczas wykonywania kodu bez odpowiadającego jej źródła lub symboli (.pdb), pliki), debuger wyświetla **nie znaleziono źródła plików** lub **nie można odnaleźć symboli** strony, które mogą pomóc znaleźć odpowiednie pliki. Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Jeśli nie masz dostępu do plików pomocniczych, nadal można debugować instrukcji zestawu z okna dezasemblacji.  
  
-   **Uruchamianie funkcji w stosie wywołań**  
  
     W **stos wywołań** okna (dostępne podczas debugowania), wybierz funkcję, kliknij prawym przyciskiem myszy i wybierz opcję **Uruchom do kursora**. Wizualne śledzenie stosu wywołań, zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
-   **Uruchom funkcję określona na podstawie nazwy**  
  
     Można ustalić debugera do uruchamiania aplikacji, dopóki nie osiągnie podanej funkcji. Można określić funkcji według nazwy lub wybierz go ze stosu wywołań.  
  
     Aby określić funkcję według nazwy, wybierz **debugowania**, **nowego punktu przerwania**, **dzielone w funkcji**, wprowadź nazwę funkcji i inne informacje identyfikacyjne.  
  
     ![Okno dialogowe Nowy punkt przerwania](../debugger/media/dbg_execution_newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Jeśli funkcja jest przeciążony lub w wielu przestrzeni nazw, można wybrać funkcje, które chcesz **wybierz punkty przerwania** okno dialogowe.  
  
     ![Wybierz punkty przerwania — okno dialogowe](../debugger/media/dbg_execution_overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Przesuń wskaźnik do wykonywania przepływ zmian  
 Gdy debuger jest wstrzymana, można przenieść wskaźnik instrukcji można ustawić następnej instrukcji na wykonanie kodu. Żółty grot strzałki na marginesie źródłowego lub dezasemblacji okno oznacza lokalizację następną instrukcję do wykonania. Przez przeniesienie tego grot strzałki, można pominąć części kodu lub powrócić do wiersza, który został wcześniej wykonywane. Możesz użyć tego w sytuacjach, takich jak pominięcie części kodu, który zawiera usterkę, znane.  
  
 ![Przesuń wskaźnik](../debugger/media/dbg_basics_example3.gif "DBG_Basics_Example3")
  
 Aby ustawić następnej instrukcji do wykonania, użyj jednej z tych procedur:  
  
-   W oknie źródła przeciągnij żółty grot do lokalizacji, w której chcesz ustawić następnej instrukcji w tym samym pliku źródłowego  
  
-   W oknie źródła, ustaw kursor w wierszu, który chcesz wykonać obok, kliknij prawym przyciskiem myszy i wybierz opcję **ustawienia następnej instrukcji**.  
  
-   W oknie dezasemblacji Ustaw kursor w instrukcji zestawu, który ma zostać następnej, kliknij prawym przyciskiem myszy i wybierz polecenie **ustawienia następnej instrukcji**.  
  
> [!CAUTION]
>  Ustawienie następnej instrukcji powoduje, że licznik programu bezpośrednio przejść do nowej lokalizacji. Użyj tego polecenia należy zachować ostrożność przy:  
>   
>  -   Instrukcje między punktami wykonywania stary i nowy nie zostaną wykonane.  
> -   Przenieść punkt wykonywania z poprzednimi wersjami, instrukcje pośredniczące nie są cofnąć.  
> -   Zazwyczaj przenoszenia następnej instrukcji do innej funkcji lub zakres powoduje uszkodzenie stosu wywołań, powodując błąd w czasie wykonywania lub wyjątku. Podczas przenoszenia następnej instrukcji do innego zasięgu debuger otwiera okno dialogowe z ostrzeżeniem i daje możliwość anulowania operacji. W języku Visual Basic nie można przenieść do innego zasięgu lub funkcja następnej instrukcji.  
> -   W natywnym kodzie C++ Jeśli jest włączona, sprawdzania czasu wykonywania ustawienie następnej instrukcji może spowodować wyjątek zostanie wygenerowany, gdy wykonanie dociera do końca metody.  
> -   Gdy Edytuj i Kontynuuj jest włączona, **ustawienia następnej instrukcji** kończy się niepowodzeniem, jeśli wprowadzono zmiany, które Edytuj i Kontynuuj nie można ponownie zamapować natychmiast. Może to występować, na przykład edytując kod w bloku catch. W takim przypadku zobaczysz komunikat o błędzie informujący, że operacja nie jest obsługiwana.  
  
> [!NOTE]
>  W kodzie zarządzanym nie można przenieść następnej instrukcji w następujących warunkach:  
>   
>  -   Następna instrukcja, znajduje się w innej metody niż bieżącej instrukcji.  
> -   Debugowanie został uruchomiony przy użyciu Just In Time debugowania.  
> -   Rozwinięcie stos wywołań jest w toku.  
> -   Zgłoszono wyjątek System.StackOverflowException lub System.Threading.ThreadAbortException.  
  
 Nie można ustawić następnej instrukcji, aktywnie uruchomionej aplikacji. Aby ustawić następnej instrukcji, debuger musi być w trybie przerwania.  
  
## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Wykonywanie kodu niezwiązanych z użytkownikiem  
 Domyślnie debuger próbuje wyświetlić tylko kodu aplikacji podczas debugowania, który jest określany przez debuger nosi nazwę *tylko mój kod*. (Zobacz [tylko mój kod](../debugger/just-my-code.md) aby zobaczyć, jak to działa dla różnych typach projektów i języków i jak mogą dostosować zachowanie.) Jednak czasami podczas debugowania, możesz chcieć przyjrzeć się framework kodu, kod biblioteki innych firm lub wywołań do systemu operacyjnego (wywołań systemowych).  
  
 Możesz wyłączyć opcję tylko mój kod, przechodząc do **narzędzia** > **opcje** > **debugowanie** i wyczyść **Włącz opcję tylko mój kod** wyboru.  
  
 Po wyłączeniu tylko mój kod debuger może wkroczyć do kodu innych użytkowników, a kodu innych użytkowników są wyświetlane w oknach debugera.  
  
> [!NOTE]
>  Tylko mój kod nie jest obsługiwane dla projektów urządzenia.  
  
 **Krok do wywołania systemowe**  
  
 Załadowano symbole debugowania kodu systemu, nie włączono opcję tylko mój kod może Wkrocz wywołanie systemu tak jak w innych połączeń.  
  
 Aby uzyskać dostęp do plików symboli firmy Microsoft, zobacz [wyszukiwać pliki symboli nie na komputerze lokalnym przy użyciu serwerów symboli](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) w [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) tematu.  
  
 Aby załadować symbole dla składnika systemu podczas debugowania:  
  
1.  Otwórz okno modułów (klawiatury: **Ctrl + Alt + U**).  
  
2.  Wybierz moduł, który chcesz załadować symboli dla elementu.  
  
     Można określić, które moduły mają załadować symboli, analizując **stan Symbol** kolumny.  
  
3.  Wybierz **załadować symbole** w menu kontekstowym.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Wkraczać do właściwości i operatory w kodzie zarządzanym  
 Kroki debugera nad właściwościami i operatorami w kodzie zarządzanym domyślnie. W większości przypadków ta zapewnia lepsze debugowania. Aby włączyć Przechodzenie do właściwości lub operatorów, należy wybrać **debugowania** > **opcje**. Na **debugowanie** > **ogólne** wyczyść **Przekrocz nad właściwościami i operatorami (tylko kod zarządzany)** pole wyboru