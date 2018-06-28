---
title: Zadanie DownloadFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f8a5a5ab1f1ca86b0378b14e666c8569a01fb27
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37059342"
---
# <a name="downloadfile-task"></a>Zadanie DownloadFile
Pobiera określone pliki przy użyciu funkcji Hyper-tekst transferu protokołu (HTTP).

**Uwaga:** `DownloadFile` zadanie jest dostępne w MSBuild 15.8 i powyżej tylko.
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `DownloadFile` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`DestinationFileName`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru<br /><br /> Nazwa do użycia dla pobranego pliku.  Domyślnie, nazwa pliku jest pochodną `SourceUrl` lub serwerze zdalnym.|
|`DestinationFolder`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa można pobrać pliku do folderu docelowego.  Jeśli folder jest tworzony, jeśli nie istnieje.|
|`DownloadedFile`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru wyjściowego.<br /><br /> Określa plik, który został pobrany.|
|`Retries`|Opcjonalne `Int32` parametru.<br /><br /> Określa, ile razy próbuje pobrać, jeśli wszystkie poprzednich prób. Domyślnie przyjmuje wartość zero.|  
|`RetryDelayMilliseconds`|Opcjonalne `Int32` parametru.<br /><br /> Określa opóźnienie w milisekundach między wszelkie niezbędne ponownych prób. Wartość domyślna to 5000.|  
|`SkipUnchangedFiles`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, pomijając pobieranie plików, które uległy zmianie. Domyślnie `true`. `DownloadFile` Zadań traktuje plików, które będą bez zmian, jeśli mają ten sam rozmiar i takie same Data ostatniej modyfikacji zgodnie z serwerem zdalnym. **Uwaga:** nie wszystkie serwery HTTP wskazuje datę ostatniej modyfikacji plików spowoduje, że plik zostać pobrana ponownie.|
|`SourceUrl`|Wymagane `String` parametru.<br /><br /> Określa adres URL do pobrania.|
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Pobiera plik, w tym w następującym przykładzie `Content` elementów przed skompilowanie projektu.
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>  
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>  

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
