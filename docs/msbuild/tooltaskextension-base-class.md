---
title: Tooltaskextension — klasa podstawowa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01d2abbed85b891378b0a9d5c4a41029bdc46cf3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="tooltaskextension-base-class"></a>ToolTaskExtension — Klasa podstawowa
Wielu zadań, które dziedziczą z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Ten łańcuch dziedziczenia dodaje kilka parametrów do zadań, które pochodzi z nich. Te parametry są wymienione w niniejszym dokumencie.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry klas podstawowych.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Opcjonalne <xref:Microsoft.Build.Framework.IBuildEngine> parametru.<br /><br /> Określa dostępne dla zadania interfejsu aparatu kompilacji. Ten parametr umożliwia zadań w celu wywołania zwrotnego do niego są automatycznie ustawiane w aparatu kompilacji.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Opcjonalne <xref:Microsoft.Build.Framework.IBuildEngine2> parametru.<br /><br /> Określa dostępne dla zadania interfejsu aparatu kompilacji. Ten parametr umożliwia zadań w celu wywołania zwrotnego do niego są automatycznie ustawiane w aparatu kompilacji.<br /><br /> Jest to właściwość wygody, aby autorzy zadań dziedziczenia z tej klasy nie należy rzutować wartości z `IBuildEngine` do `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Opcjonalne <xref:Microsoft.Build.Framework.IBuildEngine3> parametru.<br /><br /> Określa interfejs aparatu kompilacji dostarczony przez hosta.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A>|Opcjonalne `bool` parametru.<br /><br /> Jeśli wartość `true`, w tym zadań przekazuje **/q** do cmd.exe taki sposób, że w wierszu polecenia nie pobrać skopiowany do stdout wiersza polecenia.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>|Opcjonalne `String` parametr tablicy.<br /><br /> Tablica par zmiennych środowiskowych, oddzielonych znaku równości. Te zmienne są przekazanych do uruchomionego pliku wykonywalnego, oprócz lub selektywnie zastępowanie blok środowiska regularne.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A>|Opcjonalne `Int32` tylko do odczytu parametru wyjściowego.<br /><br /> Określa kod zakończenia zapewnianej przez wykonanego polecenia. Jeśli zadanie rejestrowane wszystkie błędy, ale proces ma kod zakończenia 0 (Powodzenie), to ma ustawioną wartość -1.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Opcjonalne <xref:Microsoft.Build.Framework.ITaskHost> parametru.<br /><br /> Określa wystąpienie obiektu hosta (może mieć wartości null). Aparat kompilacji ustawia tę właściwość, jeśli host IDE ma skojarzony obiekt hosta z tej konkretne zadanie.|  
|<xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A>|Opcjonalne <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametru tylko do odczytu.<br /><br /> Pobiera wystąpienie elementu <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> klasy zawierającej metody rejestrowania zadań.|  
|<xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A>|Opcja `bool` parametru.<br /><br /> Jeśli `true`, wszystkie komunikaty odebrane na Standardowy strumień błędów są rejestrowane jako błędy.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A>|Opcjonalne `String` parametru.<br /><br /> Znaczenie logowania tekst ze standardu limit strumienia.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A>|Opcjonalne `String` parametru.<br /><br /> Znaczenie logowania tekst ze standardu limit strumienia.|  
|<xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A>|Opcjonalne wirtualnej `Int32` parametru.<br /><br /> Określa ilość czasu, w milisekundach, po których plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue`, wskazując, że to nie okres limitu czasu. Jest limit czasu w milisekundach.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A>|Opcjonalne wirtualnej `string` parametru.<br /><br /> Projekty mogą wdrożyć do przesłonięcia Nazwa narzędzia. Zadania mogą zastąpić, aby zachować ToolName.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A>|Opcjonalne `string` parametru.<br /><br /> Określa lokalizację, z którym zadanie ładuje podstawowy plik wykonywalny. Jeśli ten parametr nie jest określony, zadanie użyje ścieżki instalacji zestawu SDK, umożliwiająca dla wersji platformy, który działa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|<xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A>|Opcjonalne `bool` parametru.<br /><br /> Jeśli wartość `true`, to zadanie tworzy plik wsadowy w wierszu polecenia i wykonuje go przy użyciu procesora poleceń zamiast bezpośrednio wykonywania polecenia.|  
|<xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A>|Opcjonalne `bool` parametru.<br /><br /> Jeśli wartość `true`, to zadanie daje węzła, gdy jego zadanie jest wykonywane.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)