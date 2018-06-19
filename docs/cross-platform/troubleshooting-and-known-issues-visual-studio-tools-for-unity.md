---
title: Rozwiązywanie problemów i znane problemy (Visual Studio Tools dla Unity) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/10/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: cb1da2ec2c41fcbec78864868d116bcd1684a5b2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31562016"
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

### <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Problemy z programu Visual Studio 2015 i IntelliSense lub kod zabarwienie.
Należy próbować uaktualniania programu Visual Studio 2015 do aktualizacji 3.

### <a name="shader-files-without-code-coloration-when-using-visual-studio-2017"></a>Pliki programu do cieniowania bez zabarwienie kodu, korzystając z programu Visual Studio 2017 r.
Upewnij się, że obciążenie "Pulpitu programowanie z C++" jest zainstalowany w programie Visual Studio 2017 r. C/C++ analizator używany dla kodu zabarwienie jest powiązane z tym obciążenia.

### <a name="visual-studio-hangs"></a>Visual Studio zawiesza się.
Kilka wtyczek Unity, takich jak analizy, fmod —, STUDZIENKĘ (Universal odtwarzacz), ZFBrowser lub osadzonej przeglądarce są przy użyciu macierzystych wątków. Jest problem, gdy dodatek kończy się dołączanie Wątek macierzysty do środowiska wykonawczego, która następnie blokowania wywołań do systemu operacyjnego. Oznacza to, Unity nie można przerwać wątek dla debugera (lub Załaduj ponownie domeny) i zawieszenie.

Fmod —, istnieje obejście tego problemu, można przekazać inicjowania FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE [flagi](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) wyłączyć przetwarzanie asynchroniczne i wykonywać przetwarzania w głównym wątku.

### <a name="incompatible-project-in-visual-studio"></a>Niezgodne projektu programu Visual Studio
Najpierw upewnij się, że program Visual Studio jest ustawiony jako edytora skryptu zewnętrznego w Unity (Edycja/preferencje/zewnętrznych narzędzi). Sprawdź, czy dodatek Visual Studio jest zainstalowany w Unity (Pomoc/informacje musi zawierać wiadomości, takich jak Microsoft Visual Studio Tools for Unity jest włączona na dole). Następnie sprawdź, czy rozszerzenie jest poprawnie zainstalowany w programie Visual Studio (Pomoc/informacje).

### <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Dodatkowe przeładowania lub Visual Studio utraty wszystkie otwarte okna
Pamiętaj nigdy nie touch pliki projektu bezpośrednio z zasobów procesora lub innego narzędzia. Jeśli naprawdę musisz modyfikowania pliku projektu, uwidaczniamy interfejsu API w tym. Sprawdź, czy [odwołań do zestawów w sekcji problemy](#Assembly-reference-issues).

Jeśli wystąpią dodatkowe przeładowania lub utracie Visual Studio wszystkie otwarte okna na Załaduj ponownie, upewnij się, że masz właściwe .NET przeznaczonych dla pakietów zainstalowanych. Sprawdź, czy w poniższej sekcji o struktur, aby uzyskać więcej informacji.

###  <a name="the-debugger-does-not-break-on-exceptions"></a>Debuger nie dzielone na wyjątki
Przy użyciu starszej wersji środowiska uruchomieniowego Unity (odpowiednik .NET 3.5), debuger będzie zawsze Przerwij, gdy jest nieobsługiwany wyjątek (= spoza bloku try/catch). Jeśli wyjątek jest obsługiwany, debuger użyje okno Ustawienia wyjątków można określić, czy podziału jest wymagane, czy nie.

Nowe środowisko uruchomieniowe (.NET 4.6 odpowiednik) Unity wprowadzono nowy sposób zarządzania wyjątków użytkownika i w związku z tym wszystkie wyjątki są widoczne jako "obsługiwane przez użytkownika", nawet jeśli znajdują się poza blokiem try/catch. Dlatego trzeba jawnie zaznacz je w oknie Ustawienia wyjątków debugera do dzielenia.

W oknie Ustawienia wyjątków (debugowanie > Windows > Ustawienia wyjątków), rozwiń węzeł kategorii wyjątków (na przykład wspólnego języka środowiska uruchomieniowego wyjątków oznacza wyjątki .NET) i zaznacz pole wyboru dla specyficznego wyjątku, aby CATCH w ramach tej kategorii (na przykład System.NullReferenceException). Można również wybrać cały kategorię wyjątków.

### <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>W systemie Windows programu Visual Studio zapyta, można pobrać platformę docelową Unity
Visual Studio Tools for Unity wymaga programu .NET framework 3.5, który nie jest instalowany domyślnie w systemie Windows 8 lub Windows 10. Aby rozwiązać ten problem, postępuj zgodnie z instrukcjami, aby pobrać i zainstalować program .NET framework 3.5.

Korzystając z nowego środowiska uruchomieniowego Unity, .NET określania wartości docelowej pakiety w wersji 4.6 i 4.7.1 są również wymagane. Istnieje możliwość używania Instalatora VS2017 szybko zainstalować je (modyfikowanie użytkownika VS2017 instalacji, pojedynczych składników, kategorii .NET, wybierz wszystkie 4.x przeznaczonych dla pakietów).

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

Wi-Fi jest uniwersalny, lecz bardzo wolno w porównaniu z USB z powodu opóźnień. Widzieliśmy Brak prawidłowego obsługę multiemisji dla niektórych routerów lub urządzenia (są dobrze znanych dla tej serii węzła).

USB jest nadrzędne szybkie do debugowania i Visual Studio Tools for Unity teraz jest w stanie wykryć urządzenia USB i zwróć się do serwera adb właściwe przekazywanie portów do debugowania.

### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrowanie z UnityVS do narzędzi Visual Studio Tools for Unity
 W przypadku migrowania z UnityVS do programu Visual Studio Tools for Unity, należy wygenerować nowy rozwiązań programu Visual Studio dla projektów Unity.

##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Do migracji projektu Unity z UnityVS 1.8 do programu Visual Studio Tools dla Unity 1.9

1.  Usuń stare pliki rozwiązań i projektów z projektu platformy Unity. W katalogu głównym projektu Unity Znajdź SLN programu Visual Studio i. * proj pliki i usunąć je wszystkie.

2.  Zaimportuj programu Visual Studio Tools dla pakietu Unity do projektu platformy Unity. Aby uzyskać informacje o tym, jak zaimportować pakiet pomocą rozszerzenia VSTU, zobacz Konfigurowanie narzędzi Visual Studio Tools for Unity na [wprowadzenie](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) strony.

3.  Generuj nowe pliki rozwiązań i projektów. Jeśli chcesz wygenerować je teraz, w edytorze Unity w menu głównym wybierz **programu Visual Studio Tools**, **wygenerować plików projektu**. W przeciwnym razie pomiń ten krok, jeśli chcesz; Visual Studio Tools for Unity wygeneruje nowe pliki automatycznie po wybraniu **programu Visual Studio Tools**, **Otwórz w programie Visual Studio**.

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
