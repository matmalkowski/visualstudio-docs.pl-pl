---
title: Task — klasa podstawowa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0f11f797955dd2b909b75c0bc758209e1a0a028
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152158"
---
# <a name="task-base-class"></a>Klasa podstawowa zadania
Wiele zadań, ale ostatecznie dziedziczyć <xref:Microsoft.Build.Utilities.Task> klasy. Ta klasa dodaje kilka parametrów do zadań, które wynikają z nich. Te parametry są wymienione w niniejszym dokumencie.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry tej klasy bazowej.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Opcjonalnie <xref:Microsoft.Build.Framework.IBuildEngine> parametru.<br /><br /> Określa dostępne dla zadań interfejsu aparatu kompilacji. Aparat kompilacji automatycznie ustawia tego parametru, aby zezwolić na wywołania zwrotnego do niego zadań.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Opcjonalnie <xref:Microsoft.Build.Framework.IBuildEngine2> parametru.<br /><br /> Określa dostępne dla zadań interfejsu aparatu kompilacji. Aparat kompilacji automatycznie ustawia tego parametru, aby zezwolić na wywołania zwrotnego do niego zadań.<br /><br /> Jest to właściwość wygody, tak aby autorzy zadań dziedziczenie z tej klasy będą musieli rzutować wartości z `IBuildEngine` do `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Opcjonalnie <xref:Microsoft.Build.Framework.IBuildEngine3> parametru.<br /><br /> Określa interfejs aparat kompilacji, które są udostępniane przez hosta.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskHost> parametru.<br /><br /> Określa wystąpienie obiektu hosta (może być null). Aparat kompilacji ustawia tę właściwość, jeśli host IDE skojarzył obiekt hosta tego konkretnego zadania.|  
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Opcjonalnie <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametru tylko do odczytu.<br /><br /> Obiekt pomocnika rejestrowania...|  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)