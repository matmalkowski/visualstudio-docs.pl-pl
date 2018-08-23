---
title: OnError — Element (MSBuild) | Dokumentacja firmy Microsoft
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
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 323aff310061cf62af7cac10ee266c15d24e6eae
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42697038"
---
# <a name="onerror-element-msbuild"></a>OnError — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [OnError — Element (MSBuild)](https://docs.microsoft.com/visualstudio/msbuild/onerror-element-msbuild).  
  
  
Powoduje, że jeden lub więcej celów do wykonania, jeśli `ContinueOnError` atrybut jest `false` dla zadania nie powiodło się.  
  
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
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczone. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Atrybut wymagany.<br /><br /> Cele do wykonania, jeśli zadanie nie powiedzie się. Wiele elementów docelowych należy oddzielić średnikami. Wiele elementów docelowych są wykonywane w określonej kolejności.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Docelowy](../msbuild/target-element-msbuild.md)|Element kontenera służy do [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zadania.|  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wykonuje `OnError` elementu, jeśli jest to jeden z `Target` elementu zadań kończy się niepowodzeniem z `ContinueOnError` ustawioną wartość atrybutu `ErrorAndStop` (lub `false`). Jeśli zadanie nie powiedzie się, obiektów docelowych określonych w `ExecuteTargets` atrybutu jest wykonywany. Jeśli istnieje więcej niż jedna `OnError` elementu w miejscu docelowym, `OnError` elementy są wykonywane sekwencyjnie, gdy zadanie nie powiodło się.  
  
 Aby uzyskać informacje o `ContinueOnError` atrybutów, zobacz [Task — Element (MSBuild)](../msbuild/task-element-msbuild.md). Aby uzyskać informacje o środowiskach docelowych, zobacz [cele](../msbuild/msbuild-targets.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod wykonuje `TaskOne` i `TaskTwo` zadania. Jeśli `TaskOne` zakończy się niepowodzeniem, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ocenia `OnError` elementu i wykonuje `OtherTarget` docelowej.  
  
```  
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



