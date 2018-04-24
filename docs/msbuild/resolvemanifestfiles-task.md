---
title: Resolvemanifestfiles — zadanie | Dokumentacja firmy Microsoft
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
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d08b22f75df3715f499481880fa764ce6ebc563c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles — Zadanie
Rozpoznaje następujących elementów w procesie kompilacji do plików do generowania manifestu: wbudowane elementy, zależności satelity, zawartość, symbole debugowania i dokumentacji.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `ResolveManifestFiles` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`DeploymentManifestEntryPoint`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa nazwę manifestu rozmieszczenia.|  
|`EntryPoint`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa zestaw zarządzany lub ClickOnce manifestu odwołanie do punktu wejścia do manifestu.|  
|`ExtraFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa dodatkowe pliki.|  
|`ManagedAssemblies`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa zestawów zarządzanych.|  
|`NativeAssemblies`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa zestawy, macierzystego.|  
|`OutputAssemblies`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Określa zestawy, wygenerowany.|  
|`OutputDeploymentManifestEntryPoint`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru wyjściowego.<br /><br /> Określa punkt wejścia manifestu wdrożenia danych wyjściowych.|  
|`OutputEntryPoint`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru wyjściowego.<br /><br /> Określa punkt wejścia danych wyjściowych.|  
|`OutputFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Określa pliki wyjściowe.|  
|`PublishFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa pliki publikowania.|  
|`SatelliteAssemblies`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa, czy zestawy satelickie|  
|`SigningManifests`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, manifesty są podpisane.|  
|`TargetCulture`|Opcjonalne `String` parametru.<br /><br /> Określa zestawy satelickie kulturze docelowej.|  
|`TargetFrameworkVersion`|Opcjonalne `String` parametru.<br /><br /> Określa docelową wersję platformy .NET.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)