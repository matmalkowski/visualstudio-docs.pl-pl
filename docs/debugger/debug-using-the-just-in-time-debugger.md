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
ms.openlocfilehash: aa31d9d9b536a614cc1000f7c25ae6fbb5e4d510
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176444"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Debugowanie w programie Visual Studio za pomocą debugera just in Time
Debugowanie Just In Time uruchamia Visual Studio automatycznie, gdy wystąpi wyjątek lub awaria wystąpi w aplikacji, która działa poza programem Visual Studio. Dzięki temu można przetestować aplikację, gdy nie jest uruchomiony program Visual Studio i rozpocząć debugowanie w programie Visual Studio, jeśli wystąpi problem.

Debugowanie Just In Time działa w przypadku aplikacji komputerowych Windows. Nie działa dla uniwersalnych aplikacji dla Windows, a nie działa dla kodu zarządzanego, który znajduje się w aplikacji macierzystej, jak na przykład Wizualizatory.

> [!TIP]
> Jeśli chcesz wiedzieć, jak reagować na Just-in-Time okno dialogowe debugera, zobacz [w tym temacie](../debugger/just-in-time-debugging-in-visual-studio.md).

##  <a name="BKMK_Enabling"></a> Włącz lub wyłącz Just-In-Time debugowania
Można włączyć lub wyłączyć debugowanie w programie Visual Studio Just In Time **Narzędzia > Opcje** okno dialogowe.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Aby włączyć lub wyłączyć Just-In-Time debugowanie

1.  Otwórz program Visual Studio z uprawnieniami administratora (kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom jako administrator**).

    Włączanie lub wyłączanie Just-In-Time debugging Ustawia klucz rejestru i może być wymagane uprawnienia administratora, aby zmienić ten klucz.

2. Na **narzędzia** menu, kliknij przycisk **opcje**.

2.  W **opcje** okna dialogowego rozwiń **debugowanie** węzła.

3.  W **debugowanie** węzeł **Just-In-Time**.

    ![Włączanie lub wyłączanie debugowania JIT](../debugger/media/dbg-jit-enable-or-disable.png "włączyć lub wyłączyć debugowanie JIT")

4.  W **włączyć debugowanie just in Time tych rodzajów kodu** zaznacz lub wyczyść typy odpowiednich programów: **zarządzane**, **natywnych**, lub **skryptu**.

5.  Kliknij przycisk **OK**.

Debugowanie Just In Time może być wciąż włączone, nawet jeśli program Visual Studio nie jest już zainstalowane na tym komputerze. Jeśli nie zainstalowano programu Visual Studio, nie można wyłączyć debugowanie w programie Visual Studio Just In Time **opcje** okno dialogowe. W takiej sytuacji można wyłączyć debugowanie, edytując Rejestr Windows Just In Time.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Aby wyłączyć debugowanie, edytując rejestr Just In Time

1.  Na **Start** menu, wyszukaj i uruchom `regedit.exe`

2.  W **Edytora rejestru** okna, zlokalizuj i Usuń następujące wpisy rejestru:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\\. NETFramework\DbgManagedDebugger

    ![Klucz rejestru JIT](../debugger/media/dbg-jit-registry.png "klucza rejestru JIT")

3.  Jeśli komputer działa w 64-bitowym systemie operacyjnym, należy również usunąć następujące wpisy rejestru:

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger

4.  Należy zadbać, aby nie przypadkowo usunąć lub zmienić żadnych kluczy rejestru.

5.  Zamknij **Edytora rejestru** okna.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Aby włączyć Just-In-Time, debugowanie formularza Windows

1.  Domyślnie aplikacje Windows Forms mają program obsługi wyjątków najwyższego poziomu, który umożliwia programowi kontynuowania działania, jeśli możliwe jest odzyskiwanie. Na przykład jeśli aplikacja Windows Forms zwraca nieobsługiwany wyjątek, zobaczysz okno dialogowe podobne do następującego:

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Aby włączyć Just-In-Time debugowanie aplikacji Windows Forms, należy wykonać następujące dodatkowe czynności:

2.  Ustaw `jitDebugging` wartość `true` w `system.windows.form` części pliku machine.config lub  *\<Nazwa aplikacji >*. exe.config pliku:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3.  W aplikacji formularzy Windows w języku C++, należy także ustawić `DebuggableAttribute` w pliku .config lub w kodzie. Jeśli kompilujesz z opcją [/zi](/cpp/build/reference/z7-zi-zi-debug-information-format) i bez [/Og](/cpp/build/reference/og-global-optimizations), kompilator ustawia ten atrybut. Jeśli chcesz debugować kompilację niezoptymalizowanego wydania, jednak należy ustawić to samodzielnie. Można to zrobić, dodając poniższą linię do one pliku AssemblyInfo.cpp aplikacji:

    ```cpp
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.DebuggableAttribute>.

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Użyj debugowania Just In Time
 W tej sekcji przedstawiono, co się stanie, gdy plik wykonywalny zgłasza wyjątek.

 Konieczne jest posiadanie programu Visual Studio wykonaj następujące kroki. Jeśli nie masz programu Visual Studio, możesz pobrać bezpłatną [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).

 Upewnij się, że Just-In-Time debugging jest [włączone](#BKMK_Enabling).

 Na potrzeby tej sekcji wprowadzimy aplikację konsoli C# w programie Visual Studio, które zgłasza [obiektu NullReferenceException](/dotnet/api/system.nullreferenceexception).

 W programie Visual Studio, tworzenie aplikacji konsolowej C# (**Plik > Nowy > Projekt > Visual C# > Aplikacja Konsolowa**) o nazwie **ThrowsNullException**. Aby uzyskać więcej informacji dotyczących tworzeniu projektów w programie Visual Studio, zobacz [wskazówki: Tworzenie prostej aplikacji](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).

 Po otwarciu projektu w programie Visual Studio, otwórz plik Program.cs. Zastąp następujący kod, który wyświetla wiersz do konsoli i następnie zgłasza obiektu NullReferenceException metody Main():

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
>  W kolejności do wykonania tej procedury do pracy w [konfiguracji wydania](../debugger/how-to-set-debug-and-release-configurations.md), należy wyłączyć [tylko mój kod](../debugger/just-my-code.md). W programie Visual Studio, kliknij przycisk **Narzędzia > Opcje**. W **opcje** okno dialogowe, wybierz opcję **debugowanie**. Usuń zaznaczenie z **Włącz tylko mój kod**.

 Skompiluj rozwiązanie (w programie Visual Studio, wybierz **kompilacji > Kompiluj rozwiązanie**). Można wybrać debugowanie lub konfigurację wydania (wybierz **debugowania** do pełnego środowiska debugowania). Aby uzyskać więcej informacji o konfiguracjach kompilacji, zobacz [ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md).

 Proces kompilacji tworzy ThrowsNullException.exe pliku wykonywalnego. Można je znaleźć w folderze, w której utworzono projekt C#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** lub **...\ThrowsNullException\ThrowsNullException\bin\Release**.

 Kliknij dwukrotnie ThrowsNullException.exe. Powinny zostać wyświetlone okno polecenia następująco:

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 Po kilku sekundach zostanie wyświetlone okno błąd:

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 Nie klikaj **anulować**! Po kilku sekundach, powinien zostać wyświetlony dwa przyciski o **debugowania** i **Zamknij program**. Kliknij przycisk **debugowania**.

> [!CAUTION]
>  Jeśli aplikacja zawiera niezaufanego kodu, pojawi się okno dialogowe z ostrzeżeniem o zabezpieczeniach. To okno dialogowe umożliwia podjęcie decyzji, czy chcesz kontynuować debugowanie. Przed kontynuowaniem debugowania, należy zdecydować, czy kodowi można zaufać. Czy napisałeś kod samodzielnie? Czy można ufać koderowi? Jeśli aplikacja jest uruchomiona na komputerze zdalnym, czy rozpoznajesz nazwę procesu? Nawet wtedy, gdy aplikacja jest uruchomiona lokalnie, który nie musi oznaczać, że można jej zaufać. Należy wziąć pod uwagę możliwość złośliwy kod uruchomiony na Twoim komputerze. Jeśli zdecydujesz, że kod masz zamiar debugowania jest godny zaufania, kliknij przycisk **debugowania**. W przeciwnym razie kliknij przycisk **nie Debuguj**.

 **Debuger just in Time programu Visual Studio** zostanie wyświetlone okno:

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 W obszarze **debugery możliwe**, który powinien zostać wyświetlony **nowego wystąpienia programu Microsoft Visual Studio <available version>**  wybrany wiersz. Jeśli go nie jest wybrana, wybierz ją.

 W dolnej części okna w obszarze **chcesz debugować za pomocą wybranego debugera?**, kliknij przycisk **tak**.

 Projekt ThrowsNullException zostanie otwarty w nowym wystąpieniu programu Visual Studio z wykonywaniem zatrzymana w wierszu, który zgłasza wyjątek:

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 Można rozpocząć debugowania na tym etapie. Gdyby to rzeczywistej aplikacji, należy dowiedzieć się, dlaczego kod zgłasza wyjątek.

## <a name="just-in-time-debugging-errors"></a>Błędy debugowania Just In Time
 Jeśli nie widzisz okna dialogowego, gdy program ulegnie awarii, może być to ze względu na ustawienia raportowania błędów Windows na komputerze. Aby uzyskać więcej informacji, zobacz [. Ustawienia raportowania błędów systemu Windows](/windows-hardware/drivers/dashboard/windows-error-reporting-getting-started).

 Można napotkać następujące komunikaty o błędach, które są skojarzone z Just-In-Time debugowania.

-   **Nie można dołączyć do procesu powodującego awarię. Określony program nie jest programem Windows ani MS-DOS.**

     Ten błąd występuje, gdy użytkownik próbuje dołączyć do procesu uruchomionego jako inny użytkownik.

     Aby obejść ten problem, uruchom program Visual Studio, otwórz **dołączyć do procesu** okno dialogowe z **debugowania** menu, a następnie znajdź proces, który chcesz debugować w **dostępne procesy**listy. Jeśli nie znasz nazwy procesu, Przyjrzyj się **debuger just in Time programu Visual Studio** okna dialogowego i zwróć uwagę, identyfikator procesu. Wybierz proces na **dostępne procesy** listy, a następnie kliknij przycisk **Dołącz**. W **debuger just in Time programu Visual Studio** okno dialogowe, kliknij przycisk **nie** aby zamknąć okno dialogowe.

-   **Nie można uruchomić debugera, ponieważ żaden użytkownik nie jest zalogowany.**

     Ten błąd występuje, gdy Just-In-Time debugowania próbuje uruchomić program Visual Studio na maszynie w przypadku, gdy nie ma żadnego użytkownika zalogowany do konsoli. Ponieważ żaden użytkownik nie jest zalogowany, nie istnieje żadna sesja użytkownika, aby wyświetlić Just-In-Time debugging okno dialogowe.

     Aby rozwiązać ten problem, należy zalogować się na komputerze.

-   **Klasa nie jest zarejestrowana.**

     Ten błąd wskazuje, że debuger próbował utworzyć klasę modelu COM, który nie jest zarejestrowana, prawdopodobnie z powodu problemu z instalacją.

     Aby rozwiązać ten problem, należy użyć dysku instalacyjnego ponownie zainstalować lub naprawić instalację programu Visual Studio.

## <a name="see-also"></a>Zobacz też
 [Zabezpieczenia debugera](../debugger/debugger-security.md) [podstawy debugera](../debugger/getting-started-with-the-debugger.md) [Just-In-Time, debugowanie, okno dialogowe Opcje](../debugger/just-in-time-debugging-options-dialog-box.md) [ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub nie masz do nich pełnego zaufania, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
