---
title: Xmlpeek — zadanie | Dokumentacja firmy Microsoft
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
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa10b53137135af32a350dad7acffd48f8b3074c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31570746"
---
# <a name="xmlpeek-task"></a>XmlPeek — Zadanie
Zwraca wartości określonych przez zapytanie XPath z pliku XML.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `XmlPeek` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Namespaces`|Opcjonalne `String` parametru.<br /><br /> Określa przestrzeni nazw dla prefiksów kwerendy XPath.|  
|`Query`|Opcjonalne `String` parametru.<br /><br /> Określa zapytanie XPath.|  
|`Result`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera wyniki, które są zwracane przez to zadanie.|  
|`XmlContent`|Opcjonalne `String` parametru.<br /><br /> Określa dane wejściowe XML jako ciąg.|  
|`XmlInputPath`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa dane wejściowe XML jako ścieżkę pliku.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)