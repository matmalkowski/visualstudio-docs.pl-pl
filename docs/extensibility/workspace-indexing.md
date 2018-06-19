---
title: Obszar roboczy indeksowania w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 5004db0d895d1fdc697c18606c346c24cd484527
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143429"
---
# <a name="workspace-indexing"></a>Indeksowanie obszaru roboczego

W rozwiązaniu, systemów projektów spoczywa odpowiedzialność za zapewnienie funkcjonalności dla kompilacji, debugowanie, **GoTo** wyszukiwanie symboli i inne. Systemy projektu można zrobić prac, ponieważ zrozumieniu relacji i możliwości pliki w projekcie. [Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) obszaru roboczego wymaga takiego samego wglądu do udostępnia również zaawansowanych funkcji środowiska IDE. Zbieranie i trwałego magazynu danych jest w procesie nazywanym indeksowania obszaru roboczego. Ten zindeksowanych danych można tworzyć zapytania za pomocą zestawu interfejsów API asynchronicznego. Extender mogą uczestniczyć w procesie indeksowania zapewniając <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>s, który potrafi obsłużyć niektórych typów plików.

## <a name="types-of-indexed-data"></a>Typy danych indeksowanych

Istnieją trzy typy danych, które są indeksowane. Należy pamiętać, że w typ oczekiwany przez skanery pliku różni się od typu rozszeregować z indeksu.

|Dane|Typ pliku skanera|Typ wyniku kwerendy indeksu|Powiązanych typów|
|--|--|--|--|
|Odwołania|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Symbole|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> należy użyć zamiast `IIndexWorkspaceService` zapytań|
|Wartości danych|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Wykonanie zapytania dotyczącego zindeksowanych danych

Istnieją dwa typy asynchroniczne umożliwiających dostęp do danych. Pierwsza to za pośrednictwem <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Zapewnia podstawowe dostęp do pojedynczego pliku `FileReferenceResult` i `FileDataResult` danych który buforuje wyników. Druga <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> który nie korzysta z pamięci podręcznej, ale zezwala na więcej możliwości wykonywanie zapytania.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Należący do indeksowania

Następująca sekwencja około indeksowania obszaru roboczego są następujące:

1. Odnajdywanie i trwałości jednostek systemowych plików w obszarze roboczym (tylko na skanowanie otwierania początkowej).
1. Dla każdego pliku, dostawca zgodnego z najwyższym priorytetem jest proszony o skanowanie w poszukiwaniu `FileReferenceInfo`s.
1. Dla każdego pliku, dostawca zgodnego z najwyższym priorytetem jest proszony o skanowanie w poszukiwaniu `SymbolDefinition`s.
1. Dla każdego pliku, wszystkich dostawców jest proszony o `FileDataValue`s.

Rozszerzenia można wyeksportować skaner zaimplementowanie `IWorkspaceProviderFactory<IFileScanner>` i eksportowanie typu o <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. `SupportedTypes` Argument atrybutu musi być co najmniej jedna wartość z <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Dla skanera przykład zestawu VS SDK [próbki](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Nie Eksportuj skanera pliku, który obsługuje `FileScannerTypeConstants.FileScannerContentType` typu. Służy do firmy Microsoft, tylko wewnętrznie.

W sytuacjach, zaawansowane rozszerzenie dynamicznie może obsługiwać dowolny zestaw typów plików. Zamiast eksportu MEF `IWorkspaceProviderFactory<IFileScanner>`, można wyeksportować rozszerzenie `IWorkspaceProviderFactory<IFileScannerProvider>`. Po rozpoczęciu indeksowania tego typu fabryki zostanie zaimportowany, wystąpienia i mieć jego <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> wywołana metoda. `IFileScanner` Obsługa dowolną wartość z wystąpienia `FileScannerTpeConstants` będzie można go uznać, nie tylko symbole.

## <a name="next-steps"></a>Następne kroki

* [Obszary robocze i usługi języka](workspace-language-services.md) — informacje o sposobie integrowania usług języka Otwórz Folder roboczy.
* [Obszar roboczy kompilacji](workspace-build.md) -Otwórz Folder obsługuje tworzenie systemów, takich jak program MSBuild i pliki reguł programu make.