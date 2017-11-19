---
title: "Informacje dotyczące wiersza polecenia programu MSBuild | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, msbuild.exe
- MSBuild, command line reference
- msbuild.exe
ms.assetid: edaa65ec-ab8a-42a1-84cb-d76d5b2f4584
caps.latest.revision: "57"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 07beb4cfbc8acad0184ff93d12121699f3b27b03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-command-line-reference"></a>Informacje w wierszu polecenia programu MSBuild
Korzystając z programu MSBuild.exe tworzenia pliku projektu lub rozwiązania, mogą obejmować kilka przełączników, aby określić różne aspekty procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Argument|Opis|  
|--------------|-----------------|  
|`ProjectFile`|Tworzy obiekty docelowe w pliku projektu, który określisz. Jeśli nie określisz pliku projektu MSBuild wyszukuje bieżący katalog roboczy dla rozszerzenia nazwy pliku, który kończy się na "proj" i używa tego pliku. Można również określić plik rozwiązania Visual Studio dla tego argumentu.|  
  
## <a name="switches"></a>Przełączniki  
  
|Przełącznik|Krótka forma|Opis|  
|------------|----------------|-----------------|  
|/help|/? lub /h|Wyświetl informacje o użyciu. Polecenie jest przykładem:<br /><br /> `msbuild.exe /?`|  
|detailedsummary|/ ds|Pokaż szczegółowe informacje na koniec dziennika kompilacji o konfiguracji, które zostały utworzone i jak były planuje węzłów.|  
|/ ignoreprojectextensions:`extensions`|/ Ignoruj:`extensions`|Ignoruj określonych rozszerzeń przy określaniu, który plik projektu do kompilacji. Użyj średnika lub przecinka do rozdzielania wielu rozszerzeń, jak przedstawiono na poniższym przykładzie:<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/maxcpucount [:`number`]|/m [:`number`]|Określa maksymalną liczbę równoczesnych procesów do użycia podczas tworzenia. Jeśli ten przełącznik nie zostanie uwzględniony, wartość domyślna to 1. Jeśli dołączysz ten przełącznik bez określenia wartości MSBuild wymaga użycia do liczby procesorów w komputerze. Aby uzyskać więcej informacji, zobacz [tworzenie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Poniższy przykład powoduje, że program MSBuild aby kompilować przy użyciu trzech procesów programu MSBuild, dzięki czemu trzy projektów do kompilacji w tym samym czasie:<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/ noautoresponse|/ noautorsp|Nie dołączaj automatycznie pliki MSBuild.rsp.|  
|/nodeReuse:`value`|/nr:`value`|Włącza lub wyłącza ponowne używanie węzłów programu MSBuild. Można określić następujące wartości:<br /><br /> -   **Wartość true,**. Węzły pozostać po zakończeniu kompilacji, tak aby kolejnych kompilacjach można używać ich (ustawienie domyślne).<br />-   **FALSE**. Węzły nie pozostać po zakończeniu kompilacji.<br /><br /> Węzeł odnosi się do projektu, który jest wykonywany. Jeśli dołączysz **/maxcpucount** przełącznika, wiele węzłów można wykonywać jednocześnie.|  
|/nologo||Nie wyświetlaj transparentu lub komunikat o prawach autorskich.|  
|<a name="preprocess"></a>/ Przetwarzanie wstępne [:`filepath`]|/PP [:`filepath`]|Utwórz plik projektu jeden, zagregowany przez ze śródwierszowaniem wszystkich plików, zaimportowane podczas kompilacji, z ich granic. Ten przełącznik może zostać użyty do łatwiej ustalić, które pliki są importowane, z którym zaimportowane pliki i które pliki przyczyniają się do kompilacji. Korzystając z tego przełącznika, projekt nie jest skompilowany.<br /><br /> Jeśli określisz `filepath`, plik projektu zagregowane jest dane wyjściowe do pliku. W przeciwnym razie dane wyjściowe zostanie wyświetlona w oknie konsoli.<br /><br /> Aby uzyskać informacje o sposobie używania `Import` elementu, aby wstawić plik projektu do innego pliku projektu, zobacz [Import — Element (MSBuild)](../msbuild/import-element-msbuild.md) i [porady: Użyj tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|  
|/Property:`name`=`value`|/ p:`name`=`value`|Ustawianie lub zastąpienie określonej właściwości poziom projektu, gdzie `name` jest nazwą właściwości i `value` jest wartość właściwości. Określ każdej właściwości oddzielnie, lub użyj średnika lub przecinka aby oddzielić wiele właściwości, jak przedstawiono na poniższym przykładzie:<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/ target:`targets`|/ t:`targets`|Tworzenie określone elementy docelowe w projekcie. Określ każdego obiektu docelowego oddzielnie, lub użyj średnika lub przecinka do oddzielania wielu elementów docelowych, jak przedstawiono na poniższym przykładzie:<br /><br /> `/target:Resources;Compile`<br /><br /> Jeśli określisz wszystkich obiektów docelowych za pomocą tego przełącznika są uruchamiane zamiast obiektów docelowych w `DefaultTargets` atrybutu w pliku projektu. Aby uzyskać więcej informacji, zobacz [kolejność kompilacji docelowej](../msbuild/target-build-order.md) i [jak: Określ którego docelowego do kompilacji pierwszej](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Element docelowy jest grupą zadań. Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md).|  
|/toolsversion:`version`|/TV:`version`|Określa wersję zestawu narzędzi do użycia, aby skompilować projekt, jak przedstawiono na poniższym przykładzie:`/toolsversion:3.5`<br /><br /> Za pomocą tego przełącznika, możesz skompilować projekt i określ wersję, która różni się od wersji, który jest określony w [Project — Element (MSBuild)](../msbuild/project-element-msbuild.md). Aby uzyskać więcej informacji, zobacz [Zastępowanie ustawienia ToolsVersion](../msbuild/overriding-toolsversion-settings.md).<br /><br /> Dla programu MSBuild 4.5, można określić następujące wartości `version`: 2.0, 3.5 lub 4.0. Jeśli określisz 4.0, `VisualStudioVersion` kompilacji właściwość określa, które sub-zestaw narzędzi do użycia. Aby uzyskać więcej informacji, zobacz sekcję podzestawach [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).<br /><br /> Zestaw narzędzi składa się z zadań, elementy docelowe i narzędzi, które są używane do tworzenia aplikacji. Narzędzia te zawierają kompilatory, takie jak csc.exe i vbc.exe. Aby uzyskać więcej informacji na temat procesami, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [standardowe i niestandardowe konfiguracje zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md), i [przeznaczanie dla wielu platform](../msbuild/msbuild-multitargeting-overview.md). **Uwaga:** wersję zestawu narzędzi nie jest taka sama jak platformy docelowej, który jest wersją programu .NET Framework, na którym projekt korzysta z wbudowanej Uruchom. Aby uzyskać więcej informacji, zobacz [platformy docelowej i platformy docelowej](../msbuild/msbuild-target-framework-and-target-platform.md).|  
|/ validate: [`schema`]|/Val [`schema`]|Sprawdź poprawność pliku projektu i, jeśli weryfikacja zakończy się powodzeniem, skompiluj projekt.<br /><br /> Jeśli nie określisz `schema`, projekt jest weryfikowana pod kątem schemat domyślny.<br /><br /> Jeśli określisz `schema`, projektu jest weryfikowane względem schematu, który określisz.<br /><br /> Następujące ustawienie jest przykładem:`/validate:MyExtendedBuildSchema.xsd`|  
|/ verbosity:`level`|/ v:`level`|Określa ilość informacji do wyświetlenia w dzienniku kompilacji. Każdy rejestrator Wyświetla zdarzenia na podstawie poziomu szczegółowości dla tego rejestratora.<br /><br /> Można określić następujących poziomów szczegółowości: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.<br /><br /> Następujące ustawienie jest przykładem:`/verbosity:quiet`|  
|/ Version|/ VER|Wyświetl tylko informacje o wersji. Projekt nie jest skompilowany.|  
|@`file`||Wstaw przełączniki wiersza polecenia z pliku tekstowego. Jeśli masz wiele plików, możesz je określić osobno. Aby uzyskać więcej informacji, zobacz [pliki odpowiedzi](../msbuild/msbuild-response-files.md).|  
  
### <a name="switches-for-loggers"></a>Przełączniki rejestratorów  
  
|Przełącznik|Krótka forma|Opis|  
|------------|----------------|-----------------|  
|/ consoleloggerparameters:<br /><br /> `parameters`|/CLP:`parameters`|Przekaż parametry, które określisz do rejestratora konsoli, który zawiera informacje o kompilacji w oknie konsoli. Można określić następujące parametry:<br /><br /> -   **PerformanceSummary**. Pokaż jest zużywany czas w zadań, elementy docelowe i projekty.<br />-   **Podsumowanie**. Pokaż błąd i ostrzeżenie podsumowanie na końcu.<br />-   **NoSummary**. Nie pokazuj błąd i ostrzeżenie podsumowanie na końcu.<br />-   **ErrorsOnly**. Pokaż tylko błędy.<br />-   **WarningsOnly**. Pokaż tylko ostrzeżenia.<br />-   **NoItemAndPropertyList**. Nie pokazuj listę elementów i właściwości, które będą widoczne na początku każdej kompilacji projektu, jeśli ustawiono poziom szczegółowości `diagnostic`.<br />-   **ShowCommandLine**. Pokaż `TaskCommandLineEvent` wiadomości.<br />-   **ShowTimestamp**. Pokaż sygnatura czasowa jako prefiksu do wiadomości.<br />-   **ShowEventId**. Pokaż Identyfikatora zdarzenia dla każdego uruchomionego zdarzenia gotowego zdarzenia i komunikatu.<br />-   **ForceNoAlign**. Tekst, który ma rozmiar buforu konsoli nie są wyrównywane.<br />-   **DisableConsoleColor**. Użyj kolorów konsoli domyślnego dla wszystkich wiadomości rejestrowania.<br />-   **DisableMPLogging**. Wyłącz styl wieloprocesorowych rejestrowania danych wyjściowych w trybie z systemem innym niż wieloprocesorowych.<br />-   **EnableMPLogging**. Włącz styl wieloprocesorowych rejestrowania, nawet wtedy, gdy działa w trybie z systemem innym niż wieloprocesorowych. Ten styl rejestrowanie jest domyślnie włączone.<br />-   **Poziom szczegółowości**. Zastąpienie **/verbosity** ustawienie dla tego rejestratora.<br /><br /> Użyj średnika lub przecinka do rozdzielania wielu parametrów, jak przedstawiono na poniższym przykładzie:<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/distributedFileLogger|/DFL|Dane wyjściowe kompilacji w każdym węźle MSBuild własną w pliku dziennika. Położenie początkowe tych plików jest to katalog bieżący. Domyślnie pliki są nazywane "MSBuild*ID. węzła*.log". Można użyć **/fileloggerparameters** przełącznik, aby określić lokalizację plików i inne parametry fileLogger.<br /><br /> Jeśli nazwa pliku dziennika przy użyciu **/fileloggerparameters** przełącznika rozproszonej rejestratora użyje nazwy jako szablon i Dołącz identyfikator węzła tej nazwy, podczas tworzenia pliku dziennika dla każdego węzła.|  
|/distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|/DL:`central logger`*`forwarding logger`|Zdarzenia dziennika z MSBuild dołączanie wystąpienia rejestratora różnych do każdego węzła. Aby określić wiele rejestratorów, określ osobno każdy rejestrator.<br /><br /> Aby określić rejestrator, użyj składni rejestratora. Rejestrator składni, zobacz **/logger** przełącznika poniżej.<br /><br /> W poniższych przykładach pokazano sposób użycia tej opcji:<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/fileLogger<br /><br /> *[numer]*|/FL [`number`]|Rejestrowanie danych wyjściowych kompilacji do jednego pliku w bieżącym katalogu. Jeśli nie określisz `number`, plik wyjściowy nosi nazwę msbuild.log. Jeśli określisz `number`, plik wyjściowy nosi nazwę msbuild`n`.log, gdzie n to `number`. `Number`może być cyfrą z zakresu od 1 do 9.<br /><br /> Można użyć **/fileloggerparameters** przełącznik, aby określić lokalizację pliku oraz innych parametrów fileLogger.|  
|/ fileloggerparameters: [numer]<br /><br /> `parameters`|/FLP: [ `number`]`parameters`|Określa wszelkie dodatkowe parametry rejestratora plików i rejestratora plików rozproszonych. Obecność tego parametru oznacza, że odpowiednie /**filelogger [**`number`**]** ma przełącznika. `Number`może być cyfrą z zakresu od 1 do 9.<br /><br /> Można użyć wszystkich parametrów, które są wymienione **/consoleloggerparameters**. Można także użyć co najmniej jeden z następujących parametrów:<br /><br /> -   **Plik dziennika**. Ścieżka do pliku dziennika, w którym są zapisywane w dzienniku kompilacji. Rejestratora plików rozproszonych prefiksy tę ścieżkę do nazwy jej pliki dziennika.<br />-   **Dołącz**. Określa, czy dziennik kompilacji jest dołączany do pliku dziennika lub zastąpiony. Po ustawieniu przełącznika dziennika kompilacji jest dołączany do pliku dziennika. Jeśli nie ma przełącznika, zawartość istniejącego pliku dziennika zostaną zastąpione.<br />     Jeśli dołączysz przełącznik dołączania, niezależnie od tego, czy jest ustawiona na wartość true lub false, jest dołączany dziennika. Jeśli nie ma przełącznika append, dziennik jest zastępowany.<br />     W takim przypadku plik jest zastępowany:`msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     W takim przypadku jest dołączany plik:`msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     W takim przypadku jest dołączany plik:`msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Kodowanie**. Określa kodowanie pliku (na przykład UTF-8, Unicode i ASCII).<br /><br /> Poniższy przykład generuje oddzielnych plików dziennika dla ostrzeżeń i błędów:<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> W poniższych przykładach pokazano innych możliwości:<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|/binaryLogger [: [plik dziennika =]`output.binlog`[; ProjectImports = [None, osadzić, ZipFile]]]|/BL|Serializuje wszystkich zdarzeń kompilacji do skompresowanego pliku binarnego. Domyślnie plik znajduje się w bieżącym katalogu i o nazwie `msbuild.binlog`. Dziennik binarny jest szczegółowy opis procesu kompilacji, które później mogą być używane do rekonstrukcji dzienniki tekstowe i używane przez inne narzędzia analizy. Dziennik binarny jest zwykle mniejsze niż najbardziej szczegółowy dziennik tekstowy w poziomie Diagnostyka x 10-20, ale zawiera więcej informacji.<br /><br />Binarny rejestratora domyślnie zbiera tekst źródłowy pliki projektu, w tym wszystkie projekty zaimportowane i pliki docelowej podczas kompilacji. Opcjonalny `ProjectImports` przełącznika steruje zachowaniem w tym:<br /><br /> -   **ProjectImports = Brak**. Nie zbieraj importów projektu.<br /> -   **ProjectImports = osadzić**. Osadź importów projektu w pliku dziennika (ustawienie domyślne).<br /> -   **ProjectImports = ZipFile**. Zapisz pliki projektu do `output.projectimports.zip` gdzie `output` jest tej samej nazwie jak nazwa pliku dziennik binarny.<br /><br />Ustawieniem domyślnym dla ProjectImports jest osadzania.<br />**Uwaga**: Rejestrator nie zbiera takich jak pliki źródłowe z systemem innym niż MSBuild `.cs`, `.cpp` itp.<br />A `.binlog` plik może być "odtwarzane" przekazując go do `msbuild.exe` jako argument zamiast projektu/rozwiązania. Inne rejestratorów będą otrzymywać informacje zawarte w pliku dziennika, tak, jakby oryginalnego kompilacji został sytuacji. Więcej o dziennik binarny i jego użycia w: https://github.com/Microsoft/msbuild/wiki/Binary-Log <br /><br />**Przykłady**:<br /> -   `/bl`<br /> -    `/bl:output.binlog`<br /> -   `/bl:output.binlog;ProjectImports=None`<br /> -   `/bl:output.binlog;ProjectImports=ZipFile`<br /> -   `/bl:..\..\custom.binlog`<br /> -   `/binaryLogger`|
|/Logger:<br /><br /> `logger`|/ l: wyświetlenie`logger`|Określa Rejestrator służące do rejestrowania zdarzeń z programu MSBuild. Aby określić wiele rejestratorów, określ osobno każdy rejestrator.<br /><br /> Należy użyć następującej składni dla `logger`:`[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Należy użyć następującej składni dla `LoggerClass`:`[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Nie masz w celu określenia klasy rejestratora, jeśli zestaw zawiera dokładnie jeden rejestratora.<br /><br /> Należy użyć następującej składni dla `LoggerAssembly`: `{``AssemblyName``[,``StrongName``] &#124;``AssemblyFile``}`<br /><br /> Rejestrator parametry są opcjonalne i są przekazywane do rejestratora, dokładnie tak, jak wprowadzić je.<br /><br /> W poniższych przykładach użyto **/logger** przełącznika.<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolelogger|/ noconlog|Wyłącz domyślnego rejestratora konsoli, a nie Rejestruj zdarzenia do konsoli.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy `rebuild` docelowy `MyProject.proj` projektu.  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>Przykład  
 MSBuild.exe służy do wykonywania bardziej złożonych kompilacji. Na przykład służy ona do kompilacja określonych obiektów docelowych określonych projektów w rozwiązaniu. Poniższy przykład odtwarza projektu `NotInSolutionFolder` i czyści projektu `InSolutionFolder`, która znajduje się w `NewFolder` folder rozwiązania.  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Wspólne właściwości projektów MSBuild](../msbuild/common-msbuild-project-properties.md)
