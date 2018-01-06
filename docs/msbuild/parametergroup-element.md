---
title: "Parametergroup — Element | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/13/2017
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
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f5ec46e5d6aea28a4124447c0f541cfb71e2f62f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="parametergroup-element"></a>Parametergroup — Element
Zawiera opcjonalną listę parametrów, które będą znajdować się na zadania, które są generowane przez `UsingTask``TaskFactory`. Aby uzyskać więcej informacji, zobacz [usingtask — Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Projekt >  
 \<UsingTask >  
 \<Parametergroup — >  

## <a name="syntax"></a>Składnia  

```  
<ParameterGroup />  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  
 Brak.  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Parametr](../msbuild/parameter-element.md)|Zawiera informacje na temat określonego parametru dla zadania, które są generowane przez `UsingTask``TaskFactory`. Nazwa elementu jest nazwą parametru.|  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Zapewnia sposób rejestrowania zadań w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Może wynosić zero lub więcej `UsingTask` elementów w projekcie.|  

## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `ParameterGroup` elementu.  

```xml  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  

## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
