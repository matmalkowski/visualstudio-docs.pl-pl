---
title: "Makedir — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#MakeDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MakeDir task [MSBuild]
- MSBuild, MakeDir task
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
caps.latest.revision: "14"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 23586200e0f50b8d0fdae5a05780e894c38020d6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="makedir-task"></a>MakeDir — Zadanie
Tworzy katalogi i w razie potrzeby dominujące katalogów.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `MakeDir` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Directories`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Zestaw katalogów do utworzenia.|  
|`DirectoriesCreated`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Katalogi, które są tworzone przez to zadanie. Jeśli nie można utworzyć niektórych katalogów, to może nie zawierać wszystkich elementów, które zostały przekazane do `Directories` parametru.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `MakeDir` zadanie tworzenia katalogu określonego przez `OutputDirectory` właściwości.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
    </PropertyGroup>  
  
    <Target Name="CreateDirectories">  
        <MakeDir  
            Directories="$(OutputDirectory)"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)