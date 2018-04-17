---
title: Getframeworkpath — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db4bb2c17e0bbfa624782c3c31e02ef55746385c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath — Zadanie
Pobiera ścieżkę do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zestawów.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `GetFrameworkPath` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Zawiera ścieżkę do zestawów platformy w wersji 1.1, jeśli jest obecny. W przeciwnym razie zwraca `null`.|  
|`FrameworkVersion20Path`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Zawiera ścieżkę do zestawów platformy w wersji 2.0, jeśli jest obecny. W przeciwnym razie zwraca `null`.|  
|`FrameworkVersion30Path`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Zawiera ścieżkę do zestawów platformy w wersji 3.0, jeśli jest obecny. W przeciwnym razie zwraca `null`.|  
|`FrameworkVersion35Path`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Zawiera ścieżkę do zestawów w wersji 3.5 framework, jeśli jest obecny. W przeciwnym razie zwraca `null`.|  
|`FrameworkVersion40Path`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Zawiera ścieżkę do zestawów platformy w wersji 4.0, jeśli jest obecny. W przeciwnym razie zwraca `null`.|  
|`Path`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Zawiera ścieżkę do najnowszej zestawów platformy, jeśli są dostępne. W przeciwnym razie zwraca `null`.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli kilka wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] są instalowane, to zadanie zwraca informacje o wersji który [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] przeznaczony do uruchamiania.  
  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `GetFrameworkPath` zadań do ścieżki do przechowywania [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] w `FrameworkPath` właściwości.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)