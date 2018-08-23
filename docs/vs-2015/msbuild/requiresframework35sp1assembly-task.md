---
title: Requiresframework35sp1assembly — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0ffc3b685314983949026a67f9be95f0fce1245
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677157"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [requiresframework35sp1assembly — zadanie](https://docs.microsoft.com/visualstudio/msbuild/requiresframework35sp1assembly-task).  
  
  
Określa, czy aplikacja wymaga .NET Framework 3.5 SP1.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `RequiresFramework35SP1Assembly` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Assemblies`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa zestawy, do których istnieją odwołania w aplikacji.|  
|`CreateDesktopShortcut`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, tworzy ikonę skrótu na pulpicie podczas instalacji.|  
|`DeploymentManifestEntryPoint`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa nazwę pliku manifestu aplikacji.|  
|`EntryPoint`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa zestaw, który ma być wykonany po uruchomieniu aplikacji.|  
|`ErrorReportUrl`|Opcjonalnie `String` parametru.<br /><br /> Określa witryny sieci Web, która jest wyświetlana w oknach dialogowych, które zostaną napotkane podczas instalacji ClickOnce.|  
|`Files`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa listę plików, które zostaną wdrożone, gdy aplikacja została opublikowana.|  
|`ReferencedAssemblies`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa zestawy, do których istnieją odwołania w projekcie.|  
|`RequiresMinimumFramework35SP1`|Opcjonalnie `Boolean` parametr wyjściowy.<br /><br /> Jeśli `true`, aplikacja wymaga .NET Framework 3.5 SP1.|  
|`SigningManifests`|Opcjonalnie `Boolean` parametr wyjściowy.<br /><br /> Jeśli `true`, manifesty ClickOnce są podpisane.|  
|`SuiteName`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę folderu na **Start** menu, w którym aplikacja zostanie zainstalowana.|  
|`TargetFrameworkVersion`|Opcjonalnie `String` parametru.<br /><br /> Określa wersję programu .NET, że cele aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)



