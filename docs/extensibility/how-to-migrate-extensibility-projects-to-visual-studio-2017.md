---
title: "Porady: Migracja rozszerzalności projekty do programu Visual Studio 2017 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb00d2c338ac1ef9e2be6d77d68ebfe2a246d807
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2017
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Porady: Migracja rozszerzalności projekty do programu Visual Studio 2017 r

Ten dokument wyjaśniono, jak uaktualnić rozszerzalności projekty do programu Visual Studio 2017 r. Oprócz opisujące, jak zaktualizować plików projektu, opisano w nim również sposób uaktualniania z wersji manifestu rozszerzenia 2 (VSIX v2) do nowej wersji 3 format manifestu VSIX (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instalowanie programu Visual Studio 2017 przy użyciu wymagane obciążenia

Upewnij się, że ta instalacja obejmuje następujące obciążenia:

* .NET — rozwój pulpitu
* Programowanie rozszerzenia usługi Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Otwórz rozwiązanie VSIX w Visual Studio 2017 r.

Wszystkie projekty VSIX wymaga wersji głównej jednokierunkowe uaktualnienia do programu Visual Studio 2017 r.

Plik projektu (na przykład *.csproj) zostaną zaktualizowane:

* MinimumVisualStudioVersion — teraz wartość 15.0
* OldToolsVersion (jeśli istnieje wcześniej)-teraz wartość 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Pakiet Microsoft.VSSDK.BuildTools NuGet aktualizacji

>**Uwaga:** rozwiązania nie odwołują się do pakietu Microsoft.VSSDK.BuildTools NuGet, możesz pominąć ten krok.

Aby można było skompilować rozszerzenia w nowej wersji pliku VSIX 3 (wersja 3), rozwiązania będzie konieczne ma zostać utworzony przy użyciu nowych narzędzi kompilacji VSSDK. To zostanie zainstalowany z programu Visual Studio 2017, ale rozszerzenie VSIX v2 może zawierający odwołanie do starszej wersji za pośrednictwem pakietu NuGet. Jeśli tak, należy ręcznie zainstalować aktualizację pakietów Microsoft.VSSDK.BuildTools NuGet dla rozwiązania.

Aby zaktualizować odwołań NuGet do Microsoft.VSSDK.BuildTools:

* Kliknij prawym przyciskiem myszy w ramach rozwiązania i wybierz polecenie **Zarządzaj pakietami NuGet rozwiązania...**
* Przejdź do **aktualizacje** kartę.
* Wybierz Microsoft.VSSDK.BuildTools (Najnowsza wersja).
* Naciśnij klawisz **aktualizacji**.

![Narzędzia kompilacji VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Wprowadzanie zmian do manifestu rozszerzenia VSIX

Aby upewnić się, że użytkownika instalacji programu Visual Studio ma wszystkie zestawy wymagane do uruchomienia rozszerzenia, należy określić wszystkie wstępnie wymagane składniki lub pakietów w pliku manifestu rozszerzenia. Gdy użytkownik próbuje zainstalować rozszerzenie, VSIXInstaller sprawdzi, czy wszystkie wymagania wstępne są zainstalowane. Jeśli brakuje niektórych, użytkownik wyświetli monit o Zainstaluj brakujące składniki jako część procesu instalacji rozszerzenia.

>**Uwaga:** co najmniej wszystkich rozszerzeń należy określić Edytor składnik programu Visual Studio jako warunek wstępny.

* Edytuj plik manifestu rozszerzenia (zwykle nazywane source.extension.vsixmanifest).
* Upewnij się, `InstallationTarget` obejmuje 15.0.
* Dodawanie wymagań wstępnych instalacji wymagane (jak pokazano w poniższym przykładzie).
  * Firma Microsoft zaleca się, że możesz określić tylko identyfikatory składników wymagania wstępne instalacji.
  * Zobacz sekcję na końcu niniejszego dokumentu [instrukcje dotyczące identyfikowania identyfikatory składników](#finding-component-ids).

Przykład:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opcja: Użyj projektanta, aby wprowadzić zmiany do manifestu rozszerzenia VSIX

Zamiast bezpośredniego edytowania pliku XML manifestu, można użyć nowej **wymagania wstępne** będzie można zaktualizować kartę projektanta manifestu, aby wybrać wymagań wstępnych i XML.

>**Uwaga:** projektanta manifestu tylko pozwala wybrać składniki (nie obciążeń lub pakietów), które są zainstalowane w bieżącym wystąpieniu programu Visual Studio. Jeśli konieczne jest dodanie do wymagań wstępnych dla obciążenia, pakietu lub składnik, który nie jest obecnie zainstalowany, bezpośredniego edytowania manifestu XML.

* Otwórz plik Source.Extension.vsixmanifest,a [projekt].
* Wybierz **wymagania wstępne** kartę i naciśnij klawisz **nowy** przycisku.

  ![Projektant manifestu VSIX](media/vsix-manifest-designer.png)

* **Dodawanie nowych wymagań wstępnych** zostanie otwarte okno.

  ![Dodaj wstępnie wymaganego pliku vsix](media/add-vsix-prerequisite.png)

* Kliknij listę rozwijaną dla **nazwa** i wybierz odpowiednią wymagań wstępnych.
* Zaktualizuj wersję, jeśli jest to wymagane.

  >Uwaga: Pole wersji będzie wstępnie wypełniane wersja aktualnie zainstalowanego składnika, z zakresu do rozszerzania (z wyjątkiem) następnej wersji głównej składnika.

  ![Dodaj wstępnie wymaganego programu roslyn](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="update-debug-settings-for-project"></a>Zaktualizuj ustawienia debugowania dla projektu

Jeśli chcesz debugować rozszerzenia w eksperymentalne wystąpienie programu Visual Studio, upewnij się, że ustawienia projektu dla **debugowania** > **uruchomienie akcji** ma **Start zewnętrznych Program:** wartość do pliku devenv.exe instalację programu Visual Studio 2017 r.

Może ona wyglądać tak:

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![Uruchom program zewnętrznych](media/start-external-program.png)

>**Uwaga:** Akcja uruchamiania debugowania jest zazwyczaj przechowywany w. csproj.user pliku. Ten plik znajduje się zwykle w pliku .gitignore i w związku z tym nie są zwykle zapisywane z innymi plikami projektu, gdy zostało zatwierdzone do kontroli źródła. Tak jeśli mają pobierane rozwiązania świeże z kontroli źródła prawdopodobnie projektu nie odniesie żadnych wartości ustawione dla Akcja uruchamiania. Nowe projekty VSIX utworzone za pomocą programu Visual Studio 2017 będzie miał. plik csproj.user utworzony przy użyciu ustawień domyślnych wskazuje bieżący katalog instalacyjny programu Visual Studio. Jednak w przypadku migracji v2 rozszerzenie VSIX, istnieje prawdopodobieństwo, że. csproj.user plik będzie zawierał odwołania do katalogu instalacyjnego poprzedniej wersji programu Visual Studio. Ustawienie wartości dla **debugowania** > **uruchomienie akcji** umożliwi prawidłowe wystąpienie programu Visual Studio eksperymentalne do uruchomienia podczas debugowania na Twoje rozszerzenie.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Sprawdź, czy rozszerzenie kompilacje poprawnie (jako VSIX v3)

* Tworzenie projektu VSIX.
* Rozpakuj wygenerowanego pliku VSIX.
  * Przez domyślny, życie pliku VSIX wewnątrz bin/Debug lub bin i wersji jako .vsix [YourCustomExtension].
  * Zmień nazwę .vsix zip, aby łatwo przeglądać zawartość.
* Sprawdź, czy istnieją trzy pliki:
  * Extension.vsixmanifest
  * Manifest.JSON
  * Catalog.JSON

## <a name="check-when-all-required-prerequisites-are-installed"></a>Sprawdź, gdy wszystkie wymagania wstępne są zainstalowane

Przetestuj pliku VSIX pomyślnie instaluje na komputerze z wszystkie wymagania wstępne zainstalowane.

>**Uwaga:** przed zainstalowaniem dowolnego rozszerzenia, zamknij wszystkie wystąpienia programu Visual Studio.

Próba zainstalowania rozszerzenia:

* W programie Visual Studio 2017 r.

![Instalator VSIX w Visual Studio 2017 r.](media/vsixinstaller-vs-2017.png)

* Opcjonalnie: Sprawdź poprzednie wersje programu Visual Studio.
  * Potwierdza zgodność z poprzednimi wersjami.
  * Powinny działać dla programu Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Opcjonalnie: Sprawdź, czy sprawdzanie wersji Instalatora VSIX umożliwia wybór wersji.
  * Zawiera poprzednie wersje programu Visual Studio (jeśli jest zainstalowana).
  * Obejmuje Visual Studio 2017 r.

Jeśli ostatnio otwarto Visual Studio, mogą pojawić okno dialogowe następująco:

![VS uruchomionego procesu](media/vs-running-processes.png)

Poczekaj, aż procesy wyłączyć, lub ręcznie zakończenia zadania. Procesy można znaleźć przez nazwę listy lub o identyfikatorze PID, wyświetlane w nawiasach.

>**Uwaga:** te procesy nie automatycznie wyłączy wystąpienia programu Visual Studio jest uruchomiona. Należy upewnić się, że zostały Zamknij wszystkie wystąpienia programu Visual Studio na komputerze — łącznie z tymi od innych użytkowników, następnie kontynuuj ponowić próbę.

## <a name="check-when-missing-the-required-prerequisites"></a>Sprawdź, gdy brakujące wymagania wstępne

* Próba zainstalowania rozszerzenia na maszynie z programu Visual Studio 2017 ten KONTENER jest nie wszystkie składniki, które są określone w wymaganiach wstępnych (powyżej).
* Sprawdź, czy instalacja identyfikuje brakujących składników/s i wyświetla je jako wymaganie wstępne w VSIXInstaller.
* Uwaga: Podniesienia uprawnień konieczności czy wszystkie wymagania wstępne, które muszą być zainstalowane z rozszerzeniem.

![Brak wstępnie wymaganego składnika vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>Wcześniejsze podjęcie decyzji dotyczących składników

Podczas wyszukiwania zależności, można zauważyć, że jedną zależność może mapować wielu składników. Do określenia zależności, które należy określić jako z wymagań wstępnych, zaleca się, że wybierasz składnika, który funkcjonalność podobną do rozszerzenia i również wziąć pod uwagę użytkowników i jakiego rodzaju składników będzie prawdopodobnie zainstalowanie lub nie pamiętać instalacji. Zalecamy także tworzenie rozszerzeń w taki sposób, w którym wymagania wstępne spełniają minimum, które umożliwiają rozszerzenie do uruchomienia i dodatkowych funkcji, niech być nieaktywni, jeśli pewne składniki nie są wykrywane.

Aby podać dodatkowe wskazówki, określiliśmy kilka typowych rozszerzenia i ich sugerowane wymagania wstępne:

Typ rozszerzenia | Nazwa wyświetlana | Identyfikator
--- | --- | ---
Edytor | Edytor podstawowe usługi Visual Studio  | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# i Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Zarządzane podstawowe obciążenie pulpitu | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debuger | Debuger Just In Time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>Znajdowanie identyfikatory składników

Na liście składników posortowane według produktu Visual Studio jest w [obciążenia 2017 r w usłudze Visual Studio i identyfikatory składników](https://aka.ms/vs2017componentIDs). Użyj tych identyfikatorów składników z wymagań wstępnych identyfikatorów w manifeście.

Jeśli nie wiesz, który składnik zawiera określone pobieranie plików binarnych, [składnika -> arkusza mapowanie binarne](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Istnieją cztery kolumny w arkuszu programu Excel: **nazwa składnika**, **ComponentId**, **wersji**, i **Binary / nazwy plików**.  Filtry można użyć do wyszukiwania i znaleźć konkretnych składnikach i pliki binarne.

Dla wszystkich odwołań należy najpierw określić, które znajdują się w głównym składnikiem edytora (Microsoft.VisualStudio.Component.CoreEditor).  Co najmniej wymagamy podstawowy składnik Edytor można określić jako warunek wstępny dla wszystkich rozszerzeń. Odwołań, które pozostało nie będących w edytorze podstawowe, należy dodać filtry w **plików binarnych / nazwy plików** sekcji, aby znaleźć składników, które nie ma żadnej z podzbioru te odwołania.

Przykłady:

* Jeśli korzystasz z rozszerzenia debugera i dowiedzieć się, że projekt zawiera odwołanie do VSDebugEng.dll i VSDebug.dll, kliknij przycisk filtru w **plików binarnych / nazwy plików** nagłówka.  Wyszukaj "VSDebugEng.dll", a następnie kliknij przycisk OK.  Następnie kliknij przycisk filtru w **plików binarnych / nazwy plików** ponownie nagłówka i wyszukaj "VSDebug.dll".  Zaznacz pole wyboru "Dodaj bieżące zaznaczenie do filtru" i wybierz przycisk OK.  Teraz wyglądać za pośrednictwem **nazwa składnika** można znaleźć składnika, które najbardziej powiązany typ rozszerzenia. W tym przykładzie wybrano czy Just-In-Time debugera i dodaj go do Twojego vsixmanifest.
* Jeśli wiesz, że projektu dotyczy elementów debugera, można wyszukiwać na "debugera" w polu wyszukiwania filtr jakie składniki zawierają debugera w swoim imieniu.

## <a name="specifying-a-visual-studio-2017-release"></a>Określanie wersji programu Visual Studio 2017 r.

Jeśli rozszerzenie wymaga określonej wersji programu Visual Studio 2017, na przykład zależy od funkcji wydane w ramach 15 ustęp 3, należy określić numer kompilacji w Twojej VSIX **InstallationTarget**. Na przykład wersji 15 ustęp 3 ma numer kompilacji programu "15.0.26730.3". Widać mapowania wydań numery kompilacji [tutaj](../install/visual-studio-build-numbers-and-release-dates.md). Za pomocą numeru wersji 15 ustęp "3" nie będzie działać prawidłowo.

Jeśli rozszerzenie wymaga 15 ustęp 3 lub nowszym, czy zadeklarować **wersji InstallationTarget** jako [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```