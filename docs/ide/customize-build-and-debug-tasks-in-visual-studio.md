---
title: Dostosowywanie kompilacji i debugowanie zadań w programie Visual Studio przy użyciu tasks.vs.json i launch.vs.json | Dokumentacja firmy Microsoft
ms.date: 02/21/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
- vsworkspacesettings.json file [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc193c8c54c09a7d2950cd80994d62512d9232d7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Dostosowywanie kompilacji i debugowanie zadań rozwoju "Otwórz Folder"

Program Visual Studio umożliwia uruchamianie wielu różnych językach i codebases, ale nie wiadomo, jak uruchomić wszystkie. Jeśli użytkownik [otworzyć folderu kodu](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) w programie Visual Studio i Visual Studio potrafi do uruchomienia kodu, można uruchomić w od razu bez przeprowadzania dodatkowej konfiguracji.

Jeśli codebase używa narzędzia niestandardowej kompilacji, które nie rozpoznaje programu Visual Studio, musisz podać niektóre szczegóły konfiguracji do uruchamiania i debugowania kodu w programie Visual Studio. Poinstruuj program Visual Studio sposób tworzenia kodu, definiując *zadania kompilacji*. Możesz utworzyć jedną lub więcej zadania, aby określić wszystkie elementy potrzebne języka Aby skompilować i uruchomić kodu kompilacji. Istnieje również możliwość utworzenia dowolnego zadania, które można wykonać prawie wszystko, co ma. Na przykład można utworzyć zadania na wyświetlanie zawartości folderu lub aby zmienić nazwę pliku.

Dostosowywanie kodu bez projektu przy użyciu następujących *JSON* plików:

|Nazwa pliku|Cel|
|-|-|
|*tasks.vs.json*|Określenie niestandardowych poleceń kompilacji i przełączniki kompilatora i dowolnego (z systemem innym niż kompilacji powiązane) zadania.<br>Używanych przez **Eksploratora rozwiązań** elementu menu kontekstowego **skonfigurować zadania**.|
|*launch.vs.json*|Określ argumenty wiersza polecenia do debugowania.<br>Używanych przez **Eksploratora rozwiązań** elementu menu kontekstowego **debugowania i ustawienia uruchamiania**.|
|*VSWorkspaceSettings.json*|Ustawienia ogólne, które mogą mieć wpływ na zadania, a następnie uruchom. Na przykład definiowanie `envVars` w *VSWorkspaceSettings.json* dodaje określone zmienne środowiskowe zewnętrznie uruchomienie poleceń.<br>Ten plik możesz utworzyć ręcznie.|

Te *JSON* pliki znajdują się w ukrytym folderze o nazwie *.vs* w folderze głównym baza kodu. *Tasks.vs.json* i *launch.vs.json* pliki są tworzone przez program Visual Studio na zgodnie z potrzebami, po wybraniu **skonfigurować zadania** lub **debugowania Ustawienia uruchamiania i** do pliku lub folderu w **Eksploratora rozwiązań**. Te *JSON* pliki są ukryte, ponieważ użytkownicy zwykle nie chcesz sprawdzić ich do kontroli źródła. Jednak jeśli chcesz mieć możliwość sprawdzenia je do kontroli źródła, przeciągnij pliki w folderze głównym baza kodu, gdy są one widoczne.

> [!TIP]
> Aby wyświetlić ukryte pliki w programie Visual Studio, wybierz **Pokaż wszystkie pliki** znajdującego się na **Eksploratora rozwiązań** paska narzędzi.

## <a name="define-tasks-with-tasksvsjson"></a>Definiowanie zadań z tasks.vs.json

Można zautomatyzować kompilacji skryptów lub inne operacje zewnętrznych od plików, które ma w bieżącym obszarze roboczym przez uruchomienie zadania bezpośrednio w środowisku IDE. Można skonfigurować nowe zadanie prawym przyciskiem myszy plik lub folder, a następnie wybierając **skonfigurować zadania**.

![Konfigurowanie menu zadania](../ide/media/customize-configure-tasks-menu.png)

Tworzy (lub otwiera) *tasks.vs.json* w pliku *.vs* folderu. Można zdefiniować zadania kompilacji lub dowolnego zadania w tym pliku, a następnie wywołaj go przy użyciu nazwy, można użyć go z **Eksploratora rozwiązań** menu kontekstowego.

Niestandardowe zadania można dodawać do pojedynczych plików lub do wszystkich plików określonego typu. Na przykład pliki pakietu NuGet można skonfigurować tak, aby zadanie "Przywracanie pakietów" lub wszystkie pliki źródłowe można skonfigurować tak, aby zadanie analizy statycznej, takich jak linter dla wszystkich *js* plików.

### <a name="define-custom-build-tasks"></a>Definiowanie zadań niestandardowej kompilacji

Jeśli baza kodu używa narzędzia niestandardowej kompilacji, które nie rozpoznaje programu Visual Studio, nie można uruchomić i debugowania kodu w programie Visual Studio, dopóki nie zostaną wykonane, niektóre kroki konfiguracji. Program Visual Studio udostępnia *zadania kompilacji* w przypadku, gdy program Visual Studio można ustalić sposób tworzenia, ponowne skompilowanie i czyszczenie kodu. *Tasks.vs.json* kompilacji pozamałżeńskie pliku zadań narzędzi używanych przez baza kodu do kompilacji z pętli wewnętrzny programowania Visual Studio niestandardowe.

Należy wziąć pod uwagę codebase, która składa się z jednego pliku C# o nazwie *hello.cs*. *Pliku reguł programu make* dla takich codebase może wyglądać następująco:

```makefile
build: directory hello.exe

hello.exe: hello.cs
    csc -debug hello.cs /out:bin\hello.exe

clean:
    del bin\hello.exe bin\hello.pdb

rebuild: clean build

directory: bin

bin:
    md bin
```

Na przykład *pliku reguł programu make* który zawiera kompilacji czystą i skompiluj ponownie elementy docelowe, można określić następujące *tasks.vs.json* pliku. Zawiera trzy zadania kompilacji do tworzenia, ponownie skompilować i czyszczenia kodu za pomocą NMAKE jako narzędzie kompilacji.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "makefile-build",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "build",
      "command": "nmake",
      "args": [ "build" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-clean",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "clean",
      "command": "nmake",
      "args": [ "clean" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-rebuild",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "rebuild",
      "command": "nmake",
      "args": [ "rebuild" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    }
  ]
}
```

Po zdefiniowaniu zadania kompilacji w *tasks.vs.json*, dodatkowy kontekst elementy menu są dodawane do odpowiednich plików w **Eksploratora rozwiązań**. Na przykład "kompilacji", "odbudować" i "Wyczyść" opcje są dodawane do dowolnego menu kontekstowego *pliku reguł programu make* plików.

![menu kontekstowe pliku reguł programu make z kompilacją, ponowne skompilowanie i czyszczenia](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Polecenia są wyświetlane w menu kontekstowym w obszarze **skonfigurować zadania** polecenia ze względu na ich `contextType` ustawienia. "kompilacji", "odbudować" i "Wyczyść" są poleceń kompilacji, aby były wyświetlane w sekcji kompilacji w środku menu kontekstowego.

Po wybraniu jednej z tych opcji, wykonuje zadanie. Zostaną wyświetlone dane wyjściowe w **dane wyjściowe** okna i błędy kompilacji są wyświetlane w **listy błędów**.

### <a name="define-arbitrary-tasks"></a>Definiowanie dowolnych zadań

Można zdefiniować dowolnego zadania w *tasks.vs.json* pliku wszystko, co chcesz zrobić. Na przykład można zdefiniować zadania, aby wyświetlić nazwę aktualnie wybranego pliku w **dane wyjściowe** okna, lub aby wyświetlić listę plików w określonym katalogu.

W poniższym przykładzie przedstawiono *tasks.vs.json* pliku, który definiuje jedno zadanie. Gdy została wywołana, zadanie Wyświetla nazwę pliku aktualnie wybranego *js* pliku.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.js",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "echo ${file}" ]
    }
  ]
}
```

- `taskName` Określa nazwę, która jest wyświetlana w menu kontekstowym.
- `appliesTo` Określa pliki, które można wykonać polecenia na.
- `command` Właściwość określa polecenie do wywołania. W tym przykładzie `COMSPEC` zmiennej środowiskowej jest używany do identyfikowania interpreter wiersza polecenia, zwykle *cmd.exe*.
- `args` Właściwość określa argumenty do przekazania do wywoływanej polecenia.
- `${file}` Makro pobiera wybrany plik w **Eksploratora rozwiązań**.

Po zapisaniu *tasks.vs.json*, kliknąć prawym przyciskiem myszy na dowolnym *js* plików w folderze, a następnie wybierz pozycję **Echo filename**. Nazwa pliku jest wyświetlana w **dane wyjściowe** okna.

> [!NOTE]
> Jeśli baza kodu nie zawiera *tasks.vs.json* plików, można go utworzyć, wybierając **skonfigurować zadania** z menu kliknij prawym przyciskiem myszy lub kontekstu pliku w **Eksploratora rozwiązań**.

W następnym przykładzie zdefiniowano zadań, która zawiera pliki i podfoldery z *bin* katalogu.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "List Outputs",
      "appliesTo": "*",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "dir ${outDir}" ]
    }
  ]
}
```

- `${outDir}` zdefiniowano niestandardowe makra, który jest pierwszy przed `tasks` bloku. Następnie jest wywoływana `args` właściwości.

To zadanie dotyczy wszystkich plików. Po otwarciu menu kontekstowego w jakikolwiek plik w **Eksploratora rozwiązań**, nazwa zadania **dane wyjściowe listy** pojawia się w dolnej części menu. Po wybraniu **listy danych wyjściowych**, zawartość *bin* katalogu są wymienione w **dane wyjściowe** okna w programie Visual Studio.

![Dowolnego zadania w menu kontekstowym](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Zakres ustawień

Wiele *tasks.vs.json* pliki mogą znajdować się w katalogu głównego i podkatalogi codebase. Ten projekt umożliwia elastyczność w celu zapewnienia inaczej w różnych podkatalogi bazy kodu. Visual Studio agreguje lub zastępuje ustawienia w całym codebase, stawiając na pierwszym miejscu pliki w następującej kolejności:

- Ustawienia plików w folderze głównym *.vs* katalogu.
- Katalog, w której jest obliczana ustawienie.
- Katalog nadrzędny bieżącego katalogu, aż do katalogu głównego.
- Ustawienia plików w katalogu głównym.

Mają zastosowanie następujące reguły agregacji *tasks.vs.json* i *VSWorkspaceSettings.json* plików. Aby uzyskać informacje na agregowaniem ustawienia w innych plików Zobacz sekcję odpowiednie dla tego pliku w tym artykule.

### <a name="properties-for-tasksvsjson"></a>Właściwości tasks.vs.json

W tej sekcji opisano niektóre właściwości można określić w *tasks.vs.json*.

#### <a name="appliesto"></a>Element appliesTo

Można tworzyć zadania dla dowolnego pliku lub folderu, określając jej nazwę w `appliesTo` pól, na przykład `"appliesTo": "hello.js"`. Następujące maski plików może być używane jako wartości:

|||
|-|-|
|`"*"`| zadanie jest dostępna dla wszystkich plików i folderów w obszarze roboczym|
|`"*/"`| zadanie jest dostępne dla wszystkich folderów w obszarze roboczym|
|`"*.js"`| zadanie jest dostępny dla wszystkich plików z rozszerzeniem *js* w obszarze roboczym|
|`"/*.js"`| zadanie jest dostępny dla wszystkich plików z rozszerzeniem *js* w folderze głównym obszaru roboczego|
|`"src/*/"`| zadanie jest dostępne dla wszystkich podfolderów *src* folderu|
|`"makefile"`| zadanie jest dostępna dla wszystkich *pliku reguł programu make* plików w obszarze roboczym|
|`"/makefile"`| zadanie jest dostępne tylko dla *pliku reguł programu make* w folderze głównym obszaru roboczego|

#### <a name="macros-for-tasksvsjson"></a>Makra dla tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Określa wszelkie zmienna środowiskowa (na przykład ${env. ŚCIEŻKA} ${env.COMSPEC} itd.) dla wiersza polecenia dewelopera ustawiono. Aby uzyskać więcej informacji, zobacz [wiersz polecenia dla programu Visual Studio deweloperów](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| Pełna ścieżka do folderu roboczego (na przykład *C:\sources\hello*)|
|`${file}`| Pełna ścieżka pliku lub folder wybrany do uruchomienia tego zadania przed (na przykład *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Ścieżka względna do pliku lub folderu (na przykład *src\hello.js*)|
|`${fileBasename}`| Nazwa pliku bez ścieżki i rozszerzenia (na przykład *hello*)|
|`${fileDirname}`| Pełna ścieżka do pliku, z wyjątkiem pliku (na przykład *C:\sources\hello\src*)|
|`${fileExtname}`| Rozszerzenie wybranego pliku (na przykład *js*)|

## <a name="configure-debugging-with-launchvsjson"></a>Konfigurowanie debugowania z launch.vs.json

1. Aby skonfigurować Twoje ścieżki bazowej kodu do debugowania, w **Eksploratora rozwiązań** wybierz **debugowania i ustawienia uruchamiania** element menu z menu kliknij prawym przyciskiem myszy lub kontekstu pliku wykonywalnego.

   ![Menu kontekstowe debugowania i ustawienia uruchamiania](media/customize-debug-launch-menu.png)

1. W **wybierz debuger** okno dialogowe, wybierz opcję, a następnie wybierz **wybierz** przycisku.

   ![Wybierz okno dialogowe debugera](media/customize-select-a-debugger.png)

   Jeśli *launch.vs.json* plik już nie istnieje, jest tworzona.

   ```json
   {
     "version": "0.2.1",
     "defaults": {},
     "configurations": [
       {
         "type": "default",
         "project": "bin\\hello.exe",
         "name": "hello.exe"
       }
     ]
   }
   ```

1. Następnie kliknij prawym przyciskiem myszy plik wykonywalny w **Eksploratora rozwiązań**i wybierz polecenie **Ustaw jako element startowy**.

   Plik wykonywalny jest oznaczony jako element startowy baza kodu i debugowanie **Start** przycisku tytuł zmiany w celu odzwierciedlenia nazwy pliku wykonywalnego.

   ![Dostosowany przycisk Start](media/customize-start-button.png)

   Po wybraniu **F5**, debuger uruchamia i zatrzymuje na dowolnym punkt przerwania może zostały skonfigurowane. Wszystkie znane debugera systemu windows są dostępne i funkcjonują prawidłowo.

### <a name="specify-arguments-for-debugging"></a>Określ argumenty do debugowania

Można określić argumenty wiersza polecenia przekazywane w celu debugowania w *launch.vs.json* pliku. Dodaj argumentów `args` tablicy, jak pokazano w poniższym przykładzie:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe"
    },
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe a1",
      "args": [ "a1" ]
    }
  ]
}
```

Po zapisaniu tego pliku, nazwa nowej konfiguracji pojawia się na liście rozwijanej debugowania i możesz wybrać je można uruchomić debugera. Można utworzyć wiele konfiguracje debugowania, według uznania.

![Listy rozwijanej konfiguracje debugowania](media/customize-debug-configurations.png)

> [!NOTE]
> `configurations` Tablicy właściwości w *launch.vs.json* są odczytywane z dwóch lokalizacji pliku&mdash;katalogiem głównym codebase i *.vs* katalogu. Jeśli występuje konflikt, priorytet znajduje się wartość *.vs\launch.vs.json*.

## <a name="define-workspace-settings-in-vsworkspacesettingsjson"></a>Definiowanie ustawień obszaru roboczego w VSWorkspaceSettings.json

Można określić ustawień ogólnych, które mogą mieć wpływ na zadania, a następnie uruchom w *VSWorkspaceSettings.json* pliku. Na przykład w przypadku definiowania `envVars` w *VSWorkspaceSettings.json*, Visual Studio dodaje określone zmienne środowiskowe poleceniami, które są uruchamiane zewnętrznie. Aby użyć tego pliku, należy utworzyć ją ręcznie.

## <a name="additional-settings-files"></a>Pliki dodatkowe ustawienia

Oprócz trzech *JSON* pliki w tym temacie opisano, Visual Studio również odczytuje ustawienia z niektóre dodatkowe pliki, jeśli istnieją w baza kodu.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual Studio odczytuje ograniczone ustawienia z pliku o nazwie *settings.json*, jeśli znajduje się w katalogu o nazwie *.vscode*. Ta funkcja jest dostępne w celu codebases, które wcześniej zostały opracowane w programie Visual Studio Code. Obecnie tylko ustawienie odczytywać *.vscode\settings.json* jest `files.exclude`, który filtruje pliki wizualnie w Eksploratorze rozwiązań i z niektóre narzędzia wyszukiwania.

Może mieć dowolną liczbę *.vscode\settings.json* pliki w baza kodu. Ustawienia z tego pliku do odczytu są stosowane do katalogu nadrzędnym *.vscode* i wszystkich jego podkatalogach.

### <a name="gitignore"></a>.gitignore

*.gitignore* sprawdzić Git, które pliki, aby zignorować używane są pliki; oznacza to, które pliki i katalogi nie chcesz zaewidencjonować. *.gitignore* plików są zwykle dołączone jako część codebase tak, aby ustawienia można udostępniać wszystkich deweloperów bazy kodu. Visual Studio odczytuje wzorce w *.gitignore* pliki, aby filtrować elementy wizualne i z niektórych wyszukiwania narzędzi.

Ustawienia są odczytywane z *.gitignore* plików są stosowane do katalogu nadrzędnego i jego podkatalogach.

## <a name="see-also"></a>Zobacz także

- [Opracuj kodu bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Otwórz Folder projektów dla języka C++](/cpp/ide/non-msbuild-projects)
- [CMake projektów w języku C++](/cpp/ide/cmake-tools-for-visual-cpp)
- [Odwołanie NMAKE](/cpp/build/nmake-reference)
- [Pisanie kodu w edytorze kodu i tekstu](../ide/writing-code-in-the-code-and-text-editor.md)