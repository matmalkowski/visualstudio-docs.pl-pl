---
title: "Assignprojectconfiguration — zadanie | Dokumentacja firmy Microsoft"
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
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2362eb55d0744c67b83725d0cabb059516b2eddb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration — Zadanie
To zadanie akceptuje listy ciągów konfiguracji i przypisuje je do określonych projektów.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `AssignProjectConfiguration` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`SolutionConfigurationContents`|Opcjonalne `string` parametru wyjściowego.<br /><br /> Zawiera ciąg XML zawierający konfigurację projektu dla każdego projektu. Konfiguracje są przypisane do nazwanego projektów.|  
|`DefaultToVcxPlatformMapping`|Opcjonalne `string` parametru wyjściowego.<br /><br /> Zawiera rozdzielaną średnikami listę mapowań z nazwy platformy używane<br /><br /> przez większość typów do używanych przez .vcxproj plików.<br /><br /> Na przykład:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|  
|`VcxToDefaultPlatformMapping`|Optional<br /><br /> `string`Parametr wyjściowy.<br /><br /> Zawiera rozdzielaną średnikami listę mapowania nazw platformy .vcxproj do używania nazwy platformy przez większość typów.<br /><br /> Na przykład:<br /><br /> `"Win32=AnyCPU;X64=X64"`|  
|`CurrentProjectConfiguration`|Opcjonalne `string` parametru wyjściowego.<br /><br /> Zawiera konfigurację dla bieżącego projektu.|  
|`CurrentProjectPlatform`|Opcjonalne `string` parametru wyjściowego.<br /><br /> Zawiera platformy dla bieżącego projektu.|  
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Opcjonalne `bool` parametru wyjściowego.<br /><br /> Zawiera nieobsługiwaną flagę wskazującą, czy odwołania powinny zostać skompilowane, nawet jeśli zostały one wyłączone w konfiguracji projektu.|  
|`ShouldUnsetParentConfigurationAndPlatform`|Opcjonalne `bool` parametru wyjściowego.<br /><br /> Zawiera nieobsługiwaną flagę wskazującą, jeśli platforma i konfiguracji nadrzędnej powinny być unset.|  
|`OutputType`|Opcjonalne `string` parametru wyjściowego.<br /><br /> Zawiera typ danych wyjściowych dla projektu.|  
|`ResolveConfigurationPlatformUsingMappings`|Opcjonalne `bool` parametru wyjściowego.<br /><br /> Zawiera nieobsługiwaną flagę wskazującą, czy kompilacji powinni używać domyślnych mapowań do rozpoznawania Konfiguracja i platforma przekazany w odwołaniach projektu.|  
|`AssignedProjects`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera listę ścieżek rozpoznane odwołania.|  
|`UnassignedProjects`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera listę elementów odwołanie do projektu, których nie można rozpoznać przy użyciu wstępnie rozpoznać listy danych wyjściowych.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)