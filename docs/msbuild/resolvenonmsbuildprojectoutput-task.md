---
title: "Resolvenonmsbuildprojectoutput — zadanie | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 82928797c912aac24d41d63d865e575ea90c013e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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