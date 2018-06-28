---
title: Rozpakuj zadań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Unzip
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Unzip task [MSBuild]
- MSBuild, Unzip task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a46f2a079cc35e6c1add9e53abdcbdd283ddb9e
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37059341"
---
# <a name="unzip-task"></a>Unzip — zadanie
Unzips `.zip` archiwum do określonej lokalizacji.

**Uwaga:** `Unzip` zadanie jest dostępne w MSBuild 15.8 i powyżej tylko.
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Unzip` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`DestinationFolder`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru<br /><br /> Określa, aby rozpakować plik do folderu docelowego.|
|`OverwriteReadOnlyFiles`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zastępuje pliki tylko do odczytu. Domyślnie `false`.|
|`SkipUnchangedFiles`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, pomija rozpakować pliki, które uległy zmianie. Domyślnie `true`. Zadanie `Unzip` uznaje pliki za niezmienione, jeśli mają taki sam rozmiar i taki sam czas ostatniej modyfikacji.|
|`SourceFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa jeden lub więcej plików do rozpakowania. Podczas określania wielu plików, są one rozpakowane w kolejności, w tym samym folderze.|
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład unzips archiwum i zastępuje pliki tylko do odczytu.
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="UnzipArchive" BeforeTargets="Build">
        <Unzip
            SourceFiles="MyArchive.zip"
            DestinationFolder="$(OutputPath)\unzipped"
            OverwriteReadOnlyFiles="true"
        />
    </Target>

</Project>
```
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
