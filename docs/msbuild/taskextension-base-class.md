---
title: "Taskextension — klasa podstawowa | Dokumentacja firmy Microsoft"
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
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 058ed6f4b95a395e71d1b98ce2de69257c742e23
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="taskextension-base-class"></a>TaskExtension — Klasa podstawowa
Wiele zadań dziedziczyć <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Ten łańcuch dziedziczenia dodaje kilka parametrów do zadań, które pochodzi z nich. Te parametry są wymienione w niniejszym dokumencie.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry klas podstawowych.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Opcjonalne <xref:Microsoft.Build.Framework.IBuildEngine> parametru.<br /><br /> Określa dostępne dla zadania interfejsu aparatu kompilacji. Ten parametr umożliwia zadań w celu wywołania zwrotnego do niego są automatycznie ustawiane w aparatu kompilacji.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Opcjonalne <xref:Microsoft.Build.Framework.IBuildEngine2> parametru.<br /><br /> Określa dostępne dla zadania interfejsu aparatu kompilacji. Ten parametr umożliwia zadań w celu wywołania zwrotnego do niego są automatycznie ustawiane w aparatu kompilacji.<br /><br /> Jest to właściwość wygody, aby autorzy zadań dziedziczenia z tej klasy nie należy rzutować wartości z `IBuildEngine` do `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Opcjonalne <xref:Microsoft.Build.Framework.IBuildEngine3> parametru.<br /><br /> Określa interfejs aparatu kompilacji dostarczony przez hosta.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Opcjonalne <xref:Microsoft.Build.Framework.ITaskHost> parametru.<br /><br /> Określa wystąpienie obiektu hosta (może mieć wartości null). Aparat kompilacji ustawia tę właściwość, jeśli host IDE ma skojarzony obiekt hosta z tej konkretne zadanie.|  
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Opcjonalne <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametru tylko do odczytu.<br /><br /> Pobiera `TaskLoggingHelperExtension` obiekt, który zawiera metody rejestrowania zadań.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)