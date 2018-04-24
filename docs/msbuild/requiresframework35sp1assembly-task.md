---
title: Requiresframework35sp1assembly — zadanie | Dokumentacja firmy Microsoft
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
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7317c6cdadb36d4221b98cd47cf92ca23e99cb52
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly — Zadanie
Określa, czy aplikacja wymaga platformy .NET Framework 3.5 SP1.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `RequiresFramework35SP1Assembly` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Assemblies`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa zestawy, do których istnieją odwołania w aplikacji.|  
|`CreateDesktopShortcut`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, tworzy ikonę skrótu na pulpicie podczas instalacji.|  
|`DeploymentManifestEntryPoint`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa nazwę pliku manifestu aplikacji.|  
|`EntryPoint`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa zestaw, który ma być wykonany po uruchomieniu aplikacji.|  
|`ErrorReportUrl`|Opcjonalne `String` parametru.<br /><br /> Określa witryny sieci Web, która jest wyświetlana w oknach dialogowych, które wystąpią podczas instalacji ClickOnce.|  
|`Files`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa listę plików, które zostaną wdrożone, gdy aplikacja zostanie opublikowana.|  
|`ReferencedAssemblies`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa zestawy, do których istnieją odwołania w projekcie.|  
|`RequiresMinimumFramework35SP1`|Opcjonalne `Boolean` parametru wyjściowego.<br /><br /> Jeśli `true`, aplikacja wymaga platformy .NET Framework 3.5 SP1.|  
|`SigningManifests`|Opcjonalne `Boolean` parametru wyjściowego.<br /><br /> Jeśli `true`, manifesty ClickOnce są podpisane.|  
|`SuiteName`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę folderu na **Start** menu, w którym zostanie zainstalowana aplikacja.|  
|`TargetFrameworkVersion`|Opcjonalne `String` parametru.<br /><br /> Określa wersję systemu .NET Framework tego celów aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)