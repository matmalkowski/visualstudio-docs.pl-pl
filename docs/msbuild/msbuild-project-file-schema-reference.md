---
title: "Odwołanie do schematu pliku projektu MSBuild | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords: MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: "19"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: a88962b87466a2345ac8dafa642d457a6fee5be0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-project-file-schema-reference"></a>Odwołanie do schematu pliku projektu MSBuild
Zawiera spis wszystkich [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] elementów schematu XML z dostępne atrybuty i elementy podrzędne.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]używa plików projektu aby nakazać co aparatu kompilacji do kompilacji i sposobie jego tworzenia. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]pliki projektu będą stosować się do plików XML [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] schematu XML. W tej sekcji omówiono plik definicji (XSD) schematu XML dla [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## <a name="msbuild-xml-schema-elements"></a>Elementy schematu XML programu MSBuild  
 W poniższej tabeli wymieniono wszystkie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] elementów schematu XML wraz z ich elementów podrzędnych i atrybutów.  
  
|Element|Elementy podrzędne|Atrybuty|  
|-------------|--------------------|----------------|  
|[Choose — Element (MSBuild)](../msbuild/choose-element-msbuild.md)|w przeciwnym razie<br /><br /> Kiedy|--|  
|[Import — Element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Warunek<br /><br /> Project|  
|[Importgroup — Element](../msbuild/importgroup-element.md)|Import|Warunek|  
|[Item — Element (MSBuild)](../msbuild/item-element-msbuild.md)|*Itemmetadata —*|Warunek<br /><br /> Wyklucz<br /><br /> Uwzględnij<br /><br /> Usuń|  
|[ItemDefinitionGroup — Element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Element*|Warunek|  
|[ItemGroup — Element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Element*|Warunek|  
|[Itemmetadata — Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Element*|Warunek|  
|[OnError — Element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Warunek<br /><br /> ExecuteTargets|  
|[Otherwise — Element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Wybierz<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[OUTPUT — Element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Warunek<br /><br /> Nazwa elementu<br /><br /> PropertyName<br /><br /> TaskParameter|  
|[Parameter — Element](../msbuild/parameter-element.md)|--|Dane wyjściowe<br /><br /> ParameterType<br /><br /> Wymagane|  
|[Parametergroup — Element](../msbuild/parametergroup-element.md)|*Parametr*|--|  
|[Project — Element (MSBuild)](../msbuild/project-element-msbuild.md)|Wybierz<br /><br /> Import<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> docelowy<br /><br /> UsingTask|Defaulttargets —<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|  
|[ProjectExtensions — Element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Property — Element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Warunek|  
|[PropertyGroup — Element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Właściwość*|Warunek|  
|[TARGET — Element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError —<br /><br /> *Zadanie*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Warunek<br /><br /> DependsOnTargets<br /><br /> Dane wejściowe<br /><br /> KeepDuplicateOutputs<br /><br /> Nazwa<br /><br /> Dane wyjściowe<br /><br /> Zwraca|  
|[Task — Element (MSBuild)](../msbuild/task-element-msbuild.md)|Dane wyjściowe|Warunek<br /><br /> ContinueOnError<br /><br /> *Parametr*|  
|[Taskbody — Element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Dane*|Ocena|  
|[Usingtask — Element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|Parametergroup —<br /><br /> Taskbody —|AssemblyFile<br /><br /> AssemblyName<br /><br /> Warunek<br /><br /> Fabryka zadań<br /><br /> TaskName|  
|[Gdy Element (MSBuild)](../msbuild/when-element-msbuild.md)|Wybierz<br /><br /> ItemGroup<br /><br /> PropertyGroup|Warunek|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Warunki](../msbuild/msbuild-conditions.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)