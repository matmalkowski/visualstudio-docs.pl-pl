---
title: "Przełączniki wiersza polecenia Devenv | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- switches, Devenv
- builds [Team System], command-line
- applications [Visual Studio], executing
- compiling source code, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
- environment, Devenv commands
- compilers, Devenv commands
- switches
- Devenv, syntax and list of switches
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f06722f4a6192323d92ce6828b25bc57666de8bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="devenv-command-line-switches"></a>Przełączniki wiersza polecenia Devenv
Devenv pozwala ustawić różne opcje zintegrowane środowisko programistyczne (IDE) i również tworzenia, debugowania i wdrażania projektów z wiersza polecenia. Użyj tych przełączników, do uruchomienia skryptu lub pliku .bat, na przykład skryptu kompilacji co noc, IDE, czy też chcesz rozpocząć IDE w określonej konfiguracji.  
  
> [!NOTE]
>  Teraz zadania związane z kompilacji, zaleca, użyj programu MSBuild, zamiast devenv. Aby uzyskać więcej informacji, zobacz [dotyczące wiersza polecenia](../../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Devenv musi działać jako administrator, aby można było używać [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) i [/installvstemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) przełączników.  
  
## <a name="devenv-switch-syntax"></a>Składnia — przełącznik Devenv  
 Domyślnie polecenia devenv przekazać przełączników do narzędzia devenv.com.  
  
 Udostępnia w celu dostarczania danych wyjściowych za pośrednictwem strumieni standardowych systemowych, takich jak narzędzie devenv.com `stdout` i `stderr`i określa odpowiedniej przekierowania we/wy, gdy na przykład zarejestrowaniu dane wyjściowe do pliku txt. Polecenia, zamiast tego zaczynające się `devenv.exe` można używać tego samego przełączników, ale będzie wysyłać je do programu devenv.exe, pomijanie narzędzie devenv.com.  
  
 Zasady składni `devenv` przełączniki podobne jak w przypadku innych narzędzi wiersza polecenia systemu DOS. Następujące reguły składni dotyczą wszystkich `devenv` przełączników i ich argumentów:  
  
-   Polecenia zaczyna się od `devenv`.  
  
-   Przełączniki nie jest rozróżniana.  
  
-   Podczas określania rozwiązania lub projektu, pierwszy argument jest nazwą pliku rozwiązania lub pliku projektu, w tym ścieżki pliku.  
  
-   Pierwszy argument w przypadku plików, który nie jest rozwiązania lub projektu, ten plik zostanie otwarty w edytorze odpowiednie w nowym wystąpieniu IDE.  
  
-   Jeśli podasz nazwę pliku projektu, a nie nazwę pliku rozwiązania `devenv` polecenia przeszuka folderu nadrzędnego dla pliku rozwiązania, który ma taką samą nazwę pliku projektu. Na przykład polecenie `devenv /build myproject1.vbproj` przeszuka folderu nadrzędnego dla pliku rozwiązania o nazwie "myproject1.sln".  
  
    > [!NOTE]
    >  Jeden i tylko jeden plik rozwiązania, który odwołuje się do tego projektu powinien znajdować się w jego folderu nadrzędnego. Jeśli folder nadrzędny nie zawiera rozwiązań pliku odwołujących się do tego projektu, lub jeśli folder nadrzędny zawiera dwa lub więcej plików rozwiązania, które odwołania, następnie tymczasowego pliku rozwiązania zostaną utworzone który nosi nazwę dla tego projektu i odwołuje się on.  
  
-   Gdy nazwy pliku i ścieżki plików spacji, możesz należy ująć w podwójny cudzysłów (""). Na przykład "c:\project\\".  
  
-   Wstaw jednego znaku spacji między przełączników i argumenty w tym samym wierszu. Na przykład polecenie **devenv/log output.txt** otwiera IDE i wyświetla wszystkie dziennika do output.txt informacje dla tej sesji.  
  
-   Nie można użyć składni wieloznacznej w `devenv` poleceń.  
  
## <a name="devenv-switches"></a>Przełączniki Devenv  
 Użyj następujących przełączników wiersza polecenia do wyświetlania IDE i wykonać zadania opisane.  
  
|Przełącznik wiersza polecenia|Opis|  
|-------------------------|-----------------|  
|[/ Command (devenv.exe)](../../ide/reference/command-devenv-exe.md)|Uruchamia IDE i wykonuje określone polecenie.|  
|[/ DebugExe (devenv.exe)](../../ide/reference/debugexe-devenv-exe.md)|Ładunki [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] wykonywalnego pod kontrolą debugera. Ta opcja nie jest dostępna dla [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] plików wykonywalnych. Aby uzyskać więcej informacji, zobacz [automatyczne uruchamianie procesu w debugerze](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|  
|[/ LCID (devenv.exe)](../../ide/reference/lcid-devenv-exe.md) lub`/l`|Określa domyślny język dla IDE. Jeśli określony język nie jest uwzględniony w instalacji programu Visual Studio, to ustawienie zostanie zignorowane.|  
|[/ Log (devenv.exe)](../../ide/reference/log-devenv-exe.md)|Uruchamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i rejestruje wszystkie działania w pliku dziennika.|  
|[/ Uruchom (devenv.exe)](../../ide/reference/run-devenv-exe.md) lub`/r`|Kompiluje i uruchamia określone rozwiązanie.|  
|[/ Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)|Kompiluje i uruchamia określone rozwiązanie, minimalizuje IDE, gdy rozwiązanie jest uruchamiany i zamyka IDE po rozwiązaniu zakończył działanie.|  
|[/ UseEnv (devenv.exe)](../../ide/reference/useenv-devenv-exe.md)|Powoduje, że IDE używać zmiennych środowiskowych PATH, INCLUDE i LIB dla [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kompilacji zamiast ustawień określonych w sekcji katalogi VC ++ **projekty** opcje w **opcje** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds)|  
|[/ Edit (devenv.exe)](../../ide/reference/edit-devenv-exe.md)|Otwiera określone pliki w działającej instancji tej aplikacji. Jeśli nie Brak uruchomionych wystąpień, zostanie ona rozpoczęta nowe wystąpienie z układem uproszczony okna.|  
|[/ ResetAddin (devenv.exe)](../../ide/reference/resetaddin-devenv-exe.md)|Uruchamia wystąpienie programu Visual Studio IDE bez ładowania określonego dodatku.|  
|[/ SafeMode (devenv.exe)](../../ide/reference/safemode-devenv-exe.md)|Uruchamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym ładuje tylko z domyślnego środowiska i usługami i wysłane wersje pakietów innych producentów.|  
|[/ ResetSkipPkgs (devenv.exe)](../../ide/reference/resetskippkgs-devenv-exe.md)|Czyści wszystkie tagi SkipLoading dodane do VSPackages przez użytkowników, którzy chcą uniknąć obciążania problem VSPackages.|  
|[/ Instalacji (devenv.exe)](../../ide/reference/setup-devenv-exe.md)|Wymusza Visual Studio, aby scalić metadanych zasobów, które opisują menu, paski narzędzi i grupy poleceń, z VSPackages wszystkie dostępne.|  
  
 Umożliwia wykonanie zadania opisane następujące przełączniki wiersza polecenia. Te przełączniki wiersza polecenia nie są wyświetlane IDE.  
  
|Przełącznik wiersza polecenia|Opis|  
|-------------------------|-----------------|  
|[/? (devenv.exe)](../../ide/reference/q-devenv-exe.md)|Wyświetla Pomoc dla przełączników devenv w **okno wiersza polecenia**.<br /><br /> **Devenv /?**|  
|[/ Kompilacji (devenv.exe)](../../ide/reference/build-devenv-exe.md)|Tworzy określonego rozwiązania lub projektu, zgodnie z konfiguracją określonego rozwiązania.<br /><br /> **/ Build myproj.csproj Devenv**|  
|[/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)|Usuwa wszystkie pliki utworzone za pomocą polecenia kompilacji bez wpływu na pliki źródłowe.<br /><br /> **Devenv myproj.csproj / clean**|  
|[/ Wdróż (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)|Tworzy rozwiązania, oraz pliki niezbędne do wdrożenia, zgodnie z konfiguracją rozwiązania.<br /><br /> **Devenv myproj.csproj / deploy**|  
|[/ Diff](../../ide/reference/diff.md)|Porównuje dwa pliki.  Przyjmuje cztery parametry: SourceFile, TargetFile, SourceDisplayName(optional),TargetDisplayName(optional).|  
|[/ InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md)|Rejestruje szablony projektów lub elementów, które znajdują się w  *\<VisualStudioInstallDir >*\Common7\IDE\ProjectTemplates lub  *\<VisualStudioInstallDir >*\Common7 \IDE\ItemTemplates, dzięki czemu są one dostępne za pośrednictwem **nowy projekt** i **Dodaj nowy element** okien dialogowych.<br /><br /> **/ Installvstemplates Devenv**|  
|[/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)|Pozwala określić plik błędy podczas kompilowania.<br /><br /> **/ Build myproj.csproj Devenv/out log.txt**|  
|[/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)|Projekt do kompilacji, czyszczenia lub wdrożenia. Ten przełącznik może zostać użyty tylko wtedy, gdy należy dostarczyć także/Build, / rebuild, / clean, lub / deploy — przełącznik.|  
|[/ ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)|Określa konfigurację projektu do kompilacji lub wdrożenia. Ten przełącznik może zostać użyty tylko wtedy, gdy należy dostarczyć także przełącznika/Project.|  
|[/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)|Czyści a potem kompiluje określonego rozwiązania lub projektu, zgodnie z konfiguracją określonego rozwiązania.|  
|[/ ResetSettings (devenv.exe)](../../ide/reference/resetsettings-devenv-exe.md)|Przywraca ustawienia domyślne programu Visual Studio. Opcjonalnie resetuje ustawienia do pliku określonego .vssettings.|  
|[/ Updateconfiguration (devenv.exe)](../../ide/reference/updateconfiguration-devenv-exe.md)|Powiadamia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do scalenia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pakietów w systemie i wyboru MEF pamięci podręcznej zostały wprowadzone zmiany.|  
|[/ Upgrade (devenv.exe)](../../ide/reference/upgrade-devenv-exe.md)|Uaktualnia plik określonego rozwiązania i wszystkie jego pliki projektu lub plik określony projekt do bieżącego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] formaty tych plików.|  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)