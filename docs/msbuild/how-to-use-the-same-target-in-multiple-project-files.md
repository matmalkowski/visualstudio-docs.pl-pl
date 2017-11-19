---
title: "Porady: Użyj tej samej wartości docelowej w wielu plikach projektów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: b591f0158408161d268930416d49c465e29d0b2c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Porady: użycie tej samej wartości docelowej w wielu plikach projektów
Jeśli niektóre utworzyli [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliki projektu, użytkownik może odkryć należy używać tych samych zadań i elementów docelowych w plikach inny projekt. Zamiast w każdym pliku projektu w tym pełny opis tych zadań lub miejsc docelowych, można zapisać obiektu docelowego w oddzielny plik projektu, a następnie zaimportuj tego projektu do innego projektu, który musi być elementem docelowym.  
  
## <a name="using-the-import-element"></a>Za pomocą elementu importu  
 `Import` Element służy do wstawiania jeden plik projektu do innego pliku projektu. Plik projektu, który jest importowany musi być prawidłowym [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu i zawierać poprawnie sformułowany plik XML. `Project` Atrybut określa ścieżkę do zaimportowanego pliku projektu. Aby uzyskać więcej informacji na temat `Import` elementu, zobacz [Import — Element (MSBuild)](../msbuild/import-element-msbuild.md).  
  
#### <a name="to-import-a-project"></a>Aby zaimportować projekt  
  
1.  Zdefiniuj w importowania pliku projektu, wszystkie właściwości i elementów, które są używane jako parametry dla właściwości i elementów w zaimportowanego projektu.  
  
2.  Użyj `Import` element Importowanie projektu. Na przykład:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3.  Po `Import` elementu, zdefiniuj wszystkie właściwości i elementy, które należy zastąpić domyślne definicji właściwości i elementów w zaimportowanego projektu.  
  
## <a name="order-of-evaluation"></a>Kolejność obliczania  
 Gdy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] osiągnie `Import` elementu zaimportowanego projektu skutecznie zostaną wstawione do importowania projektu w lokalizacji `Import` elementu. W związku z tym lokalizację `Import` element może mieć wpływ na wartości właściwości i elementów. Należy zapoznać się z właściwości i elementy, które są ustawiane przez zaimportowanego projektu i właściwości i elementów używanych zaimportowanego projektu.  
  
 Podczas tworzenia projektu, wszystkie właściwości są oceniane najpierw, a po nim elementów. Na przykład następujący kod XML definiuje zaimportowanego pliku projektu MyCommon.targets:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 Następujący kod XML definiuje MyApp.proj, który importuje MyCommon.targets:  
  
```xml  
<Project  
    DefaultTargets="Go"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyApp</Name>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
 Podczas tworzenia projektu, zostanie wyświetlony następujący komunikat:  
  
 `Name="MyCommon"`  
  
 Ponieważ projekt jest zaimportowany po właściwość `Name` został zdefiniowany w MyApp.proj, definicji `Name` MyCommon.targets zastąpienia definicji w MyApp.proj. Jeśli projekt jest importowany przed zdefiniowano nazwy właściwości, kompilacja będzie wyświetli następujący komunikat:  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>Podczas importowania projektów, zastosuj następujące podejście  
  
1.  Zdefiniuj w pliku projektu, wszystkie właściwości i elementów, które są używane jako parametry dla właściwości i elementów w zaimportowanego projektu.  
  
2.  Importowanie projektu.  
  
3.  Wszystkie właściwości i elementy, które należy zastąpić domyślne definicji właściwości i elementów w zaimportowanego projektu i zdefiniuj w pliku projektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia plik MyCommon.targets, który importuje w drugim przykładzie kodu. W pliku .targets oblicza właściwości z importowania projektu, aby skonfigurować kompilacji.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>  
        <appname>$(MSBuildProjectName)</appname>  
    <PropertyGroup>  
    <Target Name="Build">  
        <Csc Sources="hello.cs"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod importuje plik MyCommon.targets.  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Import — Element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Obiekty docelowe](../msbuild/msbuild-targets.md)