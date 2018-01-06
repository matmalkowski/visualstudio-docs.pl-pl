---
title: "Resolvenativereference — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: "9"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5d2b7cffec4dc9e321ab9468ce57232e82087eab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference — Zadanie
Usuwa odwołania natywnego. Implementuje <xref:Microsoft.Build.Tasks.ResolveNativeReference> klasy. Ta klasa obsługuje infrastrukturę programu .NET Framework, która nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `ResolveNativeReference` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|Wymagany parametr interfejsu <xref:System.String?displayProperty=fullName>`[]`.<br /><br /> Pobiera lub ustawia Przeszukuj ścieżki pod kątem rozpoznawania tożsamości zestawu macierzystego odwołań.|  
|`ContainedComComponents`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Pobiera lub ustawia składniki COM natywny zestaw.|  
|`ContainedLooseEtcFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Pobiera lub ustawia utracić Etc pliki wymienione w manifeście macierzystego.|  
|`ContainedLooseTlbFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Pobiera lub ustawia plików .tlb utracić zestawu macierzystego.|  
|`ContainedPrerequisiteAssemblies`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Pobiera lub ustawia zestawy, które musi znajdować się przed użyciem manifestu.|  
|`ContainedTypeLibraries`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Pobiera lub ustawia bibliotek typu macierzystego zestawu.|  
|`ContainingReferenceFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Pobiera lub ustawia pliki odwołania.|  
|`NativeReferences`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Pobiera lub ustawia odwołania do zestawów natywnych Win32.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)