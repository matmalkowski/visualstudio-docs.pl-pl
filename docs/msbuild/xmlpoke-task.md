---
title: "Xmlpoke — zadanie | Dokumentacja firmy Microsoft"
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
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 01b44f9adf82224b1eae09a452798284bbcc1935
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xmlpoke-task"></a>XmlPoke — Zadanie
Ustawia wartości określonych przez zapytanie XPath do pliku XML.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `XmlPoke` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Namespaces`|Opcjonalne `String` parametru.<br /><br /> Określa przestrzeni nazw dla prefiksów kwerendy XPath.|  
|`Query`|Opcjonalne `String` parametru.<br /><br /> Określa zapytanie XPath.|  
|`Value`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa plik wyjściowy.|  
|`XmlInputPath`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa dane wejściowe XML jako ścieżkę pliku.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)