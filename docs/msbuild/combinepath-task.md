---
title: Combinepath — zadanie | Dokumentacja firmy Microsoft
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
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9efb3a997eb0e6aa0d731f4fbf5d9d8ce0e9e978
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="combinepath-task"></a>CombinePath — Zadanie
Scala określonych ścieżek w pojedynczą ścieżkę.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry [combinepath — zadanie](../msbuild/combinepath-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BasePath`|Wymagane `String` parametru.<br /><br /> Podstawowa ścieżka do łączenia z innych ścieżek. Może to być ścieżka względna, ścieżka bezwzględna lub pusty.|  
|`Paths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista poszczególnych ścieżek do łączenia z nieistniejący do utworzenia połączonym ścieżki. Ścieżki może być względna lub bezwzględna.|  
|`CombinedPaths`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Połączone ścieżki, który jest tworzony przez to zadanie.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)