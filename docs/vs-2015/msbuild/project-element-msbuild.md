---
title: Project — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a7d832ba052c557411a3c689f30cf133deb523d1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628801"
---
# <a name="project-element-msbuild"></a>Project — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Project — Element (MSBuild)](https://docs.microsoft.com/visualstudio/msbuild/project-element-msbuild).  
  
  
Element główny wymagany [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>  
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Choose>... </Choose>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Target>... </Target>  
    <UsingTask.../>  
    <ProjectExtensions>... </ProjectExtensions>  
    <Import... />  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`DefaultTargets`|Atrybut opcjonalny.<br /><br /> Domyślny element docelowy lub cele, które mają być punktem wejścia kompilacji, jeśli żadne miejsce docelowe nie zostało określone. Wiele elementów docelowych są rozdzielonych średnikami (;) rozdzielonych.<br /><br /> Jeśli określono nie domyślnego obiektu docelowego w jednym `DefaultTargets` atrybutu lub [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wiersza polecenia, aparat wykonuje pierwszego obiektu docelowego w pliku projektu po [importu](../msbuild/import-element-msbuild.md) elementy zostały ocenione.|  
|`InitialTargets`|Atrybut opcjonalny.<br /><br /> Początkowa docelowego lub obiekty docelowe do uruchomienia przed obiektów docelowych określonych w `DefaultTargets` atrybutu lub w wierszu polecenia. Wiele elementów docelowych są rozdzielonych średnikami (;) rozdzielonych.|  
|`ToolsVersion`|Atrybut opcjonalny.<br /><br /> Wersja zestawu narzędzi MSBuild używa do określenia wartości $(MSBuildBinPath) i $(MSBuildToolsPath).|  
|`TreatAsLocalProperty`|Atrybut opcjonalny.<br /><br /> Nazwy właściwości, które nie były uznawane za będzie globalnym. Ten atrybut zapobiega zastępowanie wartości właściwości, które są ustawione w pliku projektu lub miejsc docelowych i wszystkie Importy kolejnych określonych właściwości wiersza polecenia. Wiele właściwości są rozdzielonych średnikami (;) rozdzielonych.<br /><br /> Zwykle globalne właściwości zastępują wartości właściwości, które są ustawione w pliku projektu lub miejsc docelowych. Jeśli właściwość jest wymieniona w `TreatAsLocalProperty` wartość, wartość właściwości globalnej nie zastępuje wartości właściwości, które są ustawiane w pliku i wszystkie Importy kolejne. Aby uzyskać więcej informacji, zobacz [porady: kompilacja tych samych plików źródłowych przy użyciu różnych opcji](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Uwaga:** ustawić globalne właściwości w wierszu polecenia, używając **/property** (lub **/p**) przełącznika. Możesz również ustawić lub zmodyfikować globalnych właściwości dla projektów podrzędnych w kompilacji wielu projektów za pomocą `Properties` atrybut zadanie programu MSBuild. Aby uzyskać więcej informacji, zobacz [zadanie MSBuild](../msbuild/msbuild-task.md).|  
|`Xmlns`|Atrybut wymagany.<br /><br /> `xmlns` Atrybut musi mieć wartość "http://schemas.microsoft.com/developer/msbuild/2003".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Wybierz opcję](../msbuild/choose-element-msbuild.md)|Element opcjonalny.<br /><br /> Ocenia elementy podrzędne, aby wybrać jeden zestaw `ItemGroup` elementy i/lub `PropertyGroup` elementy do oceny.|  
|[Import](../msbuild/import-element-msbuild.md)|Element opcjonalny.<br /><br /> Umożliwia pliku projektu zaimportować innego pliku projektu. Może wynosić zero lub więcej `Import` elementy w projekcie.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Element grouping dla poszczególnych elementów. Elementy określone za pomocą [elementu](../msbuild/item-element-msbuild.md) elementu. Może wynosić zero lub więcej `ItemGroup` elementy w projekcie.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|Element opcjonalny.<br /><br /> Zapewnia sposób, aby utrwalić non -[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] informacje zawarte w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu. Może mieć zero lub jeden `ProjectExtensions` elementy w projekcie.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Element grouping dla poszczególnych właściwości. Właściwości są określane za pomocą [właściwość](../msbuild/property-element-msbuild.md) elementu. Może wynosić zero lub więcej `PropertyGroup` elementy w projekcie.|  
|[Docelowy](../msbuild/target-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw zadań dla [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do wykonania po kolei. Zadania są określone za pomocą [zadań](../msbuild/task-element-msbuild.md) elementu. Może wynosić zero lub więcej `Target` elementy w projekcie.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Element opcjonalny.<br /><br /> Zapewnia sposób zarejestrować zadań w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Może wynosić zero lub więcej `UsingTask` elementy w projekcie.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
 Brak.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Określanie pierwszego obiektu docelowego do kompilacji](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](msbuild.md)


