---
title: Zadanie ZipDirectory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0dbd45d32e2268a687d09c48527acb1a6df0bff5
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468367"
---
# <a name="zipdirectory-task"></a>Zadanie ZipDirectory
Tworzy *zip* archiwum z zawartości katalogu.

>[!NOTE]
>`ZipDirectory` Zadanie jest dostępne w MSBuild 15.8 i nowszym tylko.
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `ZipDirectory` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`DestinationFile`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru<br /><br /> Pełna ścieżka do *zip* pliku do utworzenia.|
|`Overwrite`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, pomija docelowego pliku zostaną zastąpione, jeśli taki istnieje. Wartość domyślna to `false`.|
|`SourceDirectory`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa katalog, aby utworzyć *zip* archiwum z.|
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy *zip* archiwum z katalogu wyjściowego Po skompilowaniu projektu.
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip">
        />
    </Target>

</Project>
```
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
