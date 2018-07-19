---
title: Findinlist — zadanie | Dokumentacja firmy Microsoft
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
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 54562e26e0da5568ba74d40425cf377260d41000
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945123"
---
# <a name="findinlist-task"></a>FindInList — zadanie
Na określonej liście wyszukuje element, który ma pasujące itemspec.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry [findinlist — zadanie](../msbuild/findinlist-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`CaseSensitive`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, w wyszukiwaniu jest uwzględniana wielkość liter; w przeciwnym razie, nie jest. Wartość domyślna to `true`.|  
|`FindLastMatch`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zwracają ostatniego dopasowania; w przeciwnym razie zwraca pierwsze dopasowanie. Wartość domyślna to `false`.|  
|`ItemFound`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego tylko do odczytu.<br /><br /> Pierwsze dopasowanie znaleziono elementu na liście, jeśli istnieje.|  
|`ItemSpecToFind`|Wymagane `String` parametru.<br /><br /> Specyfikacja_elementu do wyszukania.|  
|`List`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista, w których należy szukać itemspec.|  
|`MatchFileNameOnly`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, dopasowywania tylko plik część nazwy specyfikacja_elementu; w przeciwnym razie dopasowywania całego itemspec. Wartość domyślna to `true`.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)