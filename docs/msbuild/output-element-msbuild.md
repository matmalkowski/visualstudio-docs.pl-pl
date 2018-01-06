---
title: "OUTPUT — Element (MSBuild) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: abeb4b0f4a34270b8b4ae4155cac910c08cf5f0b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="output-element-msbuild"></a>Output — Element (MSBuild)
Magazyny wartości danych wyjściowych zadania w elementów i właściwości.  

 \<Projekt >  
 \<Docelowy >  
 \<Zadanie >  
 \<Dane wyjściowe >  

## <a name="syntax"></a>Składnia  

```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`TaskParameter`|Atrybut wymagany.<br /><br /> Parametr wyjściowy nazwę zadania.|  
|`PropertyName`|Albo `PropertyName` lub `ItemName` atrybut jest wymagany.<br /><br /> Właściwość, która odbiera zadanie wyjściowy wartość parametru. Projekt można odwołać właściwości o `$(` *PropertyName* `)` składni. Nazwa tej właściwości może być nową nazwę właściwości lub nazwę, która jest już zdefiniowany w projekcie.<br /><br /> Nie można użyć tego atrybutu, jeśli `ItemName` jest również używany.|  
|`ItemName`|Albo `PropertyName` lub `ItemName` atrybut jest wymagany.<br /><br /> Wartość parametru wyjściowy element, który odbiera zadania. Projekt można odwołać elementu z `@(` *ItemName* `)` składni. Nazwa elementu może być nową nazwę elementu lub nazwę, która jest już zdefiniowany w projekcie.<br /><br /> Nie można użyć tego atrybutu, jeśli `PropertyName` jest również używany.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do sprawdzenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Zadanie](../msbuild/task-element-msbuild.md)|Tworzy i wykonuje wystąpienia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań.|  

## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład `Csc` zadań wykonywana wewnątrz `Target` elementu. Elementy i właściwości przekazywane do parametrów zadań są deklarowane jako poza zakres tego przykładu. Wartość parametru wyjściowego `OutputAssembly` są przechowywane w `FinalAssemblyName` elementu, a wartość parametru wyjściowego `BuildSucceeded` są przechowywane w `BuildWorked` właściwości. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).  

```xml  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)
