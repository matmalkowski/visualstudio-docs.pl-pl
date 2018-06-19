---
title: Obszar roboczy kompilacji w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: f7415c99c68436519f9bab721fe88a48f750fa1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143930"
---
# <a name="workspace-build"></a>Obszar roboczy kompilacji

Obsługa kompilacji [Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) scenariuszy wymaga rozszerzenia umożliwiają określanie wartości [indeksowane](workspace-indexing.md) i [kontekst pliku](workspace-file-contexts.md) dane [obszaru roboczego](workspaces.md), jako również jako akcja kompilacji do uruchomienia.

Poniżej przedstawiono zarys rozszerzenie będzie potrzebny.

## <a name="build-file-context"></a>Tworzenie kontekstu pliku

- Fabryka dostawcy
  - `ExportFileContextProviderAttribute` atrybutem `supportedContextTypeGuids` we wszystkich odpowiednich `string` stałe z `BuildContextTypes`
  - Implementuje `IWorkspaceProviderFactory<IFileContextProvider>`
  - Dostawca kontekstu plików
    - Zwraca `FileContext` dla każdej kompilacji operacji i konfiguracja jest obsługiwana
      - `contextType` Z <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` implementuje <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> z `Configuration` właściwość jako Konfiguracja kompilacji (na przykład `"Debug|x86"`, `"ret"`, lub `null` Jeśli nie ma to zastosowanie). Alternatywnie można użyć wystąpienia <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. Wartość konfiguracji **musi** pasuje do konfiguracji z pliku indeksowanego wartości danych.

## <a name="indexed-build-file-data-value"></a>Wartość danych pliku indeksowanego kompilacji

- Fabryka dostawcy
  - `ExportFileScannerAttribute` atrybutem `IReadOnlyCollection<FileDataValue>` jako obsługiwanym typem
  - Implementuje `IWorkspaceProviderFactory<IFileScanner>`
- Skaner plik na `ScanContentAsync<T>`
  - Zwraca dane podczas `FileScannerTypeConstants.FileDataValuesType` jest argumentem typu
  - Zwraca wartość danych pliku dla każdej konfiguracji skonstruowany przy:
    - `type` jako `BuildConfigurationContext.ContextTypeGuid`
    - `context` jako konfigurację kompilacji (na przykład `"Debug|x86"`, `"ret"`, lub `null` Jeśli nie ma to zastosowanie). Ta wartość **musi** jest zgodna z konfiguracją w kontekście pliku.

## <a name="build-file-context-action"></a>Plik kontekstu akcji kompilacji

- Fabryka dostawcy
  - `ExportFileContextActionProvider` atrybutem `supportedContextTypeGuids` we wszystkich odpowiednich `string` stałe z `BuildContextTypes`
  - Implementuje `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Akcja dostawcy na `IFileContextActionProvider.GetActionsAsync`
  - Zwraca `IFileContextAction` odpowiadającego danego `FileContext.ContextType` wartość
- Plik kontekstu akcji
  - Implementuje `IFileContextAction` i <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` Zwraca właściwości `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` jest `0x1000` dla kompilacji, `0x1010` do odbudowywania, lub `0x1020` do czyszczenia

>[!NOTE]
>Ponieważ `FileDataValue` musi zostać pomyślnie zindeksowane, będzie niektórych ilość czasu między Otwieranie obszaru roboczego i punkt, jaką plik jest skanowany w poszukiwaniu kompilacji pełną funkcjonalność. Opóźnienie będą widoczne na potrzeby otwierania folderu, ponieważ nie istnieje żadne buforowanych indeksu.

## <a name="reporting-messages-from-a-build"></a>Raportowanie wiadomości z kompilacji

Kompilacja może powierzchni informacje, ostrzeżenia i komunikaty o błędach do użytkowników jednego z dwóch sposobów. Prosty sposób polega na użyciu <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> i podaj <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, w następujący sposób:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` i `BuildMessage.LogMessage` kontrolują zachowanie, gdy informacje są prezentowane użytkownikowi. Wszelkie `BuildMessage.TaskType` wartości innych niż `None` utworzy **listy błędów** wpis ze szczegółami danego. `LogMessage` zawsze będą dane wyjściowe w **kompilacji** okienku **dane wyjściowe** okna narzędzia.

Alternatywnie rozszerzenia mogą bezpośrednio współdziałać z **listy błędów** lub **kompilacji** okienka. Istnieje błąd w wersjach wcześniejszych niż Visual Studio 2017 wersji 15.7 gdzie `pszProjectUniqueName` argumentu <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> jest ignorowana.

>[!WARNING]
>Wywołaniach `IFileContextAction.ExecuteAsync` może zawierać dowolne implementacje podstawowej dla `IProgress<IFileContextActionProgressUpdate>` argumentu. Nigdy nie wywołania `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` bezpośrednio. Obecnie nie istnieją żadne ogólne wskazówki dotyczące używania tego argumentu, ale te wskazówki mogą ulec zmianie.

## <a name="build-related-apis"></a>Interfejsy API skojarzone z kompilacji

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> szczegółowe informacje o konfiguracji kompilacji.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> Pokazuje <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>s dla użytkowników.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.VS.JSON i launch.vs.json

Informacje dotyczące tworzenia pliku tasks.vs.json lub launch.vs.json znajdują się w temacie [Dostosowywanie kompilacji i debugowanie zadań](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Następne kroki

* [Protokół serwera języka](language-server-protocol.md) — Dowiedz się, jak zintegrować serwerów języka Visual Studio.