---
title: "Findinlist — zadanie | Dokumentacja firmy Microsoft"
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
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: c30b667564b3ffc4852f39c5ccc96c6527720a1f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="findinlist-task"></a>FindInList — Zadanie
Wymienionych na liście umożliwia znalezienie elementu, który ma specyfikacja_elementu dopasowania.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry [findinlist — zadanie](../msbuild/findinlist-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`CaseSensitive`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, wyszukiwanie jest rozróżniana wielkość liter; w przeciwnym razie, nie jest. Wartość domyślna to `true`.|  
|`FindLastMatch`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zwróć ostatni dopasowania; w przeciwnym razie zwraca pierwsze dopasowanie. Wartość domyślna to `false`.|  
|`ItemFound`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy tylko do odczytu.<br /><br /> Pierwszy dopasowywania znaleziono elementu na liście, jeśli istnieje.|  
|`ItemSpecToFind`|Wymagane `String` parametru.<br /><br /> Specyfikacja_elementu do wyszukania.|  
|`List`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista, w których będą poszukiwane specyfikacja_elementu.|  
|`MatchFileNameOnly`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, dopasować tylko część nazwy pliku z specyfikacja_elementu; w przeciwnym razie dopasowywania całego specyfikacja_elementu. Wartość domyślna to `true`.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)