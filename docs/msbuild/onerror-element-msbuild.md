---
title: "OnError — Element (MSBuild) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ed8d48fe390f5a5990506a6b7eeab3d1efe8b5ed
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="onerror-element-msbuild"></a>OnError — Element (MSBuild)
Powoduje, że jeden lub więcej celów do wykonania, jeśli `ContinueOnError` atrybutu `false` zadania nie powiodło się.  

 \<Project>  
 \<Docelowy >  
 \<OnError — >  

## <a name="syntax"></a>Składnia  

```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do sprawdzenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Atrybut wymagany.<br /><br /> Cele do wykonania, jeśli zadanie nie powiedzie się. Wiele obiektów docelowych należy rozdzielić średnikami. Wiele obiektów docelowych są wykonywane w określonej kolejności.|  

### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Docelowy](../msbuild/target-element-msbuild.md)|Element kontenera dla [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadania.|  

## <a name="remarks"></a>Uwagi  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wykonuje `OnError` elementu, jeśli jeden z `Target` elementu zadań kończy się niepowodzeniem z `ContinueOnError` ustawić atrybutu `ErrorAndStop` (lub `false`). Jeśli zadanie nie powiedzie się, cele określone w `ExecuteTargets` atrybutu jest wykonywana. Jeśli istnieje więcej niż jeden `OnError` elementu w miejscu docelowym `OnError` elementy są wykonywane sekwencyjnie, gdy zadanie nie powiodło się.  

 Aby uzyskać informacje o `ContinueOnError` atrybutów, zobacz [Task — Element (MSBuild)](../msbuild/task-element-msbuild.md). Informacje dla celów, zobacz [cele](../msbuild/msbuild-targets.md).  

## <a name="example"></a>Przykład  
 Poniższy kod wykonuje `TaskOne` i `TaskTwo` zadania. Jeśli `TaskOne` zakończy się niepowodzeniem, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ocenia `OnError` element i wykonuje `OtherTarget` docelowej.  

```xml  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  

## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Docelowe elementy](../msbuild/msbuild-targets.md)
