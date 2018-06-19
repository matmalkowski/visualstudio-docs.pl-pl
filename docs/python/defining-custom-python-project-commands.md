---
title: Sposób definiowania polecenia niestandardowych menu dla projektów języka Python
description: Pokazuje, jak edytować pliki projektów i elementów docelowych, aby dodać niestandardowych poleceń do menu kontekstowego projektu języka Python w programie Visual Studio. Polecenia można wywołać na programów wykonywalnych, skryptów, modułów, fragmentów kodu wbudowanego i pip.
ms.date: 02/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 93d7e01037712d633ed4c23534163924647183f4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31583635"
---
# <a name="defining-custom-commands-for-python-projects"></a>Definiowanie niestandardowego polecenia dla projektów języka Python

W trakcie pracy z projektów języka Python, możesz znaleźć go samodzielnie przełączenie do okna polecenia do uruchomienia określonego skrypty lub moduły, Uruchom polecenia narzędzia pip, lub uruchom dowolnego narzędzia. Aby usprawnić przepływ pracy, można dodać niestandardowe polecenia do **Python** podmenu w menu kontekstowe projektów języka Python. Tych poleceń, można uruchomić w oknie konsoli lub w oknie danych wyjściowych programu Visual Studio. Jak analizować błędów i ostrzeżeń z danych wyjściowych polecenia nakazać programowi Visual Studio umożliwia także wyrażeń regularnych.

Domyślnie tego menu zawiera tylko jednej **Uruchom Pylint** polecenia:

![Wygląd domyślny podmenu Python w menu kontekstowym projektu](media/custom-commands-default-menu.png)

Polecenia niestandardowe są wyświetlane w tym samym menu kontekstowego. Polecenia niestandardowe są dodawane do pliku projektu bezpośrednio, której odnoszą się do poszczególnych projektu. Istnieje również możliwość definiowania niestandardowych poleceń w `.targets` pliku, który można łatwo importować w wielu plikach projektów.

Niektóre szablony projektów języka Python w programie Visual Studio już dodać niestandardowe polecenia ich używania ich `.targets` pliku. Na przykład szablony projektów sieci Web Bottle i projektu sieci Web platformy Flask Dodaj dwa polecenia **początkowego serwera** i **początkowego debugowania serwera**. Szablon projektu sieci Web Django dodaje te same polecenia oraz kilka innych:

![Wygląd podmenu Python w menu kontekstowym projektu Django](media/custom-commands-django-menu.png)

Każdego polecenia niestandardowych mogą odwoływać się do pliku Python, moduł Python, wbudowanego kodu języka Python, dowolnego pliku wykonywalnego lub polecenie pip. Można również określić, jak i gdzie polecenie jest uruchamiane.

> [!Tip]
> Jeśli wprowadzisz zmiany w pliku projektu w edytorze tekstu, należy ponownie załadować projekt w programie Visual Studio, aby zastosować te zmiany. Na przykład należy ponownie załadować projekt po dodaniu definicji polecenia niestandardowych dla tych poleceń, są wyświetlane w menu kontekstowym projektu.
>
> Jak wiadomo, Visual Studio umożliwia edytowanie bezpośrednio pliku projektu. Najpierw kliknij prawym przyciskiem myszy plik projektu i wybierz opcję **Zwolnij projekt**, ponownie kliknij prawym przyciskiem myszy i wybierz **Edytuj (nazwa projektu)** otworzyć projektu w edytorze programu Visual Studio. Następnie należy i Zapisz zmiany, ponownie kliknij prawym przyciskiem myszy projekt i wybierz **Załaduj ponownie projekt**, który również wyświetli monit o potwierdzenie zamknięcia pliku projektu w edytorze.
>
> Podczas tworzenia polecenia niestandardowych, jednak te klika przycisk może stać się nużące. Większa wydajność przepływu pracy, załadować projektu programu Visual Studio i również otworzyć `'.pyproj` plik w edytorze oddzielne całkowicie (takie jak inne wystąpienie programu Visual Studio, Visual Studio Code, Notatnik itp.). Podczas zapisywania zmian w edytorze i przełączenia na program Visual Studio, Visual Studio wykrywa zmiany i zapyta, czy ponowne załadowanie projektu ("(nazwa) projektu został zmodyfikowany poza środowiskiem."). Wybierz **Załaduj ponownie** i zmiany są natychmiast stosowane tylko w jednym kroku.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Wskazówki: Dodawanie polecenia do pliku projektu

Aby zapoznać się z niestandardowych poleceń, w tej sekcji przeprowadzi Cię przez prosty przykład wykonywana bezpośrednio za pomocą python.exe pliku uruchomienia projektu. (Takiego polecenia skutecznie jest taka sama jak przy użyciu **Debuguj > Uruchom bez debugowania**.)

1. Tworzenie nowego projektu o nazwie "Python-CustomCommands" przy użyciu szablonu "Python aplikacji". (Zobacz [Szybki Start: Tworzenie projektu języka Python z szablonu](quickstart-02-python-in-visual-studio-project-from-template.md) instrukcje, jeśli nie znasz już z procesem.)

1. W `Python_CustomCommands.py`, Dodaj kod `print("Hello custom commands")`.

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, wybierz pozycję **Python**i zwróć uwagę, że jest tylko polecenie, które pojawia się podmenu **Uruchom PyLint**. Niestandardowych poleceń pojawiają się w tej samej podmenu.

1. Zgodnie z sugestią podaną w wprowadzenie, otwórz `Python-CustomCommands.pyproj` w osobnego edytora tekstu. Następnie dodaj następujące wiersze na końcu pliku wewnątrz zamknięcia `</Project>` i Zapisz plik.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Przełącza z powrotem do programu Visual Studio i wybierz **Załaduj ponownie** po monituje o zmianie pliku. Następnie sprawdź **Python** menu ponownie, aby zobaczyć, które **Uruchom PyLint** nadal jest jedynym elementem w nim wyświetlone ponieważ wiersze zostały dodane tylko replikować domyślnie `<PythonCommands>` właściwości grupy zawierające PyLint polecenie.

1. Przełącz się do edytora z pliku projektu i dodaj następującą `<Target>` definicji po `<PropertyGroup>`. Zgodnie z objaśnieniem w dalszej części tego artykułu, to `Target` element definiuje niestandardowe polecenie do uruchomienia przy użyciu pliku (określone przez właściwość "StartupFile") uruchamiania `python.exe` w oknie konsoli. Atrybut `ExecuteIn="consolepause"` używa konsoli, która oczekuje na naciśnięcie klawisza przed zamknięciem.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. Dodaj wartość element docelowy `Name` atrybutu `<PythonCommands>` właściwości grupy dodane wcześniej, dlatego, że element wygląda jak poniższy kod. Dodawanie do tej listy nazwę elementu docelowego jest co dodaje go do **Python** menu.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Jeśli chcesz, aby polecenia wyświetlany przed nazwami zdefiniowanymi w `$(PythonCommands)`, umieść je przed tokenu.

1. Zapisz plik projektu, przełącz się do programu Visual Studio i ponownie Załaduj projekt po wyświetleniu monitu. Następnie kliknij prawym przyciskiem myszy projekt "Python CustomCommands" i wybierz **Python**. Powinny pojawić się **Uruchom plik uruchamiania** elementu menu. Jeśli nie widzisz element menu, sprawdź dodania nazwa `<PythonCommands>` elementu. Zobacz też [Rozwiązywanie problemów](#troubleshooting) dalszej części tego artykułu.

    ![Polecenia niestandardowych znajdujących się w podmenu kontekstu Python](media/custom-commands-walkthrough-menu-item.png)

1. Wybierz **Uruchom plik uruchamiania** polecenia i powinna zostać wyświetlona okno polecenia pojawiają się od tekstu "Hello niestandardowych poleceń" następuje "naciśnij dowolny klawisz, aby kontynuować. . .".  Naciśnij dowolny klawisz, aby zamknąć okno.

    ![Dane wyjściowe polecenia niestandardowych w oknie konsoli](media/custom-commands-walkthrough-console.png)

1. Powrócić do edytora z pliku projektu i zmienić wartość `ExecuteIn` atrybutu `output`. Zapisz plik, przełącz się do programu Visual Studio ponownie Załaduj projekt i wywołaj polecenie ponownie. Teraz zostanie wyświetlony wyjściowy program są wyświetlane w programie Visual Studio **dane wyjściowe** okno:

    ![Dane wyjściowe polecenia niestandardowych w oknie danych wyjściowych](media/custom-commands-walkthrough-output-window.png)

1. Aby dodać więcej poleceń, zdefiniuj odpowiedniej `<Target>` elementu dla każdego polecenia Dodaj nazwę elementu docelowego do `<PythonCommands>` grupy właściwości i ponownie Załaduj projekt w programie Visual Studio.

>[!Tip]
> Jeśli wywołanie polecenia, że używa właściwości projektu, takie jak `($StartupFile)`i polecenie kończy się niepowodzeniem, ponieważ token jest niezdefiniowana, Visual Studio wyłącza polecenie do momentu ponownego załadowania projektu. Wprowadzanie zmian do projektu, określające właściwość, jednak nie Odśwież stan tych poleceń, należy ponownie załadować projekt w takich przypadkach.

## <a name="command-target-structure"></a>Polecenie strukturze docelowej

Ogólny kształt `<Target>` element jest wyświetlany w poniższym pseudo kodzie:

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

Aby odwołać się do właściwości projektu lub zmiennych środowiskowych zawartych w wartości atrybutu, użyj nazwy w `$()` token, takich jak `$(StartupFile)` i `$(MSBuildProjectDirectory)`. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Atrybuty docelowego

| Atrybut | Wymagane | Opis |
| --- | --- | --- |
| Nazwa | Tak | Identyfikator polecenia w ramach projektu programu Visual Studio. Ta nazwa musi zostać dodany do `<PythonCommands>` właściwości grupy dla polecenia w podmenu Python. |
| Etykieta | Tak | Nazwa wyświetlana interfejsu użytkownika zostanie wyświetlony w podmenu Python. |
| Zwraca | Tak | Musi zawierać `@(Commands)`, który wskazuje element docelowy jako polecenia. |

### <a name="createpythoncommanditem-attributes"></a>Atrybuty CreatePythonCommandItem

Wszystkie wartości atrybutów jest rozróżniana wielkość liter.

| Atrybut | Wymagane | Opis |
| --- | --- | --- |
| Element TargetType | Tak | Określa atrybut docelowy zawiera i sposobie ich użycia wraz z argumentami atrybutu:<ul><li>**wykonywalny**: uruchomienia pliku wykonywalnego o nazwie w celu dołączania wartości argumentów, tak jakby wprowadzone bezpośrednio w wierszu polecenia. Wartość musi zawierać tylko nazwę programu bez argumentów.</li><li>**skrypt**: Uruchom `python.exe` z nazwą pliku w lokalizacji docelowej, a następnie z wartością w argumentach.</li><li>**Moduł**: Uruchom `python -m` następuje nazwa modułu w lokalizacji docelowej, a następnie z wartością w argumentach.</li><li>**Kod**: Uruchom kodu wbudowanego zawarte w lokalizacji docelowej. Wartość argumentów jest ignorowana.</li><li>**PIP**: Uruchom `pip` przy użyciu polecenia w lokalizacji docelowej, a następnie argumentów; jest ExecuteIn ma ustawioną wartość "output", jednak zakłada pip `install` poleceń i używa docelowy jako nazwę pakietu.</li></ul> |
| docelowy | Tak | Nazwa pliku, nazwa modułu, kodu lub pip polecenia do użycia, w zależności od TargetType. |
| Argumenty | Optional | Określa ciąg argumentów (jeśli istnieje) ma zostać przypisany do obiektu docelowego. Należy pamiętać, że po TargetType `script`, argumenty są podane z programem Python nie `python.exe`. Ignorowane dla `code` TargetType. |
| ExecuteIn | Tak | Określa środowisko, w którym uruchomienia polecenia:<ul><li>**Konsola**: (domyślnie) uruchamia docelowy i argumenty tak, jakby ich zostaną wprowadzone bezpośrednio w wierszu polecenia. Zostanie wyświetlone okno polecenia, podczas gdy elementem docelowym jest uruchomiona, a następnie automatycznie zamknięte.</li><li>**consolepause**: tej samej konsoli, ale oczekuje na naciśnięcie klawisza przed zamknięciem okna.</li><li>**dane wyjściowe**: docelowy działa i wyświetla wyniki w oknie danych wyjściowych w programie Visual Studio. Jeśli element TargetType "pip", Visual Studio wykorzystuje docelowy jako nazwę pakietu i dołącza argumentów.</li><li>**repl**: docelowy działa w [okna interaktywnego Python](python-interactive-repl-in-visual-studio.md); opcjonalna nazwa wyświetlana jest używany jako tytuł okna.</li><li>**Brak**: działa tak samo jak konsoli.</li></ul>|
| WorkingDirectory | Optional | Folder, w którym można uruchomić polecenie. |
| ErrorRegex<br>WarningRegEx | Optional | Używana tylko wtedy, gdy ExecuteIn jest `output`. Obie wartości Określ wyrażenie regularne, z którym program Visual Studio analizuje dane wyjściowe polecenia, aby wyświetlić błędy i ostrzeżenia w oknie Lista błędów. Jeśli nie zostanie określony, polecenie nie dotyczy w oknie Lista błędów. Aby uzyskać więcej informacji, w jaki Visual Studio oczekuje, zobacz [grup przechwytywania o nazwie](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | Optional | Listę wymagań dotyczących pakietu dla polecenia przy użyciu tego samego formatu co [requirements.txt](https://pip.readthedocs.io/en/1.1/requirements.html) (pip.readthedocs.io). **Uruchom PyLint** polecenia, na przykład Określa `pylint>=1.0.0`. Przed uruchomieniem polecenia, programu Visual Studio sprawdza, czy są zainstalowane wszystkie pakiety na liście. Aby zainstalować wszystkie brakujące pakiety programu Visual Studio korzysta pip. |
| Środowisko | Optional | Ciąg zmiennych środowiskowych, aby zdefiniować przed uruchomieniem polecenia. Używa każdej zmiennej w postaci nazwa = wartość, gdy wiele zmiennych, oddzielając je średnikami. Zmienna z wieloma wartościami musi być zawarty w pojedynczym lub podwójnym cudzysłowie, podobnie jak w "Nazwa = wartość1; WARTOŚĆ2 ". |

#### <a name="named-capture-groups-for-regular-expressions"></a>Grup przechwytywania o nazwie dla wyrażeń regularnych

Podczas analizowania błędów i ostrzeżeń z danych wyjściowych polecenia, programu Visual Studio oczekuje wyrażeń regularnych w `ErrorRegex` i `WarningRegex` wartości należy użyć następującego o nazwie grupy:

- `(?<message>...)`: Tekst błędu
- `(?<code>...)`: Kod błędu
- `(?<filename>...)`: Nazwa pliku, dla którego zgłaszany jest błąd
- `(?<line>...)`: Numer wiersza lokalizacja pliku, dla którego zgłosił błąd.
- `(?<column>...)`: Numer kolumny Lokalizacja pliku, dla którego zgłosił błąd.

Na przykład PyLint tworzy ostrzeżenia mają następującą postać:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Aby umożliwić Visual Studio, aby wyodrębnić odpowiednie informacje z takich ostrzeżeń i wyświetlić je w **listy błędów** okna, `WarningRegex` wartość **Uruchom Pylint** polecenia jest następujący:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Należy pamiętać, że `msg_id` wartości faktycznie powinna być `code`, zobacz [3680 problem](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="creating-a-targets-file-with-custom-commands"></a>Tworzenie pliku .targets za pomocą polecenia niestandardowych

Definiowanie niestandardowych poleceń w pliku projektu udostępnia ten plik projektu. Użycie poleceń w wielu plikach projektów, możesz zamiast tego Zdefiniuj `<PythonCommands>` właściwości grupy, a wszystkie Twoje `<Target>` elementów w `.targets` pliku. Można następnie zaimportować do pojedyncze pliki projektu.

`.targets` Plik jest sformatowany w następujący sposób:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

Aby załadować `.targets` plików do projektu, umieść `<Import Project="(path)">` elementu w obrębie `<Project>` elementu. Na przykład, jeśli istnieje plik o nazwie `CustomCommands.targets` w `targets` podfolderu w projekcie, użyj następującego kodu:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Przy każdej zmianie `.targets` pliku, należy ponownie załadować *rozwiązania* zawierający projekt, nie tylko projektu.

## <a name="example-commands"></a>Przykładowe polecenia

### <a name="run-pylint-module-target"></a>Uruchom PyLint (moduł docelowy)

Poniższy kod zostanie wyświetlony w `Microsoft.PythonTools.targets` pliku:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Uruchomienie instalacji narzędzia pip z określonego pakietu (pip docelowy)

Następujące polecenie uruchamia `pip install my-package` w oknie danych wyjściowych. Można użyć polecenia, takich jak podczas tworzenia pakietu i testowania instalacji. Należy pamiętać, że docelowy zawiera nazwę pakietu, a nie `install` polecenia, które przyjęto, że przy użyciu `ExecuteIn="output"`.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>Pokaż przestarzałe pip pakiety (pip docelowy)

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>Uruchom plik wykonywalny z consolepause

Następujące polecenie, po prostu działa `where` pokazanie Python pliki w folderze projektu:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>Uruchom serwer i debugowania wykonywania polecenia serwera

Aby zapoznać się z jak **początkowego serwera** i **początkowego debugowania serwera** poleceń dla projektów sieci web są zdefiniowane, sprawdź [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Zainstaluj pakiet do tworzenia aplikacji

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) używane z uprawnieniami.*

### <a name="generate-windows-installer"></a>Generowanie Instalatora Windows

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) używane z uprawnieniami.*

### <a name="generate-wheel-package"></a>Generuj pakiet wheel

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*Z [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub) używane z uprawnieniami.*

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="message-the-project-file-could-not-be-loaded"></a>Komunikat o błędzie: "plik projektu nie można załadować"

Wskazuje, czy masz błędów składni w pliku projektu. Komunikat zawiera konkretny błąd o numerze wiersza i znaku na pozycji.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Zamyka okno konsoli od razu po uruchomieniu polecenia

Użyj `ExecuteIn="consolepause"` zamiast `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>Polecenie nie jest wyświetlane w menu

Sprawdź, czy polecenie jest zawarte w `<PythonCommands>` grupy właściwości, oraz że nazwę na liście polecenia zgodny nazwa określona w `<Target>` elementu.

Na przykład w następujących elementach z nazwą "Example" w grupie właściwości nie jest zgodna z nazwą "ExampleCommand" w elemencie docelowym. Programu Visual Studio nie znaleźć polecenia o nazwie "Example", więc zostanie wyświetlone żadne polecenie. Użyj "ExampleCommand" na liście polecenia lub zmień nazwę elementu docelowego "Example" tylko.

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Komunikat o błędzie: Wystąpił błąd podczas uruchamiania (nazwa polecenia). Nie można pobrać polecenia (Nazwa docelowego) z projektu.

Oznacza to, że zawartość `<Target>` lub `<CreatePythonCommandItem>` elementy są nieprawidłowe. Możliwe przyczyny:

- Wymagane `Target` atrybut jest pusty.
- Wymagane `TargetType` jest pusta lub zawiera nierozpoznaną wartość atrybutu.
- Wymagane `ExecuteIn` jest pusta lub zawiera nierozpoznaną wartość atrybutu.
- `ErrorRegex` lub `WarningRegex` został określony bez ustawienia `ExecuteIn="output"`.
- Nierozpoznany atrybuty istnieje w elemencie. Na przykład użyto `Argumnets` (zapisana) zamiast `Arguments`.

Wartości atrybutów może być pusta, odwołując się do właściwości, która nie jest zdefiniowany. Na przykład, jeśli używasz token `$(StartupFile)` , ale plik uruchomienia nie została zdefiniowana w projekcie, a następnie token jest rozpoznawany jako ciąg pusty. W takich przypadkach możesz określić wartość domyślną. Na przykład **uruchamiania serwera** i **serwer uruchamiania debugowania** poleceń zdefiniowanych w Bottle, Flask, i domyślnie szablony projektów Django `manage.py` , jeśli nie określono inaczej pliku uruchamiania serwera we właściwościach projektu.

### <a name="visual-studio-hangs-and-crashes-when-running-the-command"></a>Program Visual Studio zawiesza się i ulega awarii podczas uruchamiania polecenia

Prawdopodobnie w przypadku próby uruchomienia polecenia konsoli z `ExecuteIn="output"`, w którym to przypadku programu Visual Studio może ulec awarii próby przeprowadzenia analizy danych wyjściowych. Zamiast nich należy używać słów kluczowych `ExecuteIn="console"`. (Zobacz [wystawiać 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operate-program-or-batch-file"></a>Wykonywalny polecenia "nie jest rozpoznawana jako polecenie wewnętrzne lub zewnętrzne, działanie programu lub pliku wsadowego"

Korzystając z `TargetType="executable"`, wartość w `Target` musi być *tylko* bez żadnych argumentów, takie jak "python" lub "python.exe" tylko nazwę programu. Przenieś wszystkie argumenty `Arguments` atrybutu.
