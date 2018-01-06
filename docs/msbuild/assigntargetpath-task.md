---
title: "Assigntargetpath — zadanie | Dokumentacja firmy Microsoft"
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
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 144b8b82209b63262db8b7a25f2478b9a4c89edb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assigntargetpath-task"></a>AssignTargetPath — Zadanie
To zadanie akceptuje listę plików i dodaje `<TargetPath>` atrybuty, jeśli nie są już określony.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `AssignTargetPath` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`RootFolder`|Opcjonalne `string` parametru wejściowego.<br /><br /> Zawiera ścieżkę do folderu, który zawiera łącza docelowego.|  
|`Files`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wejściowego.<br /><br /> Zawiera listę plików przychodzących.|  
|`AssignedFiles`|Optional<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametru wyjściowego.<br /><br /> Zawiera wynikowa lista plików.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje `AssignTargetPath` zadanie, aby skonfigurować projekt.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)