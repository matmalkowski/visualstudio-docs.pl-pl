---
title: "Rozwiązywanie problemów z błędami obiektów docelowych w programie .NET Framework | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e22020797d14c74c744276df3fafef6a9d799f2f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="troubleshooting-net-framework-targeting-errors"></a>Rozwiązywanie problemów z błędami obiektów docelowych programu .NET Framework
W tym temacie opisano błędy MSBuild, które mogą występować z powodu odwołania problemy i jak można usunąć te błędy.  
  
## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Ma odwołanie do projektu lub zestawu, którego celem jest inna wersja programu .NET Framework  
 Można tworzyć aplikacje, które odwołują się do projektów lub zestawów, które odnoszą się do różnych wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Na przykład można utworzyć aplikację, przeznaczonego dla profilu klienta [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] , ale odwołuje się do zestawu, przeznaczonego dla programu .NET Framework 2.0. Jednak w przypadku utworzenia projektu który jest przeznaczony dla starszej wersji programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], nie można ustawić odwołanie projektu do projektu lub zestawu, który jest przeznaczony dla profilu klienta [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] lub [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] samej siebie. Aby rozwiązać problem, upewnij się, że aplikacja jest przeznaczony dla profilu lub profilach, które są zgodne z profilem, który jest celem projektów lub zestawów, które odwołuje się do aplikacji.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Ponownie jest skierowany projektu do innej wersji programu .NET Framework  
 Jeśli zmienisz wersję docelową [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dla aplikacji, Visual Studio zmienia niektórych odwołań, ale być może trzeba ręcznie aktualizować niektórych odwołań. Na przykład jeden z wymienionych błędów mogą wystąpić w przypadku zmiany aplikację docelową [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)] i że aplikacja ma zasoby ani ustawienia, które są oparte na profilu klienta dla [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)].  
  
 Aby obejść ustawienia aplikacji, otwórz **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki**, a następnie przeprowadź edycję pliku app.config w edytorze XML programu Visual Studio. Zmiana wersji w ustawieniach, aby dopasować odpowiednią wersję programu .NET Framework. Na przykład można zmienić ustawienie wersji z 4.0.0.0 do 2.0.0.0. Podobnie dla aplikacji, która została dodana zasobów, należy otworzyć **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** , rozwiń pozycję **mój projekt** (Visual Basic) lub **Właściwości** (C#), a następnie przeprowadź edycję pliku Resources.resx w edytorze XML programu Visual Studio. Zmień ustawienie wersji z 4.0.0.0 na 2.0.0.0.  
  
 Jeśli aplikacja ma zasoby, takie jak ikony lub mapy bitowe lub ustawienia, takie jak parametry połączenia danych, można również rozwiązać błąd, usuwając wszystkie elementy na **ustawienia** strony **projektanta projektu**, a następnie ponowne dodanie wymaganych ustawień.  
  
## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Ponownie jest skierowany projektu do innej wersji programu .NET Framework i nie rozpoznać odwołania  
 Jeśli przekierowanie projektu do innej wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], referencje mogą nie być rozpoznawane poprawnie w niektórych przypadkach. Jawne pełni kwalifikowanego odwołania do zestawów często przyczyną tego problemu, ale można go rozpoznać Usuwanie odwołań, które nie umożliwiają rozwiązania, a następnie dodanie ich do projektu. Alternatywnie można edytować pliku projektu w celu zastąpienia odwołań. Najpierw należy usunąć odwołania mają następującą postać:  
  
```xml  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Następnie należy zastąpić je prostego formularza:  
  
```xml  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
>  Po zamknięciu i ponownie otwórz projekt, należy również można odbudować go, aby poprawnie rozpoznać wszystkich odwołań.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET framework Client Profile](/dotnet/framework/deployment/client-profile)   
 [Przeznaczonych dla określonej wersji platformy .NET](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)