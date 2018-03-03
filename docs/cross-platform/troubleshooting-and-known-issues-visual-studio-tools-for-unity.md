---
title: "Rozwiązywanie problemów i znane problemy (Visual Studio Tools dla Unity) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-unity-tools
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 95d1724561886e1bcfa9a870bdf3bdadb787f9e8
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2018
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Rozwiązywanie problemów i znane problemy (Visual Studio Tools dla Unity)
W tej sekcji możesz znaleźć rozwiązania typowych problemów z programu Visual Studio Tools for Unity, opisy znanych problemów i Dowiedz się, jak można zwiększyć Visual Studio Tools for Unity raportowanie błędów.

## <a name="troubleshooting"></a>Rozwiązywanie problemów
Do rozwiązywania niektórych typowych problemów z programu Visual Studio Tools for Unity, zobacz następujące sekcje.

### <a name="visual-studio-crashes"></a>Visual Studio ulega awarii
Może to być spowodowane pamięć podręczna MEF usługi Visual Studio jest uszkodzony.

Należy usunąć następujący folder, aby zresetować pamięć podręczna MEF (Zamknij Visual Studio przed wykonaniem tego):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

To powinno rozwiązać problem. W przypadku, gdy problem nadal występuje, uruchom wiersz polecenia dewelopera dla programu Visual Studio jako Administrator i użyj następującego polecenia:

```batch
 devenv /setup
```

### <a name="issues-with-vs2015-and-intellisense-or-code-coloration"></a>Problemy z zabarwienie VS2015 i IntelliSense lub kod.
Należy próbować uaktualniania programu Visual Studio 2015 do aktualizacji 3.

### <a name="visual-studio-hangs"></a>Visual Studio zawiesza się.
Kilka wtyczek Unity, takich jak analizy, fmod —, STUDZIENKĘ (Universal odtwarzacz), ZFBrowser lub osadzonej przeglądarce są przy użyciu macierzystych wątków. Jest problem, gdy dodatek kończy się dołączanie Wątek macierzysty do środowiska wykonawczego, która następnie blokowania wywołań do systemu operacyjnego. Oznacza to, Unity nie można przerwać wątek dla debugera (lub Załaduj ponownie domeny) i zawieszenie.

Fmod —, istnieje obejście tego problemu, można przekazać inicjowania FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE [flagi](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) wyłączyć przetwarzanie asynchroniczne i wykonywać przetwarzania w głównym wątku.

### <a name="incompatible-project-in-visual-studio"></a>Niezgodne projektu programu Visual Studio
Najpierw upewnij się, że program Visual Studio jest ustawiony jako edytora skryptu zewnętrznego w Unity (Edycja/preferencje/zewnętrznych narzędzi). Sprawdź, czy dodatek Visual Studio jest zainstalowany w Unity (Pomoc/informacje musi zawierać wiadomości, takich jak Microsoft Visual Studio Tools for Unity jest włączona na dole). Następnie sprawdź, czy rozszerzenie jest poprawnie zainstalowany w programie Visual Studio (Pomoc/informacje).

### <a name="assembly-reference-issues"></a>Problemy z odwołania zestawu
Jeśli Twój projekt jest złożone reference-wise lub jeśli chcesz to lepiej kontrolować ten krok generowania, możesz użyć naszych [interfejsu API](../cross-platform/customize-project-files-created-by-vstu.md) do manipulowania wygenerowana zawartość projekt lub rozwiązanie. Można również użyć [pliki odpowiedzi](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) w Twojej Unity projektu i firma Microsoft będzie przetwarzać je.

### <a name="breakpoints-with-a-warning"></a>Punkty przerwania z ostrzeżeniem
Jeśli program Visual Studio nie może znaleźć lokalizację źródła dla określonego punktu przerwania zostanie wyświetlone ostrzeżenie wokół punkt przerwania. Sprawdź, czy zachowanie, którego używasz poprawnie załadowany/używane w bieżącym sceny Unity.

### <a name="breakpoints-not-hit"></a>Punkty przerwania nie trafień.
 Sprawdź, czy zachowanie, którego używasz poprawnie załadowany/używane w bieżącym sceny Unity. Zamknij Unity i Visual Studio, a następnie usunięcie wszystkich wygenerowanych plików (*.csproj, *.sln) i cały folder biblioteki.

### <a name="unable-to-attach"></a>Nie można dołączyć
-   Spróbuj tymczasowo wyłączyć programu antywirusowego lub tworzyć reguły wykluczania dla wersji programu VS i Unity.
-   Spróbuj tymczasowo wyłączyć zapory lub utworzyć zasady umożliwiające TCP/UDP siecią między VS i Unity.
-   Określiliśmy programów, takich jak Podgląd zespołu zakłócają proces wykrywania; możliwe, że możesz zatrzymać tymczasowo wszelkie dodatkowe oprogramowanie, aby sprawdzić, czy zmieni coś.
-   Nie zmieniaj nazw głównego pliku wykonywalnego Unity pomocą rozszerzenia VSTU jest tylko monitorowanie procesów "Unity.exe".

### <a name="unable-to-debug-android-players"></a>Nie można debugować odtwarzacze systemu Android
Używamy multiemisji wykrywania player, (która jest używana przez Unity domyślnego mechanizmu), ale po używamy regularne połączenia TCP, można dołączyć debugera. Faza wykrywania jest głównym problemem w przypadku urządzeń z systemem Android.

USB jest nadrzędne szybkiego do debugowania, ale nie jest zgodne z mechanizmu odnajdywania player Unity.
Wi-Fi jest bardziej elastyczne, ale bardzo wolno w porównaniu do USB z powodu opóźnień. Widzieliśmy Brak prawidłowego obsługę multiemisji dla niektórych routerów lub urządzenia (są dobrze znanych dla tej serii węzła).

Można spróbować następującej przy użyciu USB, aby zobaczyć otwartych portów na urządzeniu podłączonym (z player w górę i uruchomione, tak aby były widoczne portem debugowania, zawsze w formie 56xxx):

```shell
adb shell netstat
```

Przekazuj port na komputerze lokalnym:

```shell
adb forward tcp:56xxx tcp:56xxx
```

Następnie należy połączyć pomocą rozszerzenia VSTU przy użyciu 127.0.0.1:56xxx przekazywane portu.

### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrowanie z UnityVS do narzędzi Visual Studio Tools for Unity
 W przypadku migrowania z UnityVS do programu Visual Studio Tools for Unity, należy wygenerować nowy rozwiązań programu Visual Studio dla projektów Unity.

##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Do migracji projektu Unity z UnityVS 1.8 do programu Visual Studio Tools dla Unity 1.9

1.  Usuń stare pliki rozwiązań i projektów z projektu platformy Unity. W katalogu głównym projektu Unity Znajdź SLN programu Visual Studio i. * proj pliki i usunąć je wszystkie.

2.  Zaimportuj programu Visual Studio Tools dla pakietu Unity do projektu platformy Unity. Aby uzyskać informacje o tym, jak zaimportować pakiet pomocą rozszerzenia VSTU, zobacz Konfigurowanie narzędzi Visual Studio Tools for Unity na [wprowadzenie](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) strony.

3.  Generuj nowe pliki rozwiązań i projektów. Jeśli chcesz wygenerować je teraz, w edytorze Unity w menu głównym wybierz **programu Visual Studio Tools**, **wygenerować plików projektu**. W przeciwnym razie pomiń ten krok, jeśli chcesz; Visual Studio Tools for Unity wygeneruje nowe pliki automatycznie po wybraniu **programu Visual Studio Tools**, **Otwórz w programie Visual Studio**.

### <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>W systemie Windows programu Visual Studio zapyta, można pobrać platformę docelową Unity
 Visual Studio Tools for Unity wymaga programu .net framework 3.5, który nie jest instalowany domyślnie w systemie Windows 8 lub Windows 10. Aby rozwiązać ten problem, postępuj zgodnie z instrukcjami, aby pobrać i zainstalować program .net framework 3.5.

## <a name="known-issues"></a>Znane problemy
 Istnieją znane problemy w programie Visual Studio Tools for Unity wynikających z współdziałania debugera z Unity w starszej wersji kompilatora C#. Pracujemy nad pomóc w rozwiązaniu tych problemów, ale w tym czasie mogą wystąpić następujące problemy:

-   Podczas debugowania, Unity czasami ulega awarii.

-   Podczas debugowania, Unity czasami zawiesza się.

-   Wykonywanie krok po kroku do i z metody czasami działa nieprawidłowo, szczególnie w Iteratory lub w instrukcjach przełącznika.

## <a name="reporting-errors"></a>Raportowanie błędów
 Pomóż nam w ulepszaniu jakości programu Visual Studio Tools for Unity wysyłanie raportów o błędach w przypadku wystąpienia awarii, zawiesza lub inne błędy. Ułatwia to nam badanie i rozwiązywanie problemów w Visual Studio Tools for Unity. Dziękuję!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak może zgłosić błąd, gdy program Visual Studio zawiesza się
 Brak raportów, które Visual Studio zawiesza się czasami, gdy debugowanie za pomocą narzędzi Visual Studio Tools for Unity, ale potrzebujemy więcej danych, aby zrozumieć ten problem. Możesz pomóc nam zbadać, wykonując poniższe kroki.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Aby zgłosić, że program Visual Studio zawiesza się podczas debugowania za pomocą narzędzi Visual Studio Tools for Unity

*W systemie Windows:*

1.  Otwórz nowe wystąpienie programu Visual Studio.

2.  Otwórz dołączanie do procesu okna dialogowego. W nowym wystąpieniu programu Visual Studio, w menu głównym wybierz **debugowania**, **dołączyć do procesu**.

3.  Dołącz debuger do zablokowanej wystąpienie programu Visual Studio. W **dołączyć do procesu** okno dialogowe, wybierz zablokowane wystąpienie programu Visual Studio z **dostępne procesy** tabeli, a następnie wybierz pozycję **Attach** przycisku.

4.  Wstrzymaj debugera. W nowym wystąpieniu programu Visual Studio, w menu głównym wybierz **debugowania**, **Przerwij wszystkie**, lub od razu naciśnij **Ctrl + Alt + Break**.

5.  Tworzenie zrzutu wątku. W oknie wiersza polecenia, wpisz następujące polecenie i naciśnij klawisz **Enter**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Konieczne może być **polecenia** okna pierwszy widoczny. W programie Visual Studio, w menu głównym wybierz **widoku**, **inne okna**, **okno polecenia**.

*Dla komputerów Mac:*

1. Otwórz terminal i Pobierz identyfikator PID procesu programu Visual Studio dla komputerów Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Uruchom debuger lldb:

    ```shell
    lldb
    ```

1. Dołącz do programu Visual Studio for Mac wystąpienia przy użyciu identyfikatora PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Pobrać ślad stosu dla wszystkich wątków:

    ```shell
    bt all
    ```

Na koniec wysyłania zrzutu wątku do [ vstusp@microsoft.com ](mailto:vstusp@microsoft.com), wraz z opisem czynności wykonywanych w przypadku programu Visual Studio uległa zablokowane.
