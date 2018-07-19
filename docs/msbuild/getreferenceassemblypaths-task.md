---
title: GetReferenceAssemblyPaths, zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1041a298b7b195180e312e54aeadd666b478cb29
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37946823"
---
# <a name="getreferenceassemblypaths-task"></a>Getreferenceassemblypaths — zadanie
Zwraca odwołanie ścieżki zestawów w różnych architektur.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `GetReferenceAssemblyPaths` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Opcjonalnie `String[]` parametr wyjściowy.<br /><br /> Zwraca ścieżkę na podstawie `TargetFrameworkMoniker` parametru. Jeśli `TargetFrameworkMoniker` ma wartość null lub pusty, ta ścieżka będzie `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Opcjonalnie `String[]` parametr wyjściowy.<br /><br /> Zwraca ścieżkę na podstawie `TargetFrameworkMoniker` parametru, bez uwzględniania częścią profilu moniker. Jeśli `TargetFrameworkMoniker` ma wartość null lub pusty, ta ścieżka będzie `String.Empty`.|  
|`TargetFrameworkMoniker`|Opcjonalnie `String` parametru.<br /><br /> Określa krótką nazwę platformy docelowej, który jest skojarzony z ścieżki zestawów odwołania.|  
|`RootPath`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżka katalogu głównego w celu wygenerowania ścieżki zestawów odwołania.|  
|`BypassFrameworkInstallChecks`|Opcjonalnie <xref:System.Boolean> parametru.<br /><br /> Jeśli `true`, pomija kontrole podstawowe, `GetReferenceAssemblyPaths` wykonuje domyślnie, aby upewnić się, że niektórych platform środowiska uruchomieniowego są zainstalowane, w zależności od platformy docelowej.|  
|`TargetFrameworkMonikerDisplayName`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa nazwę wyświetlaną dla krótką nazwę platformy docelowej.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)