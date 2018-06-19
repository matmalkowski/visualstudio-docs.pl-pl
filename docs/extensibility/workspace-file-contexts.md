---
title: Konteksty pliku obszaru roboczego w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: cdb013bb10c72041b03fce43e115806ecb3faeac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146354"
---
# <a name="workspace-file-contexts"></a>Konteksty pliku obszaru roboczego

Wszystkie wgląd w [Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) obszarów roboczych są produkowane przez "pliku dostawców kontekstu" implementujących <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> interfejsu. Te rozszerzenia mogą szukania wzorców w folderach lub plików, odczytywanie MSBuild plików i pliki reguł programu make, wykrywania zależności pakietów itp. aby gromadzone szczegółowych danych potrzebnych do definiowanie kontekstu pliku. Kontekst pliku samodzielnie nie wykonuje żadnych czynności, ale raczej zawiera dane, które następnie można wykonywać operacje na inne rozszerzenie.

Każdy <xref:Microsoft.VisualStudio.Workspace.FileContext> ma `Guid` skojarzonych z nim identyfikujący rodzaj danych go posiada. Obszar roboczy używa to `Guid` później, aby zapewnić zgodność identyfikatorów z rozszerzeniami, które wykorzystują dane za pośrednictwem <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> właściwości. Dostawca kontekstu plików został wyeksportowany z metadanymi identyfikujący kontekstu plików, które `Guid`s go może tworzyć dane.

Po zdefiniowaniu, kontekst pliku można skojarzyć z dowolną liczbę plików lub folderów w obszarze roboczym. Dany plik lub folder może być skojarzony z dowolnej liczby kontekstów pliku. Jest to relacja wiele do wielu.

Najbardziej typowe scenariusze dla kontekstów pliku odnoszą się do usługi języka, debugowania i kompilacji. Aby uzyskać więcej informacji zobacz inne tematy związane z tych scenariuszy.

## <a name="file-context-lifecycle"></a>Cykl życia kontekstu pliku

Cyklu `FileContext` jest deterministyczna. W dowolnym momencie składnika można asynchronicznie żądanie niektórych zestaw typów kontekstu. Będzie można zbadać dostawców, którzy obsługują niektóre podzbiór typów kontekstu żądania. `IWorkspace` Wystąpienia działa jako środka man między klienta i dostawcy za pośrednictwem <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> metody. Konsumenci może kontekst żądania i wykonanie akcji krótkoterminowych na podstawie kontekstu, podczas gdy inne osoby mogą kontekst żądania i zachować długotrwałe odwołania. 

Zmiany może się zdarzyć do plików, które powodują kontekst pliku do staną się nieaktualne. Dostawca mogą wyzwalać zdarzenia na `FileContext` powiadomił użytkowników aktualizacji. Na przykład jeśli kontekst kompilacji jest dostępny dla niektórych plików, ale zmiany na dysku unieważnia w tym kontekście, następnie oryginalnego producentów mogą być wywoływane zdarzenia. Żadnych użytkowników nadal odwołuje się do który `FileContext` można następnie requery nowej `FileContext`.

>[!NOTE]
>Nie zostanie wzór wypychania dla konsumentów. Konsumenci nie będzie powiadamiany o dostawcy nowych `FileContext` po ich żądania.

## <a name="expensive-file-context-computations"></a>Obliczenia kontekstu kosztowne pliku

Zawartość pliku odczytu z dysku może być kosztowne, szczególnie w przypadku, gdy dostawca musi rozpoznać relacji między plikami. Na przykład można wykonać zapytania dostawcę dla niektórych pliku źródłowego pliku kontekstu, ale kontekst pliku zależy od metadanych z pliku projektu. Podczas analizowania pliku projektu lub oceny to przy użyciu programu MSBuild jest kosztowna. Zamiast tego rozszerzenia można wyeksportować `IFileScanner` utworzyć `FileDataValue` danych podczas indeksowania obszaru roboczego. Teraz po otrzymaniu monitu, dla kontekstów pliku `IFileContextProvider` mogą szybko przeszukiwać dla indeksowanego danych. Aby uzyskać więcej informacji na temat indeksowania, zobacz [indeksowania obszaru roboczego](workspace-indexing.md) tematu.

>[!WARNING]
>Należy uważać na inne sposoby Twojej `FileContext` może być kosztowne do obliczenia. Niektóre interakcje interfejsu użytkownika są synchroniczne i polegać na dużą liczbę `FileContext` żądań. Przykładami otwierania kartę Edytor i otwieranie **Eksploratora rozwiązań** menu kontekstowego. Te akcje należy wiele kontekst kompilacji typ żądania.

## <a name="file-context-related-apis"></a>Interfejsy API skojarzone z kontekstu pliku

- <xref:Microsoft.VisualStudio.Workspace.FileContext> przechowuje dane i metadanych.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> i <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> utworzyć kontekstu pliku.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Eksportuje dostawcy kontekstu plików.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> jest używany dla konsumentów do pobierania plików kontekstach.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> Definiuje kompilacji typów kontekstu, które będą korzystać z otwartym folderze.

## <a name="file-context-actions"></a>Plik kontekstu akcji

Gdy `FileContext` jest tylko dane dotyczące niektórych plików <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> sposób express i korzystania z tych danych. `IFileContextAction` jest elastyczny w jej użycia. Są dwa jego najbardziej typowych przypadkach kompilowanie i debugowanie.

## <a name="reporting-progress"></a>Raport z postępów

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> Metody jest przekazywany `IProgress<IFileContextActionProgressUpdate>`, ale argument nie należy używać jako typu. `IFileContextActionProgressUpdate` jest pustego interfejsu i wywoływanie `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` może zgłosić `NotImplementedException`. Zamiast tego `IFileContextAction` rzutować argument do innego typu, w razie potrzeby scenariusza.

Informacje o typach dostarczonych przez program Visual Studio scenariusz odpowiedniej dokumentacji.

## <a name="file-context-action-related-apis"></a>Interfejsy API skojarzone z pliku kontekstu akcji

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> wykonuje niektóre zachowanie na podstawie `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> tworzy wystąpienia `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> Eksportuje typ `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Obserwowanie pliku

Obszar roboczy nasłuchuje powiadomień o zmianie pliku i zapewnia <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> za pośrednictwem <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Pliki zgodne z ustawieniem "ExcludedItems" nie powoduje wygenerowanie pliku zdarzenia powiadomień. Próg między zdarzeniami służy do uproszczenia powiadomień i zmniejszenie zduplikowane. Gdy trzeba reagowania na zmiany plików, należy subskrybować tej usługi.

>[!TIP]
>Obszar roboczy [indeksowania usługi](workspace-indexing.md) subskrybuje zdarzenia pliku domyślnie. Plik dodatki i zmiany spowoduje, że odpowiednie `IFileScanner`s zdarzenia do nowych danych dla tego pliku. Liczba operacji usunięcia pliku spowoduje usunięcie zindeksowanych danych. Nie trzeba subskrybować Twojej `IFileScanner` z usługą obserwatora pliku.

## <a name="next-steps"></a>Następne kroki

* [Indeksowanie](workspace-indexing.md) -indeksowania obszaru roboczego zbiera i będzie nadal występował, informacje o obszarze roboczym.
* [Obszary robocze](workspaces.md) — Przegląd pojęć obszaru roboczego i ustawienia magazynu.
