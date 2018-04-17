---
title: Taskextension — klasa podstawowa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13835d82fa331f25060eaa96d9317eeb1226efea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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