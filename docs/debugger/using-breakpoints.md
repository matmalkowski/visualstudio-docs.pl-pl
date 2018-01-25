---
title: "Użyj punktów przerwania w debugerze programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.choose
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords: breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
caps.latest.revision: "57"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e5873276795477778e4c358d59788248230bb4b5
ms.sourcegitcommit: 062795f922e7b59fe00d3d95a01a9a8a28840017
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2018
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Użyj punktów przerwania w debugerze programu Visual Studio
Można ustawić punktów przerwania, aby zatrzymać wykonanie debugera, prawdopodobnie, aby zobaczyć stan zmiennych kodu lub spojrzeć na stosie wywołań. Są one jednym z najważniejszych metod debugowania w przyborniku dewelopera.  
  
##  <a name="BKMK_Overview"></a>Ustawienie wiersza punkt przerwania w kodzie źródłowym  
 Ustawisz wiersza punkt przerwania w kodzie źródłowym przez kliknięcie lewym marginesie pliku kodu źródłowego lub umieszczanie kursor w wierszu kodu i naciskając klawisz F9. Punkt przerwania jest wyświetlany jako czerwonej kropki na lewym marginesie, a wiersz kodu jest również pokolorowane:  
  
 ![Ustaw punkt przerwania](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Po uruchomieniu tego kodu w debugerze wykonywania zatrzymuje zawsze, gdy punkt przerwania zostaje trafiony przed wykonaniem kodu w tym wierszu. Wiersz kodu źródłowego jest kolor żółty:  
  
 ![Punkt przerwania wykonywania zatrzymana](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 W tym momencie wartość `testInt` jest nadal 1.  
  
 Można przyjrzeć się bieżący stan aplikacji, w tym wartości zmiennych i stosu wywołań. Aby uzyskać więcej informacji na temat stos wywołań, zobacz [porady: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).  
  
 Można ustawić punktu przerwania w każdym wierszu kodu wykonywalnego. Na przykład w języku C# kodu powyżej, które można ustawić punktu przerwania w deklaracji zmiennej `for` pętli lub wszelkiego kodu wewnątrz `for` pętli, ale nie można ustawić punktu przerwania w deklaracji przestrzeni nazw lub klasy lub podpis metody.  
  
##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Ustawienie inne rodzaje punkty przerwania  
 Można również ustawić punkty przerwania w stosie wywołań, w oknie dezasemblacji i, w kodzie natywnym języku C++, warunek danych lub adres pamięci.  
  
## <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a>Ustawienia punktu przerwania w oknie stosu wywołań  
 Można przerwać wykonywanie w instrukcji lub wiersza, który funkcji wywołującej, zwraca ustawić punkt przerwania w **stos wywołań** okna. Aby uzyskać więcej informacji na temat stos wywołań, zobacz [porady: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md). Debuger musi zatrzymano wykonywanie.  
  
1.  Rozpocznij debugowanie aplikacji, a wykonanie oczekiwania jest zatrzymana (na przykład w punkcie przerwania). Otwórz **stos wywołań** okna (**debugowania > Windows > stos wywołań**, lub **CTRL + ALT + C**).  
  
2.  Kliknij prawym przyciskiem myszy wywoływania funkcji, a następnie wybierz **punktu przerwania > Wstaw punktu przerwania**, lub użyć klawisza skrótu **F9**.  
  
3.  Symbol punktu przerwania pojawi się na lewym marginesie stos wywołań, obok nazwy wywołania funkcji.  
  
 W **punktów przerwania** , punkt przerwania stosu wywołań okno jako adres z lokalizacji pamięci, która odpowiada następną instrukcję pliku wykonywalnego w funkcji. Debuger dzieli wykonywania w instrukcji.  
  
 Aby wizualnie śledzenia punktów przerwania podczas wykonywania kodu, zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Ustawienia punktu przerwania w oknie dezasemblacji  
 Aby ustawić punkt przerwania w zestawie instrukcji, debuger musi być w trybie przerwania.  
  
1.  Rozpocznij debugowanie aplikacji, a wykonanie oczekiwania jest zatrzymana (na przykład w punkcie przerwania). Otwórz **dezasemblacji** okna (**Debuguj > Windows > dezasemblacji**, lub **Ctrl + Alt + D**).  
  
2.  Kliknij na lewym marginesie w instrukcji, która ma być dzielone w lub ustaw kursor w instrukcji i naciśnij klawisz **F9**.  
  
## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Ustawienia punktu przerwania danych (tylko w macierzystym C++)  
 Punkty przerwania danych przerwać wykonywanie po wartości przechowywanej w zmiany adresu określonego pamięci. Jeśli wartość jest do odczytu, ale nie został zmieniony, nie przerwać wykonywania. Aby ustawić punkty przerwania danych, debuger musi być w trybie przerwania.  
  
1.  Rozpocznij debugowanie aplikacji i zaczekaj, aż do osiągnięcia punktu przerwania. Na **debugowania** menu, wybierz **nowego punktu przerwania > punktu przerwania danych** (lub otworzyć **punktów przerwania** okna i wybierz polecenie **nowy > punktu przerwania danych**.  
  
2.  W **adres** wpisz adres pamięci lub wyrażenie obliczane jako adres pamięci. Na przykład wpisz `&avar` można przerwać, gdy zawartość zmiennej `avar` zmiany.  
  
3.  W **liczba bajtów** listy rozwijanej wybierz liczbę bajtów ma debugera, aby obejrzeć. Na przykład w przypadku wybrania **4**, debuger będzie oczekiwał na czterech bajtów, licząc od `&avar` i przerwać żadnego z tych bajtów zmiany wartości.  
  
 Należy pamiętać, że punkty przerwania danych zależy od możliwości zastosowania adresów pamięci.  
  
-   Adres zmiennej zmienia się z jednej sesji debugowania do następnego. Punkty przerwania danych są automatycznie wyłączane na końcu każdej sesji debugowania.  
  
-   Jeśli ustawisz punktu przerwania danych na zmienną lokalną, pozostaje punktu przerwania włączone, gdy funkcja kończy działanie, ale adres pamięci nie ma już zastosowania, a jest nieprzewidywalne zachowanie punktu przerwania. Jeśli ustawisz punktu przerwania danych w zmiennej lokalnej, należy usunąć lub wyłączyć punkt przerwania przed zakończeniem funkcji.  
  
 Punkty przerwania danych nie działają w tych warunkach:  
  
-   Proces, który nie jest debugowany zapisuje do lokalizacji pamięci  
  
-   Lokalizacja pamięci jest współużytkowana przez dwie lub więcej procesów  
  
-   Lokalizacja pamięci jest aktualizowana jądra. Na przykład, jeśli pamięć jest przekazywana do 32-bitowym systemie Windows `ReadFile` funkcji, pamięć zostanie zaktualizowany z trybu jądra i debuger nie być dzielone w zapisu pamięci.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Ustawianie punktów przerwania z adresem pamięci (tylko w macierzystym C++)  
 Umożliwia także adres obiektu można ustawić punktu przerwania w metodzie wywołana dla określonego wystąpienia klasy.  Oto przykład:  
  
 Na przykład, dla danego typu obiektu `my_class` z adresem, można ustawić punktu przerwania funkcji na metodę o nazwie `my_method` wywołana z tego wystąpienia.  
  
1.  Ustaw punkt przerwania gdzieś po jest tworzone wystąpienie tej klasy.  
  
2.  Znajdowanie adresu wystąpienia (będzie powiedzieć, ma `0xcccccccc`).  
  
3.  Kliknij przycisk **Debuguj > nowego punktu przerwania > punktu przerwania funkcji** (lub **ALT + F9, B**).  
  
4.  Dodaj poniższy tekst do **nazwy funkcji** pola:  
  
    ```C++  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Zarządzanie punkty przerwania  
 Można użyć **punktów przerwania** okna (**debugowania > Windows > punktów przerwania**, lub **CTRL + ALT + B**) aby wyświetlić wszystkie punkty przerwania ustawiony w rozwiązaniu:  
  
 ![Okno punktów przerwania](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 **Punktów przerwania** okna udostępnia centralne miejsce do zarządzania punkty przerwań, które mogą być szczególnie przydatne w dużym rozwiązaniem lub złożonych scenariuszach debugowania, gdzie są kluczowe punkty przerwania. Jeśli trzeba zapisać lub korzysta z lokalizacji zestawu punktów przerwania i stanu, możesz można eksportować i importować punktów przerwania tylko z **punktów przerwania** okna.  
  
##  <a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>Zaawansowane punkty przerwania  
  
## <a name="breakpoint-conditions"></a>Warunków punktu przerwania  
 Można kontrolować, kiedy i gdzie punkt przerwania wykonuje się przez ustawienie warunków.  
  
1.  Kliknij prawym przyciskiem myszy punkt przerwania lub umieść kursor nad punkt przerwania i wybierz ikonę ustawień.  
  
2.  W menu kontekstowego wybierz **warunki**. Spowoduje to otwarcie **ustawienia punktów przerwania** okno:  
  
 ![Ustawienia punktów przerwania](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
 Sprawdzenie **warunki** okno, oknie zostanie wyświetlona różnych rodzajów warunków.  
  
 **Wyrażenie warunkowe:** po wybraniu wyrażenia warunkowego, można wybrać dwa warunki: **ma wartość true** i **po zmianie**. Wybierz **ma wartość true** Jeśli chcesz podzielić gdy wyrażenie jest spełniony, lub wybierz **po zmianie** aby Przerwij, gdy zmieniono wartość wyrażenia.  
  
 W poniższym przykładzie możemy ustawić punkt przerwania trafienie tylko wtedy, gdy wartość `testInt` jest **4**:  
  
 ![Punkt przerwania warunek jest spełniony](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
 W poniższym przykładzie możemy ustawić punkt przerwania trafienie tylko wtedy, gdy wartość `testInt` zmiany:  
  
 ![Punkt przerwania po zmianie](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
 Zachowanie When zmienione pole jest różne dla różnych języków programowania. Jeśli wybierzesz **po zmianie** dla kodu natywnego debugera nie należy wziąć pod uwagę pierwszej oceny tego warunku na zmiany, aby punkt przerwania nie są osiągane w pierwszej oceny. Jeśli wybierzesz **po zmianie** dla zarządzanego kodu punkt przerwania zostaje trafiony na pierwszej oceny po **po zmianie** jest zaznaczone.  
  
 Jeśli ustawisz warunku punktu przerwania z nieprawidłową składnią, zostanie wyświetlony komunikat ostrzegawczy. Jeśli określisz warunku punktu przerwania z prawidłowej składni, ale nieprawidłowej semantyce, pojawi się ostrzeżenie punkt przerwania zostaje trafiony po raz pierwszy. W obu przypadkach debuger dzieli wykonywania, gdy nieprawidłowy punkt przerwania zostaje trafiony. Punkt przerwania zostanie pominięty, tylko wtedy, gdy warunek jest prawidłowa i daje w wyniku `false`.  
  
 Warunek może być prawidłowym wyrażeniem, który jest rozpoznawany przez debuger. Aby uzyskać więcej informacji na temat prawidłowe wyrażenia, zobacz [wyrażeń w debugerze](../debugger/expressions-in-the-debugger.md).  

> [!NOTE]
> Można użyć **klawisze CTRL + Enter** zamknąć **ustawienia punktów przerwania** okna.
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Używanie wartości identyfikatorów obiektów w warunków punktu przerwania (C# i F #)  
 Istnieją momenty, gdy chcesz obserwować zachowanie określonego obiektu; na przykład możesz dowiedzieć się, dlaczego obiektu dodano więcej niż raz w kolekcji. W języku C# i F # można utworzyć obiektu identyfikatory określone wystąpienia [typy referencyjne](/dotnet/csharp/language-reference/keywords/reference-types) i używać ich w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez środowisko uruchomieniowe języka wspólnego (CLR) debugowanie usług i skojarzone z obiektem.  Aby utworzyć identyfikator obiektu, wykonaj następujące czynności:  
  
1.  Ustaw punkt przerwania w kodzie pewien czas, po utworzeniu obiektu.  
  
2.  Rozpocznij debugowanie, a podczas wykonywania zatrzyma się punkt przerwania, znaleźć punkt przerwania w **zmiennych lokalnych** okna, kliknij go prawym przyciskiem myszy i wybierz **wprowadzić identyfikator obiektu**.  
  
     Powinny pojawić się  **$**  plus liczbą **zmiennych lokalnych** okna. Jest to identyfikator obiektu.  
  
3.  Dodać nowego punktu przerwania warunkowe w momencie, że chcesz zbadać, na przykład gdy obiekt jest ma zostać dodany do kolekcji.  
  
4.  Użyj Identyfikatora obiektu w polu wyrażenia warunkowego. Na przykład, jeśli jest zmienną `item` odwołujące się do obiektu, który ma zostać dodany do kolekcji, możesz przełączyć **elementu == $n**, gdzie  **n**  jest numer Identyfikatora obiektu.  
  
     Wykonanie spowoduje przerwanie w punkcie, jeśli ten obiekt ma zostać dodany do kolekcji.  
  
 Jeśli chcesz później usunąć identyfikator obiektu, należy kliknąć prawym przyciskiem myszy zmiennej w **zmiennych lokalnych** i zaznacz **Usuń identyfikator obiektu**.  
  
 Należy pamiętać, identyfikatory obiektów utworzyć słabe odwołania, a nie uniemożliwiają obiektu bezużytecznych. Są one prawidłowe tylko dla bieżącej sesji debugowania.  
  
## <a name="hit-count"></a>Liczba trafień  
 Jeśli podejrzewasz, że rozpoczyna się pętlę w kodzie, zachowania po określonej liczby iteracji, możesz ustawić punkt przerwania, aby zatrzymać wykonanie po upływie określonej liczby trafień do skojarzonego z nim wiersza kodu, a nie wymuszaniu naciskaj klawisz **F5**  do osiągnięcia poziomu iteracji.  
  
 W **ustawienia punktów przerwania** okna, warunek na **liczba trafień**. Następnie możesz określić liczbę iteracji. W poniższym przykładzie możemy ustawić punkt przerwania trafienie w każdej iteracji inne:  
  
 ![Liczba trafień punktu przerwania](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtr  
 Można ograniczyć uruchomienie tylko dla określonego urządzenia lub w określonych procesów i wątków punkt przerwania.  
  
 W **ustawienia punktu przerwania**okna s warunek na **filtru**. Wprowadź co najmniej jeden z następujących wyrażeń.  
  
-   MachineName = "name"  
  
-   Identyfikator procesu = wartość  
  
-   ProcessName = "name"  
  
-   Identyfikator wątku = wartość  
  
-   ThreadName = "name"  
  
 Wartości parametrów należy ująć w cudzysłów. Możesz połączyć ze sobą przy użyciu klauzuli `&` (AND) `||` (lub), `!` (nie) i nawiasy.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Punkt przerwania działania i Tracepoints  
 Śledzenia jest punkt przerwania, która wyświetla komunikat w oknie danych wyjściowych. Śledzenia mogą pełnić rolę instrukcję tymczasowego śledzenia w języku programowania.  
  
 W **ustawienia punktów przerwania** okno wyboru **akcje** pole. Wybierz **Rejestruj komunikat w oknie danych wyjściowych** w **akcji** grupy. Można wydrukować ciągu ogólny, takich jak **to jest test**. Aby uwzględnić wartość zmiennej lub wyrażenie, należy ująć go w nawiasy klamrowe.  
  
 Aby Przerwij wykonywanie, gdy zostaje trafiony śledzenia, wyczyść **kontynuować wykonywania** pole wyboru. Gdy **kontynuować wykonywania** zaznaczono wykonywania nie jest zatrzymywany. W obu przypadkach wiadomość jest drukowana.  
  
 Można użyć poniższych specjalnych słów kluczowych w **komunikat**.  
  
|||  
|-|-|  
|**$ADDRESS**|Bieżącej instrukcji|  
|**$CALLER**|Nazwa funkcji wywołania|  
|**$CALLSTACK**|Stos wywołań|  
|**$FUNCTION**|Nazwa bieżącej funkcji|  
|**$PID**|Identyfikator procesu|  
|**$PNAME**|Nazwa procesu|  
|**$TID**|Identyfikator wątku|  
|**$TNAME**|Nazwa wątku|  
|**$TICK**||  
|**$TNAME**||  
  
##  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Etykiety punktów przerwania  
 Etykiety punktów przerwania są używane tylko w **punktów przerwania** okno, aby sortować i filtrować listy punktów przerwania. Aby dodać etykietę do punktu przerwania, wybierz wiersz punkt przerwania, a następnie wybierz **etykiety** w menu kontekstowym.  
  
## <a name="export-and-import-breakpoints"></a>Funkcje eksportu i importu punkty przerwania  
 Punkt przerwania można wyeksportować do pliku XML, prawym przyciskiem myszy punkt przerwania i wybierając **wyeksportować**. Plik jest zapisywany w katalogu rozwiązania domyślnie. Aby zaimportować punktów przerwania, otwórz **punktów przerwania** okna (**CTRL + ALT + B**) i na pasku narzędzi kliknij przycisk strzałki w prawo (element tooltip jest **Importuj punkty przerwania z pliku**) .  
  
## <a name="see-also"></a>Zobacz też  
[Rozwiązywanie problemów z punktów przerwania w debugerze programu Visual Studio](../debugger/troubleshooting-breakpoints.md)  
[Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)
