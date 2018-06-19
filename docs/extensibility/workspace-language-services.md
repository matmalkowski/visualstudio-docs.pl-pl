---
title: Obszary robocze i języka usług w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8631ffea-83c8-4fd4-a01e-c59772e89c84
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 551a621ab97c232970d6ef67da14379c5cdfbd46
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140810"
---
# <a name="workspaces-and-language-services"></a>Obszary robocze i usługi języka

Usługi językowe zapewniają [Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) użytkowników tej samej funkcji zaawansowanych języka są używane do podczas pracy z rozwiązań i projektów. Usługa języka własnym może aktywować oparte na rozszerzenia pliku lub zawartości otwartego dokumentu, chociaż usługa języka "utracić plik" jest ograniczona do wyróżniania składni. Dodatkowe informacje są wymagane do świadczenia więcej możliwości, podczas edycji/przeglądu kodu źródłowego. Każda usługa języka ma własnego interfejsu API dla inicjowania przy użyciu tych danych bardzo kontekstowych dla dokumentu. Jest to zwykle zarządzana przez system projektu jest ściśle powiązane z usługą języka i system kompilacji.

## <a name="initialization"></a>Inicjalizacja

W [obszaru roboczego](workspaces.md), usługi języka są inicjowane przez <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> punkt rozszerzenia, specjalizuje się tylko w tej usłudze języka, który nie ma tworzenia kompilacji. W ten sposób Właściciel usługi języka można zachować pojedynczy Folder Otwórz rozszerzenie niezależnie od tego, ile wzorców istnieje w ramach folderów i plików do uruchamiania ich kompilatora podczas kompilacji (na przykład MSBuild, pliki reguł programu make itp.). Gdy zostały zmienione pliki, z których kontekstu plik został utworzony, na dysku i kontekst pliku jest odświeżany, dostawca usługi języka jest powiadamiany o zaktualizowany zestaw kontekstów pliku. Dostawca usługi języka można zaktualizować jej modelu.

Po otwarciu dokumentu w edytorze programu Visual Studio analizuje tylko język dostawców usług, które wymagają typów kontekstu plików, dla których można odnaleźć pasującego dostawcy kontekstu plików. Następnie przekazuje kontekstów pliku z powszechne pasującego do dostawcy usług w wybranym języku za pośrednictwem `ILangaugeServiceProvider.InitializeAsync`. Dostawca usługi języka czego z pliku danych kontekstu jest szczegółów implementacji dostawcy usług języka, że środowisko użytkownika oczekiwane jest bardziej zaawansowane funkcje usługi języka dla danego otworzyć dokument.

## <a name="using-ilanguageserviceprovider"></a>Przy użyciu ILanguageServiceProvider

Usługa języka zostanie powiadomiony, gdy kontekst pliku jest tworzony z `ContextType` odpowiada jednej z `SupportedContextTypes` wartości serwera języka export — atrybut.

Aby obsługiwać usługi języka, rozszerzenie będą potrzebne:

- Unikatową `Guid`. To umożliwi `SupportedContextTypes` argumentów atrybutu i w `FileContext` obiektu.
- Język pliku kontekstu
  - Fabryka dostawcy
    - `ExportFileContextProviderAttribute` atrybut z powyższych jednoznacznie wygenerowany `Guid` w `SupportedContextTypes`
    - Implementuje `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementacja dostawcy `IFileContextProvider.GetContextsForFileAsync`
    - Utworzyć nową `FileContext` z `contextType` argument konstruktora jako jednoznacznie wygenerowany `Guid`
    - Użyj `Context` właściwość `FileContext` umożliwiają dodatkowe dane `ILanguageServiceProvider`
- Usługa języka
  - Fabryka dostawcy
    - `ExportLanguageServiceProvider` atrybut z powyższych jednoznacznie wygenerowany `Guid` w `SupportedContextTypes`
    - Implementuje `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Dostawcy
    - Implementuje `ILanguageServiceProvider`
    - Użyj `ILanguageServiceProvider.InitializeAsync` umożliwia usługi językowe dla podanych argumentów, gdy plik jest otwarty
    - Użyj `ILanguageServiceProvider.UninitializeAsync` można wyłączyć usługi językowe dla podanych argumentów podczas zamykania pliku

>[!WARNING]
>`ILanguageServiceProvider` Metody może być wywoływane przez obszar roboczy w głównym wątku. Warto pomyśleć o zaplanowaniu pracy w innym wątku, aby uniknąć wprowadzenia występują opóźnienia interfejsu użytkownika.

## <a name="language-server-protocol"></a>Protokół serwera języka

`Microsoft.VisualStudio.Workspace.*` Interfejsy API nie są jedynym sposobem, aby umożliwić usłudze języka w otwartym folderze. Innym rozwiązaniem jest użycie serwera języka. Aby uzyskać więcej informacji, przeczytaj o [protokół serwera języka](language-server-protocol.md).

## <a name="related-interfaces"></a>Interfejsy powiązane

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> wywoływane, gdy plik zgodnych typów plików jest otwarty lub zamknięty do edycji.

## <a name="next-steps"></a>Następne kroki

* [Obszar roboczy kompilacji](workspace-build.md) -Otwórz Folder obsługuje tworzenie systemów, takich jak program MSBuild i pliki reguł programu make. 