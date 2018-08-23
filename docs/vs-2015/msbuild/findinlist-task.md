---
title: Findinlist — zadanie | Dokumentacja firmy Microsoft
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
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a66ae638363586d456b21d62d894e68d8969264
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690113"
---
# <a name="findinlist-task"></a>FindInList — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [findinlist — zadanie](https://docs.microsoft.com/visualstudio/msbuild/findinlist-task).  
  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)



