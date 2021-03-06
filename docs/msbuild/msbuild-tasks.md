---
title: Zadania programu MSBuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a380917f3a4eaba71a00ff32f1bc627f47f5d4d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153205"
---
# <a name="msbuild-tasks"></a>zadania programu MSBuild
Platforma kompilacji musi mieć możliwość wykonywania dowolną liczbę akcji podczas procesu kompilacji. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] używa *zadania* wykonywać te akcje. Zadanie jest jednostką kodu wykonywalnego, używana przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do wykonywania niepodzielnych operacji kompilacji.  
  
## <a name="task-logic"></a>Logika zadania  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Formatu pliku projektu XML pełni nie można wykonać operacji na własną, logiki zadań muszą zostać wykonane poza plik projektu kompilacji.  
  
 Logika wykonania zadania jest implementowany jako klasa .NET, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejs, który jest zdefiniowany w <xref:Microsoft.Build.Framework> przestrzeni nazw.  
  
 Task — klasa definiuje również parametry wejściowe i wyjściowe, które muszą być dostępne do zadania w pliku projektu. Wszystkie publiczne można ustawić niestatycznych nieabstrakcyjnej właściwości udostępnianych przez klasy zadania można uzyskiwać w pliku projektu, umieszczając odpowiedni atrybut o tej samej nazwie na [zadań](../msbuild/task-element-msbuild.md) elementu.  
  
 Można napisać własne zadanie, tworząc klasy zarządzanej, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejsu. Aby uzyskać więcej informacji, zobacz [zadań zapisywanie](../msbuild/task-writing.md).  
  
## <a name="execute-a-task-from-a-project-file"></a>Uruchom zadanie w pliku projektu  
 Przed wykonaniem zadania w pliku projektu, przed pierwszym mapowaniem typu w zestawie, który implementuje zadania, nazwę zadania za pomocą [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu. Dzięki temu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wiedzieć, gdzie szukać logika wykonania zadania, gdy znajdzie w pliku projektu.  
  
 Aby wykonać zadania w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu, Utwórz element o nazwę zadania jako element podrzędny elementu `Target` elementu. Jeśli zadanie akceptuje parametry, te są przekazywane jako atrybuty elementu.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] listy i właściwości można go używać jako parametrów. Na przykład, poniższy kod wywoła `MakeDir` zadań i ustawia wartość `Directories` właściwość `MakeDir` równa wartości obiektu `BuildDir` właściwości zadeklarowanych w poprzednim przykładzie.  
  
```xml  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Zadania może również zwracać informacje do pliku projektu, które mogą być przechowywane w elementach lub właściwości w celu późniejszego użycia. Na przykład, poniższy kod wywoła `Copy` zadań i przechowują informacje od `CopiedFiles` danych wyjściowych właściwość `SuccessfullyCopiedFiles` listy elementów.  
  
```xml  
<Target Name="CopyFiles">  
    <Copy  
        SourceFiles="@(MySourceFiles)"  
        DestinationFolder="@(MyDestFolder)">  
        <Output  
            TaskParameter="CopiedFiles"  
            ItemName="SuccessfullyCopiedFiles"/>  
     </Copy>  
</Target>  
```  
  
## <a name="included-tasks"></a>Dołączone zadania  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jest dostarczany z wielu zadań, takich jak [kopiowania](../msbuild/copy-task.md), który kopiuje pliki, [MakeDir](../msbuild/makedir-task.md), który tworzy katalogi, i [Csc](../msbuild/csc-task.md), który kompiluje [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pliki kodów źródłowych. Aby uzyskać pełną listę dostępnych zadań i informacje o użyciu, zobacz [zadania, odwołanie](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Zastąpione zadania  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Wyszukuje zadania w kilku lokalizacjach. Pierwszy znajduje się w plikach z rozszerzeniem *. OverrideTasks* przechowywanych w katalogach platformy .NET Framework. Zadania w tych plikach zastąpienie innych zadań, za pomocą tych samych nazw, w tym zadania w pliku projektu. Druga lokalizacja znajduje się w plikach z rozszerzeniem *. Zadania* w katalogach platformy .NET Framework. Jeśli zadanie nie zostanie znaleziony w jednej z tych lokalizacji, zadania w pliku projektu jest używany.  
  
## <a name="see-also"></a>Zobacz także  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Program MSBuild](../msbuild/msbuild.md)   
 [Wpisywanie zadania](../msbuild/task-writing.md)   
 [Zadania wbudowane](../msbuild/msbuild-inline-tasks.md)