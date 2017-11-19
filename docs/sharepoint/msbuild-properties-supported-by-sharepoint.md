---
title: "Właściwości MSBuild obsługiwane przez program SharePoint | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, MSBuild properties
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 53e90448d5e7a24f4904f9c4ea02ac041531ce02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Właściwości MSBuild obsługiwane przez SharePoint
  Wszelkie [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości zdefiniowane w pliku, plik projektu lub pliku użytkownika projektu Microsoft.VisualStudio.SharePoint.targets można używać w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint — projekty. Oprócz typowe [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości dostarczanych przez projekt SharePoint definiuje dodatkowe właściwości, które są specyficzne dla projektów programu SharePoint.  
  
 Aby uzyskać listę wspólnych [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości, zobacz [wspólne właściwości projektów MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687). Pełną listę właściwości obsługiwanych przez język programowania, można znaleźć w pliku .targets, pliku projektu (pliku .csproj lub .vbproj) lub pliku użytkownika projektu (csproj.user lub. vbproj.user).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>MSBuild właściwości charakterystyczne dla programu SharePoint  
 W poniższej tabeli wymieniono [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] właściwości, które dotyczą przede wszystkim SharePoint — projekty w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Istnieją inne właściwości, ale są one do użytku wewnętrznego.  
  
|Nazwa właściwości|Opis|  
|-------------------|-----------------|  
|SharePointSiteUrl|Ciąg reprezentujący [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] do witryny programu SharePoint.|  
|SandboxedSolution|Wartość logiczna wskazująca, czy rozwiązanie jest rozwiązania w trybie piaskownicy.|  
|ActiveDeploymentConfiguration|Konfiguracja aktywnych wdrożeń.|  
|IncludeAssemblyInPackage|Wartość logiczna wskazująca, czy zestaw jest uwzględniona w pliku pakietu.|  
|PreDeploymentCommand|Wartość ciągu, która reprezentuje polecenie do wykonania w kroku polecenia przed wdrożeniem.|  
|PostDeploymentCommand|Wartość ciągu, który reprezentuje polecenie do wykonania w kroku polecenia po wdrożeniu.|  
|CustomBeforeSharePointTargets|Ciąg, który reprezentuje ścieżkę [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] plik elementów docelowych. Jeśli plik elementów docelowych istnieje i jest zdefiniowany, zostaną zaimportowane przed wszystkie dane obiektów docelowych programu SharePoint. Ta właściwość umożliwia dostosowanie procesu pakietu przez predefiniowanie właściwości związane z — bez modyfikowania dostarczany plik elementów docelowych programu SharePoint, ale plik elementów docelowych nadal ma zastosowanie do wszystkich projektów programu SharePoint.|  
|CustomAfterSharePointTargets|Ciąg, który reprezentuje ścieżkę [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] plik elementów docelowych. Jeśli plik elementów docelowych istnieje i jest zdefiniowany, to po wszystkich importowanych danych obiektów docelowych programu SharePoint. Ta właściwość umożliwia dostosowanie procesu pakietu przez zastąpienie właściwości powiązanych z pakietów i obiektów docelowych, bez konieczności modyfikowania dostarczany plik elementów docelowych programu SharePoint, ale plik elementów docelowych nadal ma zastosowanie do wszystkich projektów programu SharePoint.|  
|Element LayoutPath|Ciąg, który reprezentuje katalog główny plików spakowanych tymczasowo rozmieszczenie zanim zostaną one dodane do pliku wsp. Ta ścieżka może być przydatne do ustalenia, kiedy można zastąpić cele BeforeLayout i AfterLayout, aby dodać, usunąć lub zmodyfikować pliki być spakowany, ponieważ służy do zmiany zawartości w pliku wsp.|  
|BasePackagePath|Ciąg, który reprezentuje folder, w której znajduje się pakiet. Katalog wyjściowy projektu, takie jak Bin\Debug korzysta z tej wartości.|  
|PackageExtension|Ciąg, który reprezentuje rozszerzenie nazwy pliku, który ma zostać dołączony do pakietu. Wartość domyślna to wsp.|  
|AssemblyDeploymentTarget|Ciąg, który reprezentuje lokalizację, w którym zestawu projekt jest wdrażany na serwerze programu SharePoint. Wartość jest GlobalAssemblyCache (ustawienie domyślne) lub aplikacji sieci Web. Tej właściwości można ustawić w taki sposób, w oknie właściwości.|  
|PackageWithValidation|Wartość logiczna określająca, czy sprawdzanie poprawności jest wykonywane przed opakowania. Ta właściwość umożliwia ignorowanie błędów sprawdzania poprawności podczas kompilowania pakietów.|  
|ValidatePackageDependsOn|Ciąg, który definiuje dodatkowe cele do wykonania przed elementem docelowym ValidatePackage.|  
|TokenReplacementFileExensions|Ciąg, który definiuje pliki, których tokenów zastąpiony podczas pakowania.|  
  
## <a name="using-msbuild-properties-in-the-properties-page"></a>Na stronie właściwości za pomocą właściwości programu MSBuild  
 Elastyczność zamiast ustalony ciągów w **wiersza polecenia przed wdrożeniem** i **wiersza polecenia po wdrożeniu** pola na stronie właściwości programu SharePoint można użyć programu SharePoint właściwości jako argumenty. Na przykład zamiast określania określony [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] ciąg witryny programu SharePoint, należy użyć `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Możesz użyć dowolnej [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] składni zmiennej `$(` *propertyName* `)` lub składnia zmiennej środowiskowej `%` *propertyName* `%` Aby określić właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do MSBuild](/visualstudio/msbuild/msbuild-reference)  
  
  