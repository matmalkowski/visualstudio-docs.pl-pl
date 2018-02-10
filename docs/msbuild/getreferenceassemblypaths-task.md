---
title: "Getreferenceassemblypaths — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6063ca7f69d5dd04c0675090eb6c6deb3075bdf5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths — Zadanie
Zwraca odwołanie ścieżki zestawu z różnych platform.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `GetReferenceAssemblyPaths` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Opcjonalne `String[]` parametru wyjściowego.<br /><br /> Zwraca ścieżkę, w oparciu o `TargetFrameworkMoniker` parametru. Jeśli `TargetFrameworkMoniker` ma wartość null lub pusty, ta ścieżka będzie `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Opcjonalne `String[]` parametru wyjściowego.<br /><br /> Zwraca ścieżkę, w oparciu o `TargetFrameworkMoniker` parametru, bez uwzględniania częścią profilu moniker. Jeśli `TargetFrameworkMoniker` ma wartość null lub pusty, ta ścieżka będzie `String.Empty`.|  
|`TargetFrameworkMoniker`|Opcjonalne `String` parametru.<br /><br /> Określa, który jest skojarzony z ścieżek zestawu odwołania moniker platformy docelowej.|  
|`RootPath`|Opcjonalne `String` parametru.<br /><br /> Określa ścieżkę katalogu głównego, można użyć w celu wygenerowania ścieżki zestawu odwołania.|  
|`BypassFrameworkInstallChecks`|Opcjonalne <xref:System.Boolean> parametru.<br /><br /> Jeśli `true`, pomija podstawowe sprawdzanie który `GetReferenceAssemblyPaths` wykonuje domyślnie, aby upewnić się, że niektórych platform środowiska uruchomieniowego są zainstalowane, w zależności od platformy docelowej.|  
|`TargetFrameworkMonikerDisplayName`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Określa nazwę wyświetlaną dla moniker platformy docelowej.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)