---
title: Getframeworksdkpath — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44d128df04ef13ea6ee4b5b20368b5932842cc3d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath — Zadanie
Pobiera ścieżkę do [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `GetFrameworkSdkPath` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Opcjonalne `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu .NET SDK w wersji 2.0, jeśli jest obecny. W przeciwnym razie zwraca `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Opcjonalne `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu .NET SDK w wersji 3.5, jeśli jest obecny. W przeciwnym razie zwraca `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Opcjonalne `String` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca ścieżkę do zestawu .NET SDK w wersji 4.0, jeśli jest obecny. W przeciwnym razie zwraca `String.Empty`.|  
|`Path`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Zawiera ścieżkę do najnowszego zestawu .NET SDK, jeśli jakakolwiek wersja jest obecny. W przeciwnym razie zwraca `String.Empty`.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `GetFrameworkSdkPath` zadań do ścieżki do przechowywania [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] w `SdkPath` właściwości.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)