---
title: Obszary robocze w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 4585ebc5288164f9d441c14332a6af0f1142119b
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="workspaces"></a>Obszary robocze

Obszar roboczy jest jak Visual Studio reprezentuje dowolnej kolekcji plików z [Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), i jest reprezentowana przez <xref:Microsoft.VisualStudio.Workspace.IWorkspace> typu. Samodzielnie obszar roboczy nie rozpoznaje zawartości lub funkcje związane z plików w folderze. Zamiast zapewnia ogólne zestaw interfejsów API funkcji i rozszerzeń do tworzenia i wykorzystywania danych, które inne osoby mogą oni oddziaływać. Producenci składają się za pośrednictwem [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) przy użyciu różnych wyeksportować atrybutów.

## <a name="workspace-providers-and-services"></a>Obszar roboczy dostawców i usługi

Obszar roboczy dostawców i usługi Podaj dane i funkcje, aby zareagować na zawartość obszaru roboczego. Mogą być zapewniają informacji kontekstowych plików symboli w plikach źródłowych lub tworzenie funkcji.

Użyj obu pojęcia [wzorzec fabryki](https://en.wikipedia.org/wiki/Factory_method_pattern) i są importowane przez MEF w obszarze roboczym. Implementuje wszystkie atrybuty eksportu `IProviderMetadataBase` lub `IWorkspaceServiceFactoryMetadata`, ale ma konkretnych typów, które rozszerzenia mają zostać użyte dla typów wyeksportowanych.

Jeden odstęp między dostawców usług jest ich relacji do obszaru roboczego. Obszar roboczy może mieć wielu dostawców określonego typu, ale tylko jedna usługa określonego typu jest tworzony na obszar roboczy. Na przykład obszaru roboczego ma wielu dostawców skanera pliku, ale obszar roboczy ma tylko jedną usługę indeksowania według obszaru roboczego.

Inny Najważniejsza różnica polega na użycie danych od dostawców i usług. Obszar roboczy jest punkt wejścia do pobrania danych z dostawców kilka przyczyn. Po pierwsze dostawców ma zwykle niektórych wąskie zestaw danych, które tworzą. Dane może symboli dla pliku źródłowego C# lub tworzenia pliku kontekstów dla _CMakeLists.txt_ pliku. Obszar roboczy będzie pasował do konsumenta żądanie z dostawcami metadanych, których były wyrównane z żądania. Po drugie, niektóre scenariusze Zezwalaj dla wielu dostawców przyczynić się do żądania, podczas gdy inne scenariusze korzystają z dostawcy o najwyższym priorytecie.

Z kolei rozszerzeń można uzyskać wystąpień i bezpośrednią interakcję z obszaru roboczego usługi. Metody rozszerzenia na `IWorkspace` są dostępne dla usług świadczonych przez program Visual Studio, takich jak <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Rozszerzenie może oferować usługę obszaru roboczego składników w ramach rozszerzenia lub korzystać z innych rozszerzeń. Należy używać konsumentów <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> lub metody rozszerzenia w `IWorkspace` typu.

>[!WARNING]
> Nie możesz tworzyć usług, które powodują konflikt z programem Visual Studio. Może to prowadzić do nieoczekiwanych problemów.

## <a name="disposal-on-workspace-closure"></a>Usuwanie na zamknięcie obszaru roboczego

Podczas zamykania obszaru roboczego, Extender może być konieczne do usunięcia, ale wywołanie asynchroniczne kodu. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> Interfejs jest dostępny pisania tego kodu.

## <a name="related-types"></a>Powiązanych typów

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> jest jednostką centralnej dla otwartego obszaru roboczego, takich jak otwartym folderze.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> tworzy dostawcę na obszar roboczy wystąpienia.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Tworzy usługę na obszar roboczy wystąpienia.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> powinny zostać wdrożone na dostawców i usług, które muszą uruchamiać asynchroniczne kodu podczas usuwania.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> udostępnia metody pomocnicze do uzyskiwania dostępu do usług dobrze znanego lub dowolnego usług.

## <a name="workspace-settings"></a>Ustawienia obszaru roboczego

Obszary robocze mają <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> usługi simple, ale jednocześnie wydajną kontrolę nad obszarem roboczym. Aby uzyskać ogólne omówienie ustawień, zobacz [Dostosowywanie kompilacji i debugowanie zadań](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Ustawienia dla większości `SettingsType` typy są _JSON_ plików, takich jak _VSWorkspaceSettings.json_ i _tasks.vs.json_.

Możliwości ustawienia obszaru roboczego koncentruje się wokół "zakresy", które są po prostu ścieżki w obszarze roboczym. Kiedy klient wywołuje <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, wszystkie zakresy obejmujące żądany ścieżce i typu ustawienia są agregowane. Priorytet agregacji zakres jest następujący:

1. "Ustawienia lokalnego", co jest zazwyczaj katalogu roboczego `.vs` katalogu.
1. Żądana ścieżka samej siebie.
1. Katalog nadrzędny żądanej ścieżki.
1. Nadrzędnego wszystkie dodatkowe katalogi, w tym katalogu roboczego.
1. "Ustawienia globalne", które znajduje się w katalogu użytkownika.

Wynik jest wystąpieniem <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Ten obiekt zawiera ustawienia dla określonego typu i może być badana Ustawianie nazw kluczy przechowywanych jako `string`. <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> Metod i <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> metody rozszerzenia oczekują od wywołującego jest znany typ żądanej wartości ustawień. Ponieważ większość plików ustawienia są zachowywane jako _JSON_ plików, będzie używana w wielu wywołań `string`, `bool`, `int`i tablice tych typów. Typy obiektów są również obsługiwane. W takich przypadkach można użyć `IWorkspaceSettings` siebie jako argument typu. Na przykład:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Zakładając, że te ustawienia były użytkownika _VSWorkspaceSettings.json_, dane są dostępne:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Ustawienia te interfejsy API są związane z interfejsami API dostępnymi w `Microsoft.VisualStudio.Settings` przestrzeni nazw. Ustawienia obszaru roboczego są niezależny hosta i użyć plików ustawienia specyficzne dla obszaru roboczego lub dostawców ustawień dynamicznych.

### <a name="providing-dynamic-settings"></a>Zapewnianie ustawień dynamicznych

Rozszerzenia może zapewnić <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Tych dostawców w pamięci umożliwia dodawanie ustawień lub inne zastąpienie przez rozszerzenia.

Eksportowanie `IWorkspaceSettingsProvider` różni się od innych dostawców obszaru roboczego. Fabryka nie jest `IWorkspaceProviderFactory` i nie ma typu atrybutu specjalnych. Zamiast tego należy zaimplementować <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> i użyj `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Podczas wykonywania metody, które zwracają `IWorkspaceSettingsSource` (takich jak `IWorkspaceSettingsProvider.GetSingleSettings`), zwrócić wystąpienia `IWorkspaceSettings` zamiast `IWorkspaceSettingsSource`. `IWorkspaceSettings` zawiera więcej informacji, które mogą być przydatne podczas agregacji niektórych ustawień.

### <a name="settings-related-apis"></a>Ustawienia związane z interfejsów API

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> odczytuje i agreguje ustawienia dla obszaru roboczego.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> pobiera `IWorkspaceSettingsManager` dla obszaru roboczego.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> pobiera ustawienia dla danego zakresu zagregowane we wszystkich nakładających się zakresów.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> zawiera ustawienia dla określonego zakresu.

## <a name="workspace-suggested-practices"></a>Obszar roboczy sugerowane rozwiązania

- Zwraca obiekty z `IWorkspaceProviderFactory.CreateProvider` lub podobne interfejsów API, które należy pamiętać, ich `Workspace` kontekście podczas tworzenia. Interfejsy dostawców są zapisywane oczekuje się, że ten obiekt jest przechowywany na tworzenie.
- Zapisz ustawienia w ścieżce "Ustawienia lokalnego" tego obszaru roboczego lub pamięci podręcznych specyficzne dla obszaru roboczego. Tworzenie ścieżki do pliku przy użyciu `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` w programie Visual Studio 2017 wersji 15.6 lub nowszej. Wersje poprzedzające wersję 15,6 użyj następującego fragmentu kodu:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Rozwiązanie zdarzenia i automatyczne ładowanie pakietu

Można wdrożyć pakietów załadować `IVsSolutionEvents7` i wywoływać `IVsSolution.AdviseSolutionEvents`. Obejmuje on zdarzeń na otwieranie i zamykanie folderu w programie Visual Studio.

Kontekst interfejsu użytkownika można automatycznie załadować pakietu. Wartość jest `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Pakiet SourceExplorerPackage nie został poprawnie załadowany.

Rozszerzalność obszaru roboczego jest silnie MEF oparty na i błędów kompozycji spowoduje, że hosting Otwórz Folder, aby nie można załadować pakietu. Na przykład, jeśli rozszerzenie eksportuje typ z `ExportFileContextProviderAttribute`, ale tylko implementuje typ `IWorkspaceProviderFactory<IFileContextActionProvider>`, wystąpi błąd podczas próby otwarcia folderu w programie Visual Studio. Szczegóły błędu można znaleźć w _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Usuń wszelkie błędy dla typów implementowane przez rozszerzenie.

## <a name="next-steps"></a>Następne kroki

* [Plik kontekstów](workspace-file-contexts.md) -dostawców kontekstu pliku dostosowania analizy kodu dla obszarów roboczych Otwórz Folder. 
* [Indeksowanie](workspace-indexing.md) -indeksowania obszaru roboczego zbiera i będzie nadal występował, informacje o obszarze roboczym.
