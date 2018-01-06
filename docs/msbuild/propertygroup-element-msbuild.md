---
title: "PropertyGroup — Element (MSBuild) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
caps.latest.revision: "21"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 326902431193d280c8f345f4ee9dde145bcac614
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup — Element (MSBuild)
Zawiera zestaw zdefiniowanych przez użytkownika [właściwości](../msbuild/property-element-msbuild.md) elementów. Każdy `Property` element używany w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu musi być elementem podrzędnym elementu `PropertyGroup` elementu.  

 \<Projekt >  
 \<PropertyGroup >  

## <a name="syntax"></a>Składnia  

```  
<PropertyGroup Condition="'String A' == 'String B'">  
    <Property1>...</Property1>  
    <Property2>...</Property2>  
</PropertyGroup>  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|Warunek|Atrybut opcjonalny.<br /><br /> Warunek do sprawdzenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Właściwość](../msbuild/property-element-msbuild.md)|Element opcjonalny.<br /><br /> Właściwości zdefiniowane nazwę użytkownika, który zawiera wartość właściwości. Może wynosić zero lub więcej *właściwości* elementów w `PropertyGroup` elementu.|  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Wymaganego głównego elementu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu.|  

## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób ustawiania właściwości na podstawie warunku. W tym przykładzie Jeśli wartość `CompileConfig` właściwość jest `DEBUG`, `Optimization`, `Obfuscate`, i `OutputPath` właściwości wewnątrz `PropertyGroup` ustawiono element.  

```xml  
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >  
    <Optimization>false</Optimization>  
    <Obfuscate>false</Obfuscate>  
    <OutputPath>$(OutputPath)\debug</OutputPath>  
</PropertyGroup>  
```  

## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)  
 [Właściwości programu MSBuild](../msbuild/msbuild-properties.md)
