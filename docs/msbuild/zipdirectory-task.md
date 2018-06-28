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
ms.openlocfilehash: e0d818c6ffbef8502634e80903f6cf1dc853e6ce
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37059340"
---
# <a name="zipdirectory-task"></a>Zadanie ZipDirectory
Tworzy `.zip` archiwum z zawartości katalogu.

**Uwaga:** `ZipDirectory` zadanie jest dostępne w MSBuild 15.8 i powyżej tylko.
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `ZipDirectory` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`DestinationFile`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru<br /><br /> Pełna ścieżka do `.zip` pliku w celu utworzenia.|
|`Overwrite`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, pomija plik docelowy zostanie zastąpiony, jeśli istnieje. Domyślnie `false`.|
|`SourceDirectory`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa katalog, aby utworzyć `.zip` archiwum z.|
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy `.zip` archiwum z katalogu wyjściowego po utworzeniu projektu.
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <ZipOutputPath>$(MSBuildProjectDirectory)</ZipOutputPath>
    </PropertyGroup>

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip">
        />
    </Target>

</Project>
```
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
