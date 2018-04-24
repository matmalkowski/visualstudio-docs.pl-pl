---
title: Resolvenonmsbuildprojectoutput — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f26798c4fd76cdb7ec06c843f50e177f94a68bb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput — Zadanie
Określa pliki wyjściowe dla innych niż MSBuild odwołania do projektu.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `ResolveNonMSBuildProjectOutput` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Opcjonalne `String` parametru.<br /><br /> Określa, że ciąg XML, który zawiera rozpoznać wyjścia projektu.|  
|`ProjectReferences`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa odwołania do projektu.|  
|`ResolvedOutputPaths`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera listę ścieżek rozpoznane odwołania (i zachowuje oryginalne atrybutów odwołania projektu).|  
|`UnresolvedProjectReferences`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera listę elementów odwołanie projektu nie można rozpoznać przy użyciu preresolved wykaz danych wyjściowych.<br /><br /> Ponieważ program Visual Studio preresolves tylko innych niż MSBuild projektów, oznacza to, że odwołania projektu na tej liście są w formacie programu MSBuild.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)