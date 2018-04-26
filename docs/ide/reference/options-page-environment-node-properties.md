---
title: Strona opcji, środowisko — Właściwości węzła
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio], controlling Tools Options
- Tools Options settings, Environment node properties
ms.assetid: 26dca41f-91fc-4ca7-9103-3da402baa1d5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ba201b4518b350a96c4c4057f6945d24ea603f0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="options-page-environment-node-properties"></a>Strona opcji, środowisko — Właściwości węzła
W tym dokumencie opisano stron (lub kolekcji właściwości) które są skojarzone z **środowiska** kategorii, `DTE.Properties("Environment", <Property Page>)`, z **opcje** okno dialogowe. Tytuł każdego podsekcji to wywołanie, które umożliwia dostęp do właściwości kolekcji, a tabeli w każdym podsekcja zawiera listę właściwości w kolekcji.

## <a name="general"></a>Ogólne
 `DTE.Properties("Environment", "General")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|ShowStatusBar|Get/Set (wartość logiczna)|Określa, czy pasek stanu jest widoczny.|
|WindowMenuContainsNItems|Pobierz/Ustaw (Short)|Określa, jak okna dokumentów znajdują się w dolnej części menu systemu Windows.|
|MRUListContainsNItems|Pobierz/Ustaw (Short)|Określa, ile plików wyświetlane w podmenu "Ostatnio używanych".|
|Animacji|Get/Set (wartość logiczna)|Określa, czy zintegrowane środowisko programistyczne (IDE) używa animacji na pasku stanu.|
|AnimationSpeed|Pobierz/Ustaw (Short)||
|AutoAdjustExperience|Get/Set (wartość logiczna)|Automatycznie dostosowuje środowisko visual w zależności od wydajności klienta.|
|RichClientExperienceOptions|Get/Set (Wyliczenie)|Włącza bogate doświadczenia wizualne z wartościami w <xref:EnvDTE100.vsRichClientExperienceOptions>.|
|CloseButtonActiveTabOnly|Get/Set (wartość logiczna)|Określa, czy **Zamknij** przycisk jest wyświetlany tylko na karcie aktywne.|
|AutohidePinActiveTabOnly|Get/Set (wartość logiczna)|Określa, czy **automatyczne ukrywanie** przycisk dotyczy tylko aktywnej karty.|

## <a name="add-inmacros-security"></a>Dodaj w/makra zabezpieczeń
 `DTE.Properties("Environment", "AddinMacrosSecurity")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|MacrosEnabled|Get/Set (wartość logiczna)|Zezwala na uruchamianie makr.|
|AddinsEnabled|Get/Set (wartość logiczna)|Umożliwia dodatki do załadowania.|
|LoadAddinsFromTheWeb|Get/Set (wartość logiczna)|Umożliwia dodatki załadować z adresu URL w sieci Web.|

## <a name="documents"></a>Dokumenty
 `DTE.Properties("Environment", "Documents")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|ReuseSavedActiveDocWindow|Get/Set (wartość logiczna)|Określa, czy otwieranie nowego pliku ponownie bieżące okno dokumentu, jeśli bieżący dokument zostanie zapisany. `false` oznacza, że zawsze otwieraj dla każdego dokumentu otworzyć nowe okno dokumentu.|
|DetectFileChangesOutsideIDE|Get/Set (wartość logiczna)|Określa, czy środowisko automatycznie ładuje ponownie pliki otwarte w IDE, gdy system operacyjny powiadamia IDE pliki zostały zmienione na dysku.|
|AutoloadExternalChanges|Get/Set (wartość logiczna)|Określa, czy wykrył, że zewnętrzne zmiany na otwieranie dokumentów automatycznie załadować ponownie zmodyfikowany plik, jeśli otwartego dokumentu nie jest modyfikowany. Jeśli otwarty dokument zostanie zmodyfikowany, a ta właściwość jest `true`, a następnie monituje IDE, jak gdyby ta właściwość `false`.|
|InitializeOpenFileFromCurrentDocument|Get/Set (wartość logiczna)|Określa, czy <xref:EnvDTE.DTEClass.OpenFile%2A> polecenia nasiona nazwy katalogów i plików z ostatnich dokumentów aktywnych lub z ostatnim miejscu otworzyć plik.|
|MiscFilesProjectSavesLastNItems|Pobierz/Ustaw (Short)|Określa, jak wiele plików rekordy z projektu różne pliki. W związku z tym widać, co ostatnio otwartym jako różne pliku na dysku obok używania IDE.|
|ShowMiscFilesProject|Get/Set (wartość logiczna)|Określa, czy jest wyświetlany projektu różne pliki.|
|CheckForConsisentLineEndings|Get/Set (wartość logiczna)|Sprawdza spójność zakończenia wierszy przy ładowaniu pliku.|
|SaveDocsAsUnicodeWhenDataLoss|Get/Set (wartość logiczna)|Zapisuje dokumenty w formacie Unicode, gdy nie można zapisać danych w stronie kodowej.|
|DontShowGlobalUndoChangeLossDialog|Get/Set (wartość logiczna)|Wyświetli ostrzeżenie, gdy globalne cofanie modyfikuje inne pliki edytowany.|
|AllowEditingReadOnlyFiles|Get/Set (wartość logiczna)|Umożliwia edytowanie plików tylko do odczytu, ale zapewnia ostrzeżenie po próba je zapisać.|
|DocumentDockPreference|Get/Set (Wyliczenie)|<xref:EnvDTE100.vsDocumentDockPreferenceOptions>. Pozycja w karcie również w celu wstawienia otwartego dokumentu.|

## <a name="extension-manager"></a>Menedżer rozszerzeń
 `DTE.Properties("Environment", "ExtensionManager")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|EnableAdminExtensions|Get/Set (wartość logiczna)|Ładuje rozszerzeń dla poszczególnych użytkowników, po uruchomieniu programu Visual Studio w obszarze poświadczeń administratora. Po zmianie tej wartości, należy ponownie uruchomić program Visual Studio.|
|EnableOnline|Get/Set (wartość logiczna)|Zapewnia dostęp do rozszerzeń dla programu Visual Studio Marketplace.|
|AutomaticallyCheckForUpdates|Get/Set (wartość logiczna)|Automatycznie sprawdza, czy aktualizacje zainstalowane rozszerzenia.|

## <a name="find-and-replace"></a>Znajdź i zamień
 `DTE.Properties("Environment", "FindAndReplace")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|ShowWarningMessages|Get/Set (wartość logiczna)|Wyświetla komunikaty ostrzegawcze.|
|InitializeFromEditor|Get/Set (wartość logiczna)|Automatycznie wypełni **Znajdź** pole z tekstem z edytora.|
|ShowMessageBoxes|Get/Set (wartość logiczna)|Wyświetla komunikaty informacyjne.|
|HideWindowsAfterMatchFromQuickFindReplace|Get/Set (wartość logiczna)|Ukrywa **Znajdź i Zamień** okna po dopasowanie znajduje się za pomocą **szybkiego wyszukiwania** lub **szybkiego zastąpienia**.|

## <a name="import-and-export-settings"></a>Import i eksport ustawień
 `DTE.Properties("Environment", "Import and Export Settings")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|TrackTeamSettings|Get/Set (wartość logiczna)|Używa ustawień w pliku określonego przez TeamSettingsFile.|
|TeamSettingsFile|Pobierz/Ustaw (ciąg)|Nazwa pliku ustawień zespołu.|
|AutoSaveFile|Pobierz/Ustaw (ciąg)|Nazwa pliku, gdy ustawienia użytkownika są domyślnie zapisywane.|

## <a name="international-settings"></a>Ustawienia międzynarodowe
 `DTE.Properties("Environment", "International")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|Język|Pobierz/Ustaw (ciąg)|Wartość LCID dla bieżącego języka dla programu Visual Studio.|

## <a name="keyboard"></a>Klawiatury
 `DTE.Properties("Environment", "Keyboard")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|Schemat|Pobierz/Ustaw (ciąg)|Zwraca ciąg zawierający schemat wbudowany, ciąg zawierający pełną ścieżkę pliku .vsk, który jest ładowany lub "(domyślna)" Jeśli plik .vsk nie został załadowany.|

## <a name="projects-and-solution"></a>Projekty i rozwiązania
 `DTE.Properties("Environment", "ProjectsAndSolution")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|OnRunOrPreview|Pobierz/Ustaw (ciąg)|Określa, czy IDE zapisywane wszystko przed Podgląd lub systemem skompilowanym projektem.|
|ProjectsLocation|Pobierz/Ustaw (ciąg)|Określa domyślny katalog, w którym **Dodawanie projektu** okno dialogowe zapisuje nowych projektów.|
|ShowOutputWindowBeforeBuild|Get/Set (wartość logiczna)|Określa, czy uruchamianie kompilacji Wyświetla **dane wyjściowe** okna.|
|ShowTaskListAfterBuild|Get/Set (wartość logiczna)|Określa, czy kompilacja powiodła się operacja wyświetla **listy zadań** po zakończeniu kompilacji.|
|TrackFileSelectionInExplorer|Get/Set (wartość logiczna)|Określa, czy bieżący element jest śledzony w **Eksploratora rozwiązań**.|
|AlwaysShowSolutionNode|Get/Set (wartość logiczna)|Określa, czy jest wyświetlany w węźle rozwiązania.|
|OnlySaveStartupProjectsAndDependencies|Get/Set (wartość logiczna)|Określa, czy operacji zapisywania są ograniczone do uruchomienia projektów i ich pliki zależne.|
|ShowAdvancedBuildConfigurations|Get/Set (wartość logiczna)|Określa, czy są wyświetlane zaawansowane konfiguracje kompilacji.|
|ConcurrentBuilds|Pobierz/Ustaw (ciąg)|Określa maksymalną liczbę równolegle kompilowanych projektów, które mogą wystąpić.|
|SaveNewProjects|Get/Set (wartość logiczna)|Określa, czy nowe projekty są automatycznie zapisywane utworzone.|
|PromptForRenameSymbol|Get/Set (wartość logiczna)|Określa, czy Monituj o symboliczną zmianę nazwy po zmianie nazw plików.|
|OnRunWhenErrors|Get/Set (Wyliczenie)|Określa zachowanie przy starcie, gdy Kompilacja została ukończona z błędami.|
|OnRunWhenOutOfDate|Get/Set (Wyliczenie)|Określa zachowanie przy starcie, gdy projekt jest nieaktualny.|
|ProjectTemplatesLocation|Pobierz/Ustaw (ciąg)|Katalog, który zawiera szablony projektów użytkownika.|
|ProjectItemTemplatesLocation|Pobierz/Ustaw (ciąg)|Katalog, który zawiera szablony elementów użytkownika.|
|DefaultBehaviorForStartupProjects|Pobierz/Ustaw (ciąg)||
|MSBuildOutputVerbosity|Pobierz/Ustaw (ciąg)|Określa poziom szczegółowości dla danych wyjściowych kompilacji.|

## <a name="startup"></a>Uruchamianie
 `DTE.Properties("Environment", "Startup")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|OnStartUp|Get/Set (Wyliczenie)|Akcja do wykonania podczas uruchamiania, z <xref:EnvDTE.vsStartUp>, o wartości od 0 do 5:<br /><br /> -0: Otwórz stronę główną<br />-1: obciążenia ostatnio załadowane rozwiązanie<br />-2: Pokaż **Otwórz projekt** — okno dialogowe<br />-3: Pokaż **nowy projekt** — okno dialogowe<br />-4: Pokaż środowisko pusty<br />-5: Pokaż stronę początkową|
|StartPageRSSUrl|Pobierz/Ustaw (ciąg)|Adres URL, dla którego źródło danych RSS jest używana podczas uruchamiania.|
|StartPageRefreshDownloadedContent|Get/Set (wartość logiczna)|Odświeża stronę początkową po każdym przejściu interwał określony we StartPageRefreshInterval.|
|StartPageRefreshInterval|Pobierz/Ustaw (Short)|Interwał w minutach, aby odświeżyć stronę początkową.|

## <a name="tasklist"></a>TaskList
 `DTE.Properties("Environment", "TaskList")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|ConfirmTaskDeletion|Get/Set (wartość logiczna)|Określa, czy okno potwierdzenia Wyświetla podczas usuwania zadania z **listy zadań**.|
|WarnOnAddingHiddenItem|Get/Set (wartość logiczna)|Określa, czy zostanie wyświetlone ostrzeżenie podczas dodawania użytkownika zadanie, które nie będą wyświetlane.|
|DontShowFilePaths|Get/Set (wartość logiczna)|Określa, czy wyświetlać ścieżki całego pliku na liście zadań.|
|CommentTokens|SafeArray|Zwraca wartości tokenów SafeArray komentarza. Każdy ma pola, `Name` (ciąg) i `Priority` (<xref:EnvDTE.vsTaskPriority>, wysoki, średni lub niski).|

## <a name="web-browser"></a>Przeglądarki sieci Web
 `DTE.Properties("Environment", "WebBrowser")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|Strona główna|Pobierz/Ustaw (ciąg)|Reprezentuje adres URL strony głównej.|
|SearchPage|Pobierz/Ustaw (ciąg)|Reprezentuje adres URL strony wyszukiwania.|
|ViewSourceIn|Get/Set (Wyliczenie)|<xref:EnvDTE.vsBrowserViewSource> (Źródło, projekt, zewnętrzny).|
|ViewSourceExternalProgram|Pobierz/Ustaw (ciąg)|Ścieżka podglądu źródła zewnętrznego.|

## <a name="see-also"></a>Zobacz też

- [Kontrolowanie opcji ustawienia](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Określanie nazwy właściwości elementów na stronach opcje](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Strona opcji, czcionki i kolory — Właściwości węzła](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
- [Strona opcji, edytor tekstu — Właściwości węzła](../../ide/reference/options-page-text-editor-node-properties.md)
- [Środowisko, Opcje — okno dialogowe](../../ide/reference/environment-options-dialog-box.md)