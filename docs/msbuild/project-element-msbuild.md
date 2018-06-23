---
title: Project — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c97557b18b589ece08ce4f3a536201df3d98aa8
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326805"
---
# <a name="project-element-msbuild"></a>Project — Element (MSBuild)
Wymaganego głównego elementu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu.  

## <a name="syntax"></a>Składnia  

```xml  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Sdk... />
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
|`DefaultTargets`|Atrybut opcjonalny.<br /><br /> Docelowy domyślne lub cele, które mają być punktem wejścia kompilacji, jeśli nie podano elementu docelowego. Wiele obiektów docelowych są średnikami (;) przecinkami.<br /><br /> Jeśli określono bez domyślnego obiektu docelowego w jednym `DefaultTargets` atrybutu lub [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wiersza polecenia, aparat wykonuje pierwszy element docelowy w pliku projektu po [importu](../msbuild/import-element-msbuild.md) elementy zostały ocenione.|  
|`InitialTargets`|Atrybut opcjonalny.<br /><br /> Docelowy początkowej lub obiekty docelowe do uruchomienia przed cele określone w `DefaultTargets` atrybutu lub w wierszu polecenia. Wiele obiektów docelowych są średnikami (;) przecinkami.|  
|`Sdk`|Atrybut opcjonalny. <br /><br /> Nazwa zestawu SDK i opcjonalnie wersja używać do tworzenia niejawne zaimportować instrukcji, które są dodawane do pliku .proj. Jeśli wersja nie jest określona, MSBuild podejmie próbę rozpoznania wersja domyślna.  Na przykład `<Project Sdk="Microsoft.NET.Sdk" />` lub `<Project Sdk="My.Custom.Sdk/1.0.0" />`.|  
|`ToolsVersion`|Atrybut opcjonalny.<br /><br /> Wersja zestawu narzędzi MSBuild używa w celu określenia wartości $(MSBuildBinPath) i $(MSBuildToolsPath).|  
|`TreatAsLocalProperty`|Atrybut opcjonalny.<br /><br /> Nazwy właściwości, które nie będą uznawane globalnego. Ten atrybut zapobiega zastępowanie wartości właściwości, które są ustawiane w pliku projektu lub miejsc docelowych i wszystkie Importy kolejnych właściwości specyficzne dla wiersza polecenia. Wiele właściwości są średnikami (;) przecinkami.<br /><br /> Zazwyczaj właściwości globalne zastąpić wartości właściwości, które są ustawione w pliku projektu lub miejsc docelowych. Jeśli właściwość jest wymieniony na liście `TreatAsLocalProperty` wartości, wartość właściwości globalnej nie zastąpi wartości właściwości, które są ustawiane w pliku i wszystkie Importy kolejne. Aby uzyskać więcej informacji, zobacz [porady: tworzenie tych samych plików źródłowych przy użyciu różnych opcji](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Uwaga:** globalnych właściwości są ustawiane w wierszu polecenia przy użyciu **/property** (lub **/p**) przełącznika. Możesz również ustawić lub zmodyfikować globalnych właściwości dla projektów podrzędnych w kompilacji wielu projektów za pomocą `Properties` atrybut zadanie programu MSBuild. Aby uzyskać więcej informacji, zobacz [zadanie programu MSBuild](../msbuild/msbuild-task.md).|  
|`Xmlns`|Atrybut opcjonalny.<br /><br /> W przypadku `xmlns` atrybut musi mieć wartość "http://schemas.microsoft.com/developer/msbuild/2003".|  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Wybierz pozycję](../msbuild/choose-element-msbuild.md)|Element opcjonalny.<br /><br /> Oblicza elementy podrzędne, aby wybrać jeden zestaw `ItemGroup` elementów i/lub `PropertyGroup` elementy do oceny.|  
|[Import](../msbuild/import-element-msbuild.md)|Element opcjonalny.<br /><br /> Włącza plik projektu do zaimportowania innego pliku projektu. Może wynosić zero lub więcej `Import` elementów w projekcie.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Element grouping dla poszczególnych elementów. Elementy są określane przy użyciu [elementu](../msbuild/item-element-msbuild.md) elementu. Może wynosić zero lub więcej `ItemGroup` elementów w projekcie.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|Element opcjonalny.<br /><br /> Zapewnia sposób utrwalić z systemem innym niż[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] informacji w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu. Może być zero lub jeden `ProjectExtensions` elementów w projekcie.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Element grouping dla poszczególnych właściwości. Właściwości są określane przy użyciu [właściwości](../msbuild/property-element-msbuild.md) elementu. Może wynosić zero lub więcej `PropertyGroup` elementów w projekcie.|
|[Sdk](../msbuild/sdk-element-msbuild.md)|Element opcjonalny.<br /><br /> Odwołania [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt zestawu SDK.  Ten element może służyć jako alternatywę do atrybutu zestawu Sdk.|  
|[Docelowy](../msbuild/target-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw zadań związanych z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do wykonania po kolei. Zadania są określane przy użyciu [zadań](../msbuild/task-element-msbuild.md) elementu. Może wynosić zero lub więcej `Target` elementów w projekcie.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Element opcjonalny.<br /><br /> Zapewnia sposób rejestrowania zadań w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Może wynosić zero lub więcej `UsingTask` elementów w projekcie.|  

### <a name="parent-elements"></a>Elementy nadrzędne  
 Brak.  

## <a name="see-also"></a>Zobacz też  
 [Porady: Określanie obiektu docelowego do kompilacji najpierw](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
