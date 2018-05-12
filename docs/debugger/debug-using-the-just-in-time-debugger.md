---
title: Debugowanie za pomocą debugera just in Time | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/06/17
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 17dc34cd030bf2eab430872a191424fb657d6cd0
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Debugowanie za pomocą debugera just in Time programu Visual Studio
Debugowanie Just In Time uruchamia program Visual Studio automatycznie po wyjątku lub awarii w aplikacji, która działa poza Visual Studio. Dzięki temu można przetestować aplikację, gdy nie jest uruchomiony program Visual Studio i rozpocząć debugowanie przy użyciu programu Visual Studio, gdy występuje problem.

Debugowanie Just In Time działa w przypadku aplikacji klasycznych systemu Windows. Nie działa dla uniwersalnych aplikacji systemu Windows, a nie działa dla zarządzanego kodu, który znajduje się w natywnej aplikacji, na przykład Wizualizatorów.

> [!TIP] 
> Jeśli chcesz, aby wiedzieć, jak reagować na Just in Time debugera — okno dialogowe, zobacz [w tym temacie](../debugger/just-in-time-debugging-in-visual-studio.md).

##  <a name="BKMK_Enabling"></a> Włącz lub wyłącz Just In Time debugowania  
Można włączyć lub wyłączyć debugowanie w programie Visual Studio Just In Time **Narzędzia > Opcje** okno dialogowe.
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Włącz lub wyłącz Just In Time debugowania  
  
1.  Otwórz program Visual Studio z uprawnieniami administratora (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom jako administrator**).

    Włączanie lub wyłączanie Just In Time debugowania ustawienie klucza rejestru, a uprawnienia administratora może być konieczna zmiana tego klucza.
    
2. Na **narzędzia** menu, kliknij przycisk **opcje**.
  
2.  W **opcje** okna dialogowego rozwiń **debugowanie** węzła.  
  
3.  W **debugowanie** węzła, wybierz opcję **Just In Time**.

    ![Włącz lub Wyłącz debugowanie JIT](../debugger/media/dbg-jit-enable-or-disable.png "włączyć lub wyłączyć debugowanie JIT") 
  
4.  W **just in Time włączyć debugowanie z tych typów kodu** wybierz lub wyczyść typów programów odpowiednich: **zarządzane**, **natywnego**, lub **skryptu**.    
  
5.  Kliknij przycisk **OK**.  
  
Debugowanie Just In Time może nadal być włączone, nawet jeśli program Visual Studio nie jest już zainstalowane na tym komputerze. Visual Studio nie jest zainstalowany, nie można wyłączyć debugowanie w programie Visual Studio Just In Time **opcje** okno dialogowe. W takim przypadku można wyłączyć debugowanie, edytując rejestr systemu Windows Just In Time.  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Aby wyłączyć debugowanie edytując rejestr Just In Time  
  
1.  Na **Start** menu Wyszukaj i uruchom `regedit.exe`  
  
2.  W **Edytora rejestru** okna, odszukaj i Usuń następujące wpisy rejestru:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\Software\Microsoft\.NETFramework\DbgManagedDebugger  

    ![Klucz rejestru JIT](../debugger/media/dbg-jit-registry.png "klucza rejestru JIT") 
  
3.  Jeśli na komputerze jest uruchomiony 64-bitowym systemie operacyjnym, Usuń następujące wpisy rejestru również:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger  
  
4.  Należy zadbać, aby nie przypadkowo usunąć lub zmienić dowolne klucze rejestru.  
  
5.  Zamknij **Edytora rejestru** okna.   
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Włącz Just In Time debugowania formularza systemu Windows  
  
1.  Domyślnie w aplikacji formularzy systemu Windows mają obsługi wyjątków najwyższego poziomu, która pozwala programowi na nadal działać, jeśli można go odzyskać. Na przykład w aplikacji Windows Forms zgłasza nieobsługiwany wyjątek, zostanie wyświetlony okno dialogowe podobne do poniższych:  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     Aby włączyć Just In Time debugowanie aplikacji formularzy systemu Windows, należy wykonać następujące dodatkowe czynności:  
  
2.  Ustaw `jitDebugging` do wartości `true` w `system.windows.form` sekcji pliku machine.config lub  *\<Nazwa aplikacji >*. exe.config pliku:  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  W aplikacji formularzy systemu Windows w języku C++, należy także ustawić `DebuggableAttribute` w pliku .config lub w kodzie. Jeśli kompilacji z [/zi](/cpp/build/reference/z7-zi-zi-debug-information-format) i bez [/Og](/cpp/build/reference/og-global-optimizations), kompilator ustawia tego atrybutu. Jeśli chcesz debugować kompilacji wydania niezoptymalizowaną, jednak należy ustawić samodzielnie. Można to zrobić, dodając następujący wiersz do użytkownika w przypadku pliku AssemblyInfo.cpp aplikacji:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.DebuggableAttribute>.  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Użyj debugowania Just In Time  
 W tej sekcji przedstawiono, co się stanie, jeśli plik wykonywalny zgłasza wyjątek.  
  
 Musi mieć zainstalowanego dla poniższych kroków programu Visual Studio. Jeśli nie masz programu Visual Studio, możesz pobrać bezpłatną [programu Visual Studio Community Edition](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).  
  
 Upewnij się, że Just-In-Time debugowanie jest [włączone](#BKMK_Enabling).
  
 Na potrzeby tej sekcji wybierzemy aplikacji konsolowej C# w programie Visual Studio, która zgłasza [NullReferenceException](http://msdn.microsoft.com/Library/658af786-d893-4114-a3c5-31c7d586056a).  
  
 W programie Visual Studio Utwórz aplikację konsoli języka C# (**Plik > Nowy > Projekt > Visual C# > aplikacji konsoli**) o nazwie **ThrowsNullException**. Aby uzyskać więcej informacji na temat tworzenia projektów programu Visual Studio, zobacz [wskazówki: Tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  
  
 Po otwarciu projektu w programie Visual Studio Otwórz plik Program.cs. Zastąp następujący kod, który wyświetla wiersz do konsoli i zgłasza wyjątek NullReferenceException metody Main():  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  Aby tej procedury, aby pracować w [konfiguracji wydanie](../debugger/how-to-set-debug-and-release-configurations.md), należy wyłączyć [tylko mój kod](../debugger/just-my-code.md). W programie Visual Studio, kliknij przycisk **Narzędzia > Opcje**. W **opcje** okno dialogowe, wybierz opcję **debugowanie**. Usuń zaznaczenie z **Włącz opcję tylko mój kod**.  
  
 Skompiluj rozwiązanie (w programie Visual Studio, wybierz **kompilacji > Kompiluj ponownie rozwiązanie**). Możesz wybrać debugowania lub konfigurację wydania (wybierz **debugowania** dla pełne środowisko debugowania). Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [opis konfiguracji kompilacji](../ide/understanding-build-configurations.md).  
  
 Proces kompilacji tworzy ThrowsNullException.exe pliku wykonywalnego. Można go znaleźć w folderze, w którym utworzono projektu C#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** lub **...\ThrowsNullException\ThrowsNullException\bin\Release**.  
  
 Kliknij dwukrotnie ThrowsNullException.exe. Powinny zostać wyświetlone okno polecenia następująco:  
  
 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")  
  
 Po kilku sekundach wyświetli się okno błędu:  
  
 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")  
  
 Nie klikaj pozycji **anulować**! Po kilku sekundach, powinny pojawić się dwa przyciski **debugowania** i **Zamknij program**. Kliknij przycisk **debugowania**.  
  
> [!CAUTION]
>  Jeśli aplikacja zawiera kodzie niezaufanym, zostanie wyświetlone okno dialogowe z ostrzeżeniem zabezpieczeń. To okno dialogowe umożliwia zdecydować, czy kontynuować debugowanie. Przed kontynuowaniem debugowania, zdecyduj, czy ufasz kodowi. Czy pisania kodu użytkownika? Czy można ufać koder? Jeśli aplikacja jest uruchomiona na komputerze zdalnym, czy znasz nazwę procesu? Nawet wtedy, gdy aplikacja jest uruchomiona lokalnie, który nie musi oznaczać, że może to być zaufane. Należy wziąć pod uwagę możliwość wykonywania złośliwego kodu na komputerze. Jeśli zdecydujesz, że kod zamierzasz debugowania jest zaufane, kliknij przycisk **debugowania**. W przeciwnym razie kliknij przycisk **nie debugowania**.  
  
 **Debuger just in Time programu Visual Studio** zostanie wyświetlone okno:  
  
 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")  
  
 W obszarze **możliwe debugery**, powinny pojawić się który **nowe wystąpienie programu Microsoft Visual Studio <available version>**  wybrany wiersz. Jeśli go nie została już wybrana, wybierz go.  
  
 W dolnej części okna w obszarze **chcesz debugować przy użyciu wybranego debugera?**, kliknij przycisk **tak**.  
  
 ThrowsNullException projekt zostanie otwarty w nowym wystąpieniu programu Visual Studio, wykonywania zatrzymana w wierszu, która zgłasza wyjątek:  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 Można rozpocząć debugowania na tym etapie. Jeżeli to rzeczywistej aplikacji, należy dowiedzieć się, dlaczego kod wywołującej wyjątek.  
  
## <a name="just-in-time-debugging-errors"></a>Błędy debugowania Just In Time  
 Jeśli nie widzisz okna dialogowego, jeśli program ulegnie awarii, to może z powodu ustawienia raportowania błędów systemu Windows na komputerze. Aby uzyskać więcej informacji, zobacz [. Ustawienia raportowania błędów systemu Windows](/windows-hardware/drivers/dashboard/windows-error-reporting-getting-started).  
  
 Można napotkać następujące komunikaty o błędach, które są skojarzone z Just In Time debugowania.  
  
-   **Nie można dołączyć do procesu, która uległa awarii. Określony program nie jest programem Windows lub MS-DOS.**  
  
     Ten błąd występuje, gdy użytkownik próbuje dołączyć do procesu uruchomionego jako inny użytkownik.  
  
     Aby obejść ten problem, uruchamiania programu Visual Studio Otwórz **dołączyć do procesu** okno dialogowe z **debugowania** menu i Znajdź proces chcesz debugować w **dostępne procesy**listy. Jeśli nie znasz nazwę procesu, obejrzyj **debuger just in Time programu Visual Studio** okno dialogowe i Uwaga identyfikatora procesu. Wybierz proces w ramach **dostępne procesy** listy i kliknij przycisk **Attach**. W **debuger just in Time programu Visual Studio** okna dialogowego, kliknij przycisk **nr** aby odrzucić okno dialogowe.  
  
-   **Nie można uruchomić debugera, ponieważ użytkownik nie jest zalogowany.**  
  
     Ten błąd występuje, gdy Just In Time debugowania próbuje uruchomić program Visual Studio na komputerze, w przypadku, gdy nie ma żadnego użytkownika zalogowany do konsoli. Żaden użytkownik nie jest zalogowany, więc nie istnieje żadna sesja użytkownika do wyświetlenia Just-In-Time debugowania — okno dialogowe.  
  
     Aby rozwiązać ten problem, zaloguj się na tym komputerze.  
  
-   **Klasa nie jest zarejestrowana.**  
  
     Ten błąd wskazuje, że debuger próbował utworzyć klasy modelu COM, który nie jest zarejestrowany, prawdopodobnie z powodu problemu z instalacji.  
  
     Aby rozwiązać ten problem, należy użyć dysku Instalator ponownie zainstalować lub naprawić instalację programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Just-In-Time, debugowanie, opcje — Okno dialogowe](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub nie masz do nich pełnego zaufania, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)