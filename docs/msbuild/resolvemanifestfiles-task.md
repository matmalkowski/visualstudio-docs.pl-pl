---
title: "Resolvemanifestfiles — zadanie | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 1cb70f44046b6b0e964bb87ba1824518976897ad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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