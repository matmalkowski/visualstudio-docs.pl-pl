---
title: Parametr elementu | Dokumentacja firmy Microsoft
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
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 39dd727eee6f9af2f60410c4dbfc9daa9ea805a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="parameter-element"></a>Parameter — Element
Zawiera informacje na temat określonego parametru dla zadania, które są generowane przez `UsingTask``TaskFactory`.  Nazwa elementu jest nazwą parametru.  Aby uzyskać więcej informacje, zobacz [usingtask — Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Projekt >  
 \<UsingTask >  
 \<Parametergroup — >  
 \<Parametr >  

## <a name="syntax"></a>Składnia  

```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`ParameterType`|Atrybut opcjonalny.<br /><br /> Typ architektury .NET parametru, na przykład "System.String".|  
|`Output`|Opcjonalny logiczny atrybut.<br /><br /> Jeśli `true`, ten parametr jest parametrem wyjściowym dla zadania. Domyślna wartość to `false`.|  
|`Required`|Opcjonalny logiczny atrybut.<br /><br /> Jeśli `true`, ten parametr jest wymagany parametr zadania. Domyślna wartość to `false`.|  

### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Parametergroup —](../msbuild/parametergroup-element.md)|Zawiera opcjonalną listę parametrów, które będą znajdować się na zadania, które są generowane przez `UsingTask``TaskFactory`.|  

## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Parameter` elementu.  

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
