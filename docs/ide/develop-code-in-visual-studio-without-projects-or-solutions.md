---
title: "Opracuj kodu w programie Visual Studio bez projekty i rozwiązania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 252f09a8a2322bca4f94b9d631ca2c6da6b14824
ms.sourcegitcommit: 94162a6b0440312cd71bc0c512daef9f122550f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2018
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Opracuj kodu w programie Visual Studio bez projektów i rozwiązań

W Visual Studio 2017 r możesz otworzyć kodu z niemal dowolnego typu na podstawie katalogu projektu do programu Visual Studio bez konieczności plik rozwiązania lub projektu. Oznacza to, można, na przykład znaleźć projektu kodu na Git, klonowanie i otworzyć go bezpośrednio w programie Visual Studio i rozpocząć tworzenie bez konieczności tworzenia rozwiązania lub projektu.  

Nie tylko możesz edytować kod i skompiluj go w programie Visual Studio, można również przejść za pomocą kodu (na przykład za pomocą przejdź do polecenia). Kod będzie wyświetlany z kolorowanie składni, a w wielu przypadkach obejmują podstawowe uzupełnianie i debugowania, wraz z punktów przerwania. W przypadku niektórych języków będzie zawierać zwiększające funkcjonalność. Zobacz [utworzyć przenośny, niestandardowego edytora ustawień](create-portable-custom-editor-options.md) Aby uzyskać więcej informacji.  

## <a name="open-code-anywhere"></a>Otwórz kod dowolnego miejsca

Kod można otworzyć w programie Visual Studio w następujący sposób:  

- Na pasku menu programu Visual Studio wybierz **pliku**, **Otwórz**, **folderu**, następnie przejdź do lokalizacji kodu.  

- W menu kontekstowym (kliknij prawym przyciskiem myszy) do folderu zawierającego kod, wybierz **Otwórz w programie Visual Studio** polecenia.  

- Wybierz **Otwórz Folder** łącza w Visual Studio — strona początkowa.  

- Otwórz kod sklonować z repozytorium GitHub.  

### <a name="to-open-code-from-a-cloned-github-repo"></a>Aby otworzyć kodu z sklonowanego repozytorium GitHub

Poniższy przykład pokazuje, jak można sklonować repozytorium GitHub, a następnie otwórz jego kodu w programie Visual Studio. Aby wykonać tę procedurę, musi mieć konto usługi GitHub i Git dla systemu Windows zainstalowanych w systemie. Zobacz [utworzeniem nowego konta usługi GitHub](https://help.github.com/articles/signing-up-for-a-new-github-account/) i [Git dla systemu Windows](https://git-for-windows.github.io/) Aby uzyskać więcej informacji.  

1. Przejdź do repozytorium, które chcesz sklonować w witrynie GitHub.  

1. Wybierz **klonowania lub pobrać** przycisk, a następnie wybierz pozycję **Kopiuj do Schowka** przycisk w menu rozwijanym, aby skopiować bezpiecznego adresu URL dla repozytorium GitHub.  

  ![Przycisk powielania GitHub](./media/VSIDE_Code_Clone.png)

    > [!NOTE]
    >  Gdy masz również opcję, aby otworzyć projekt na pulpicie lub pobrać plik zip projektu, w tym przykładzie pokazano, jak klonowanie repozytorium przy użyciu metody bezpiecznego adresu URL.

1. W programie Visual Studio, wybierz **Team Explorer** kartę, aby otworzyć program Team Explorer.  

1. W programie Team Explorer w obszarze **lokalnego repozytoriów Git** wybierz **klonowania** polecenia, a następnie wklej adres URL strony GitHub w polu tekstowym.  

  ![Klonowanie projektu](./media/VSIDE_Code_Clone2.png)

1. Wybierz **klonowania** przycisk sklonować pliki projektu do lokalnego repozytorium Git. W zależności od rozmiaru repozytorium ten proces może potrwać kilka minut.  

1. Po repozytorium ma został sklonowany w systemie, w programie Team Explorer, wybierz **Otwórz** polecenia w menu kontekstowym (kliknij prawym przyciskiem myszy) nowo sklonowanego repozytorium.  

  ![Sklonowanego repozytorium](./media/VSIDE_Code_Clone3.png)

1. Wybierz **Pokaż widok folderu** polecenie, aby wyświetlić pliki w Eksploratorze rozwiązań  

  ![Pokaż widok folderu](./media/VSIDE_Code_Clone3_show.png)

  Można teraz przeglądanie folderów i plików w repozytorium sklonowany i wyświetlić i wyszukiwanie kodu w edytorze kodu programu Visual Studio z kolorowanie składni i inne funkcje.

    ![Wyszukiwanie kodu sklonowany projektu](./media/VSIDE_Code_Clone4.png)  

|         |         |
|---------|---------|
|  ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo")  |    [Obejrzyj film](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171) dotyczące klonowania i otworzyć kodu z repozytorium GitHub, w programie Visual Studio. |

## <a name="debug-your-code"></a>Debugowanie kodu

Można debugować kodu w programie Visual Studio bez projekt lub rozwiązanie. Aby debugować niektórych języków, konieczne może być Określ prawidłowe *uruchamiania pliku* w projekcie kodu, takie jak skrypt, plik wykonywalny lub projektu. Visual Studio działa to określony kod najpierw podczas debugowania kodu.  

Pole listy rozwijanej obok przycisku Start na pasku narzędzi zawiera wszystkie wykryte Visual Studio, a także elementów, które można wybrać w folderze elementy startowe.  

![Przycisk Uruchom](./media/VSIDE_Code_Run_Button.png)  

Visual Studio automatycznie rozpoznaje projektów, ale konieczne można w sposób jawny wybrany przez użytkownika jako element startowy zanim pojawią się na liście skryptów (na przykład Python i JavaScript). Ponadto niektóre elementy startowe, takich jak program MSBuild i CMake, może mieć wielu konfiguracji kompilacji, które są wyświetlane na liście rozwijanej przycisk Uruchom.  

Program Visual Studio obsługuje obecnie debugowanie dla następujących języków:  

- Node.js  

- Python  

- Projekty oparte na MSBuild (C#, VB, C++)  

- Każdego pliku wykonywalnego z plików PDB (Python debugera).  

### <a name="to-debug-nodejs-and-python"></a>Debugowanie Node.js i Python:

1. Zainstaluj Node.js lub Python Tools lub program Visual Studio 2017 i środowiska uruchomieniowego Node.js.  

1. W menu kontekstowym pliku JavaScript w Eksploratorze rozwiązań wybierz **Ustaw jako element startowy** polecenia.  

1. Wybierz **F5** klawisz, aby rozpocząć debugowanie.  

### <a name="to-debug-msbuild-projects"></a>Debugowanie projektów MSBuild

1. W menu programu Visual Studio wybierz **debugowania**. Z menu rozwijanego wybierz projekt lub projekt lub plik, który ma być wyświetlany jako element startowy w Eksploratorze rozwiązań.  

1. Wybierz **F5** klawisz, aby rozpocząć debugowanie.  

### <a name="to-debug-executable-files"></a>Aby debugować pliki wykonywalne

1. W menu programu Visual Studio wybierz **debugowania**. Z menu rozwijanego wybierz projekt lub projekt lub plik, który ma być wyświetlany jako element startowy w Eksploratorze rozwiązań.  

1. Wybierz **F5** klawisz, aby rozpocząć debugowanie.  

## <a name="enable-custom-build-tools"></a>Włącz niestandardowe narzędzia kompilacji

Visual Studio potrafi uruchamianie wielu różnych językach, ale nie wiadomo, jak uruchomić wszystkie. Jeśli Visual Studio wie, jak uruchomić danego języka, można od razu wykonywania kodu. Jeżeli zostanie podjęta próba uruchomienia kodu programu Visual Studio nie może ustalić, sposobu jego uruchamiania, pasek informacyjny monituje można wyznaczyć plik w Twojej codebase do działania jako element startowy.  

Jeśli codebase używa narzędzia niestandardowej kompilacji, które nie rozpoznaje programu Visual Studio, jednak następnie prawdopodobnie nie można uruchomić i debugowania kodu w programie Visual Studio, dopóki nie zostanie ukończona pewnych dodatkowych czynności. Musisz określić typ prawidłowy plik wykonywalny, takich jak kompilatora, oraz wszelkie niestandardowe parametry i argumenty wymagane przez język. Aby włączyć tę opcję, program Visual Studio udostępnia *zadania kompilacji*. Można utworzyć zadania kompilacji, aby określić wszystkie elementy potrzebne języka Aby skompilować i uruchomić kodu.  

Można również utworzyć kompilacji dowolnego zadania, które można wykonać prawie wszystko, co ma. Na przykład można utworzyć zadania do wyświetlania zawartości folderu lub zmiany nazwy pliku. Alternatywnie można utworzyć więcej docelowych niestandardowej kompilacji zadań wykonywanie czynności takich jak kompilacji i skompilowanie projektu przy użyciu określonych argumentów. Poniższe kroki przedstawiają sposób tworzenia obu typów zadań kompilacji.  

#### <a name="to-create-an-arbitrary-build-task"></a>Aby utworzyć zadanie dowolnego kompilacji

1. Wybierz plik lub folder projektu w Eksploratorze rozwiązań, w którym zadanie ma i w pliku lub folderu menu kontekstowe (kliknij prawym przyciskiem myszy), **skonfigurować zadania**.  

  ![Konfigurowanie zadań](./media/VSIDE_Code_Config_Task.png)

  Wybieranie **skonfigurować zadania** otwiera plik o nazwie tasks.vs.json. Jeśli ten plik nie istnieje, jest tworzony. Ten plik zawiera zadania kompilacji dla wybranego pliku lub folderu.  

  ![Plik Tasks.VS.JSON](./media/VSIDE_Code_Tasks_JSON.png)

1. Dodaj następujące zadania kompilacji do tasks.vs.json. W tym przykładzie dodamy prostych zadań o nazwie "Listy danych wyjściowych" listę plików i podfolderów wybranego folderu, w oknie danych wyjściowych. (Nowe zadanie powinni zostać dodani w istniejącej tablicy "zadania").  

  ```xml
      {
        "taskName": "List outputs",
        "appliesTo": "*",
        "type": "command",
        "command": "${env.COMSPEC}",
        "args": [
          "dir ${outDir}"
        ]
      },
  ```
  Zadania kompilacji pełne powinna wyglądać następująco.  

  ![Zadania kompilacji dowolnego](./media/VSIDE_Code_Tasks_ArbTask.png)

1. Zapisz projekt.  

1. Otwórz menu kontekstowe dla wybranego folderu. Powinny pojawić się nowe zadanie dowolnego kompilacji są wyświetlane u dołu menu kontekstowego.  

  ![Polecenie zadań dowolnego kompilacji](./media/VSIDE_Code_Tasks_ArbTask2.png)

1. Wybierz nowy **listy danych wyjściowych** polecenie do wykonania zadania.  

### <a name="to-create-a-custom-build-task"></a>Aby utworzyć zadanie niestandardowej kompilacji

W tej procedurze dodamy dwa zadania niestandardowej kompilacji, których nMake kompilacji i czyszczenie kodu.  

1. Wybierz plik projektu w Eksploratorze rozwiązań, które chcesz wyznaczyć element startowy. W menu kontekstowym (kliknij prawym przyciskiem myszy) pliku, wybierz **skonfigurować zadania**.  

  ![Polecenia zadania niestandardowej kompilacji](./media/VSIDE_Code_Tasks_CustTask1.png)

1. Dodaj następujące zadania kompilacji do tasks.vs.json. W tym przykładzie dodamy dwa zadania: jedną o nazwie "pliku reguł programu make kompilacji", która używa polecenia nMake, aby skompilować projekt, innych o nazwie czyszczenia pliku reguł programu make które wywołuje polecenie nMake z argumentem "Wyczyść". Te zadania, należy dodać w ramach istniejącej tablicy "zadania". (Należy pamiętać, że są one tylko zadania kompilacji przykład. Dla nich faktycznie pracę, musisz mieć obciążenia, który zawiera [nNake](/cpp/build/nmake-reference) zainstalowanych w systemie.)

  ```xml
  {
  "taskName": "makefile-build",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "build",
  "command": "nmake"
  },
  {
  "taskName": "makefile-clean",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "clean",
  "command": "nmake",
  "args": [
    "clean"
    ]
  },
  ```
  Zadania ukończone niestandardowej kompilacji powinien wyglądać następująco.  

  ![Zadanie niestandardowej kompilacji](./media/VSIDE_Code_Tasks_CustTask2.png)

1. Zapisz projekt.  

1. Otwórz menu kontekstowe dla wybranego pliku. Nowe zadania kompilacji niestandardowej powinna pojawić się w środku menu kontekstowego.  

  ![Polecenia zadania niestandardowej kompilacji](./media/VSIDE_Code_Tasks_CustTask3.png)

  > [!NOTE]
  > Polecenia są wyświetlane w obszarze **skonfigurować zadania** polecenia ze względu na ich `contextType` ustawień; "kompilacji" i "Wyczyść" są poleceń kompilacji, aby były wyświetlane w sekcji kompilacji w środku menu kontekstowego.  

  Teraz, niestandardowych poleceń kompilacji został skojarzony z plikiem, można wyznaczyć plik jako element startowy.  

1. W menu kontekstowym pliku, wybierz **Ustaw jako element startowy**.  

  ![Polecenia zadania niestandardowej kompilacji](./media/VSIDE_Code_Tasks_CustTask4.png)

1. Na pasku narzędzi wybierz strzałkę listy rozwijanej obok przycisku Start. Element startowy jest teraz wyświetlany jako opcja.  

  ![Polecenia zadania niestandardowej kompilacji](./media/VSIDE_Code_Tasks_CustTask5.png)

Teraz możesz **Start** przycisk lub **F5** klawisz, aby uruchomić baza kodu. Możesz edytować i debugowania baza kodu w programie Visual Studio, mimo że program Visual Studio nie rozpoznaje narzędzia kompilacji bazy kodu. Zostaną wyświetlone dane wyjściowe z zadania kompilacji w **dane wyjściowe** okna i błędy kompilacji są wyświetlane w **listy błędów**. Tasks.vs.json kompilacji pozamałżeńskie pliku zadań narzędzi używanych przez baza kodu do kompilacji z pętli wewnętrzny programowania Visual Studio niestandardowe.  

Zadania kompilacji niestandardowej można dodawać do pojedynczych plików lub wszystkich plików określonego typu. Na przykład pliki pakietu NuGet można skonfigurować do zadania "Przywracanie Packages" lub wszystkich plików źródłowych można skonfigurować tak, aby zadanie analizy statycznej, takich jak linter dla wszystkich plików js.  

Program Visual Studio obsługuje VSCode `$variable` podstawienia w folderze głównym tasks.vs.json oprócz zmiennych środowiskowych (takie jak `$env.var`) lub kluczy.  

## <a name="specify-build-output"></a>Określ dane wyjściowe kompilacji

Jeśli projekt musi być skompilowany, możesz dodać dodatkowe tagu o nazwie `output` do pliku tasks.vs.json. Oto przykład.  

`"output": "${workspaceRoot}\\bin\\hellomake.exe"`

Określanie lokalizacji danych wyjściowych powiadamia gdzie można znaleźć w danych wyjściowych kompilacji projektu programu Visual Studio.  

## <a name="tasksvsjson-file-location"></a>Lokalizacja pliku Tasks.VS.JSON

Domyślnie plik tasks.vs.json znajduje się w ukrytym folderze o nazwie `.vs`. Aby wyświetlić ukryte pliki w programie Visual Studio, wybierz **Pokaż wszystkie pliki** przycisk na pasku narzędzi Eksplorator rozwiązań.

![Polecenie zadań dowolnego kompilacji](./media/VSIDE_Code_Tasks_FileLocation.png)

Plik tasks.vs.json jest ukryty, ponieważ większość użytkowników przeważnie nie chcesz sprawdź go do kontroli źródła. Jednak jeśli chcesz mieć możliwość sprawdzenia go do kontroli źródła, przeciągnij plik do katalogu głównego projektu gdzie będą widoczne.  

Inne pliki JSON może znajdować się w folderze .vs, ale są jedynymi osobami, które należy przenieść plik tasks.vs.json i plik launch.vs.json (jeśli jest). Plik launch.vs.json konfiguruje debuger programu Visual Studio podczas pliku tasks.vs.json konfiguruje kompilacji w programie Visual Studio.  

## <a name="see-also"></a>Zobacz także

[Pisanie kodu w edytorze kodu i tekstu](../ide/writing-code-in-the-code-and-text-editor.md)
