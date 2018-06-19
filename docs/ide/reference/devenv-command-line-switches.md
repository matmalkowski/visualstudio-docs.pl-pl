---
title: Przełączniki wiersza polecenia devenv programu Visual Studio
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b6cf3bf422c861d5a649e5cfa71cf2b4a4b5fea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31951118"
---
# <a name="devenv-command-line-switches"></a>Przełączniki wiersza polecenia Devenv

Devenv pozwala ustawić różne opcje zintegrowane środowisko programistyczne (IDE), a także tworzenia, debugowania i wdrażania projektów z wiersza polecenia. Użyj tych przełączników, uruchamianie skryptu lub pliku .bat, na przykład skryptu kompilacji co noc, IDE, czy też chcesz rozpocząć IDE w określonej konfiguracji.

> [!NOTE]
> Do wykonywania zadań związanych z kompilacją zalecane jest, użyj programu MSBuild, zamiast devenv. Aby uzyskać więcej informacji, zobacz [wiersza polecenia programu MSBuild](../../msbuild/msbuild-command-line-reference.md).

## <a name="devenv-switch-syntax"></a>Składnia przełącznik Devenv

Domyślnie polecenia devenv przekazać przełączników do narzędzia devenv.com. Narzędzie devenv.com dostarcza danych wyjściowych za pomocą strumieni w standardowym systemie, takich jak `stdout` i `stderr`. Po zarejestrowaniu wyniki, na przykład w pliku txt tego narzędzia można określić odpowiedniej przekierowania we/wy.

Z drugiej strony, polecenia zaczynające się od `devenv.exe` można używać tego samego przełączników, ale narzędzie devenv.com jest pomijane.

Zasady składni `devenv` przełączniki podobne jak w przypadku innych narzędzi wiersza polecenia systemu DOS. Następujące reguły składni dotyczą wszystkich `devenv` przełączników i ich argumentów:

- Polecenia zaczyna się od `devenv`.

- Przełączniki nie jest rozróżniana.

- Podczas określania rozwiązania lub projektu, pierwszy argument jest nazwą pliku rozwiązania lub pliku projektu, w tym ścieżki pliku.

- Pierwszy argument w przypadku plików, który nie jest rozwiązania lub projektu, ten plik zostanie otwarty w odpowiedniego edytora w nowym wystąpieniu IDE.

- Jeśli podasz nazwę pliku projektu, a nie nazwę pliku rozwiązania `devenv` polecenie wyszukuje folderu nadrzędnego dla pliku rozwiązania, który ma taką samą nazwę pliku projektu. Na przykład polecenie `devenv /build myproject1.vbproj` wyszukuje folderu nadrzędnego dla pliku rozwiązania o nazwie "myproject1.sln".

    > [!NOTE]
    > Jeden i tylko jeden plik rozwiązania, który odwołuje się do tego projektu powinien znajdować się w jego folderu nadrzędnego. Jeśli folder nadrzędny nie zawiera rozwiązań pliku odwołujący się tego projektu, lub jeśli folder nadrzędny zawiera dwa lub więcej plików rozwiązania, które odwołania, tymczasowego pliku rozwiązania jest tworzony.

- Gdy nazwy pliku i ścieżki plików spacji, możesz należy ująć w cudzysłów (""). Na przykład "c:\project\\".

- Wstaw jednego znaku spacji między przełączników i argumenty w tym samym wierszu. Na przykład polecenie **devenv/log output.txt** otwiera IDE i wyświetla wszystkie dziennika do output.txt informacje dla tej sesji.

- Nie można użyć składni wieloznacznej w `devenv` poleceń.

## <a name="devenv-switches"></a>Przełączniki Devenv

Następujące przełączniki wiersza polecenia Wyświetl IDE i wykonać zadania opisane.

|Przełącznik wiersza polecenia|Opis|
|-------------------------|-----------------|
|[/ Polecenia](../../ide/reference/command-devenv-exe.md)|Uruchamia IDE i wykonuje określone polecenie.|
|[/ DebugExe](../../ide/reference/debugexe-devenv-exe.md)|Ładuje plik wykonywalny C++ pod kontrolą debugera. Ten parametr nie jest dostępny dla plików wykonywalnych języka Visual Basic lub C#. Aby uzyskać więcej informacji, zobacz [automatyczne uruchamianie procesu w debugerze](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|
|[/ LCID lub/l](../../ide/reference/lcid-devenv-exe.md)|Określa domyślny język dla IDE. Jeśli określony język nie jest uwzględniony w instalacji programu Visual Studio, to ustawienie jest ignorowane.|
|[Zaloguj](../../ide/reference/log-devenv-exe.md)|Powoduje uruchomienie programu Visual Studio i rejestruje wszystkie działania w pliku dziennika.|
|[/ Run lub /r](../../ide/reference/run-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie.|
|[/ Runexit](../../ide/reference/runexit-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie, minimalizuje IDE, gdy rozwiązanie jest uruchamiany i zamyka IDE po rozwiązaniu zakończył działanie.|
|[/ UseEnv](../../ide/reference/useenv-devenv-exe.md)|Powoduje, że IDE używać zmiennych środowiskowych PATH, INCLUDE i LIB dla kompilacji C++, a nie ustawienia określone w sekcji katalogi VC ++ **projekty** opcje w **opcje** okno dialogowe. Ten przełącznik jest instalowany z **tworzenia klasycznych aplikacji w języku C++** obciążenia. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|
|[/ Edit](../../ide/reference/edit-devenv-exe.md)|Otwiera określone pliki w działającej instancji tej aplikacji. Jeśli nie Brak uruchomionych wystąpień, uruchamia nowe wystąpienie z układem uproszczony okna.|
|[/ SafeMode](../../ide/reference/safemode-devenv-exe.md)|Visual Studio jest uruchamiany w trybie awaryjnym, ładuje tylko z domyślnego środowiska i usługami i wysłane wersje pakietów innych producentów.|
|[/ ResetSkipPkgs](../../ide/reference/resetskippkgs-devenv-exe.md)|Czyści wszystkie tagi SkipLoading dodane do VSPackages przez użytkowników, którzy chcą uniknąć obciążania problem VSPackages.|
|[/ Instalacji](../../ide/reference/setup-devenv-exe.md)|Wymusza Visual Studio, aby scalić metadanych zasobów, które opisują menu, paski narzędzi i grupy poleceń, z VSPackages wszystkie dostępne. To polecenie musi uruchomić jako administrator.|

Następujące przełączniki wiersza polecenia nie są wyświetlane IDE.

|Przełącznik wiersza polecenia|Opis|
|-------------------------|-----------------|
|[/?](../../ide/reference/q-devenv-exe.md)|Wyświetla Pomoc dla przełączników devenv w **okno wiersza polecenia**.<br /><br /> **Devenv /?**|
|[/ Kompilacji](../../ide/reference/build-devenv-exe.md)|Tworzy określonego rozwiązania lub projektu, zgodnie z konfiguracją określonego rozwiązania.<br /><br /> **/ Build myproj.csproj Devenv**|
|[/ Clean](../../ide/reference/clean-devenv-exe.md)|Usuwa wszystkie pliki utworzone za pomocą polecenia kompilacji bez wpływu na pliki źródłowe.<br /><br /> **Devenv myproj.csproj / clean**|
|[/ Wdrożenia](../../ide/reference/deploy-devenv-exe.md)|Tworzy rozwiązania, oraz pliki niezbędne do wdrożenia, zgodnie z konfiguracją rozwiązania.<br /><br /> **Devenv myproj.csproj / deploy**|
|[/ Diff](../../ide/reference/diff.md)|Porównuje dwa pliki. Przyjmuje cztery parametry: SourceFile, TargetFile, SourceDisplayName (opcjonalny), TargetDisplayName (opcjonalnie).|
|[/ Out](../../ide/reference/out-devenv-exe.md)|Pozwala określić plik błędy podczas kompilowania.<br /><br /> **/ Build myproj.csproj Devenv/out log.txt**|
|[/ Projektu](../../ide/reference/project-devenv-exe.md)|Projekt do kompilacji, czyszczenia lub wdrożenia. Ten przełącznik może zostać użyty tylko wtedy, gdy należy dostarczyć także/Build, / rebuild, / clean, lub / deploy — przełącznik.|
|[/ ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)|Określa konfigurację projektu do kompilacji lub wdrożenia. Ten przełącznik może zostać użyty tylko wtedy, gdy należy dostarczyć także przełącznika/Project.|
|[/ Rebuild](../../ide/reference/rebuild-devenv-exe.md)|Czyści a potem kompiluje określonego rozwiązania lub projektu, zgodnie z konfiguracją określonego rozwiązania.|
|[/ ResetSettings](../../ide/reference/resetsettings-devenv-exe.md)|Przywraca ustawienia domyślne programu Visual Studio. Opcjonalnie resetuje ustawienia do pliku określonego .vssettings.|
|[/ Upgrade](../../ide/reference/upgrade-devenv-exe.md)|Uaktualnia plik określonego rozwiązania i wszystkie jego pliki projektu lub plik określony projekt do bieżącego formatu Visual Studio tych plików.|

## <a name="see-also"></a>Zobacz także

* [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)