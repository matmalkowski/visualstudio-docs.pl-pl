---
title: Zadania programu MSBuild | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: "18"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: fc2afbe7b0226cb5983aa3022ff4b24ac31fe7aa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-tasks"></a>Zadania programu MSBuild
Platformy kompilacji musi mieć możliwość wykonania dowolną liczbę akcji podczas procesu kompilacji. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]używa *zadania* do wykonania tych czynności. Zadanie jest jednostką kodu wykonywalnego, używana przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do wykonywania operacji niepodzielnych kompilacji.  
  
## <a name="task-logic"></a>Logika zadań  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Format pliku XML projektu pełni nie można wykonać operacji na własną, tak logiki zadań muszą zostać zaimplementowane poza pliku projektu kompilacji.  
  
 Logiki wykonywania zadania jest zaimplementowany jako klasy .NET, który implementuje <xref:Microsoft.Build.Framework.ITask> interfejs, który jest zdefiniowany w <xref:Microsoft.Build.Framework> przestrzeni nazw.  
  
 Klasa zadanie również definiuje parametry wejściowe i wyjściowe, które muszą być dostępne do zadań w pliku projektu. Wszystkie publiczne można ustawić niestatyczna nieabstrakcyjnej właściwości udostępnianych przez klasy zadania będą dostępne w pliku projektu umieszczając odpowiedniego atrybutu o takiej samej nazwie w [zadań](../msbuild/task-element-msbuild.md) elementu.  
  
 Można pisać własne zadania przy tworzenia zarządzanej klasy, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejsu. Aby uzyskać więcej informacji, zobacz [wpisywanie zadania](../msbuild/task-writing.md).  
  
## <a name="executing-a-task-from-a-project-file"></a>Wykonywanie zadania z pliku projektu  
 Przed wykonaniem zadania w pliku projektu, trzeba najpierw zmapować typu w zestawie, który implementuje zadania, nazwa zadania z [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu. Dzięki temu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wiedzieć, gdzie ma zostać wyszukane logiki wykonywania zadania, gdy znajdzie w pliku projektu.  
  
 Do wykonania zadania w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu, Utwórz element o nazwie zadania jako element podrzędny `Target` elementu. Jeśli zadanie akceptuje parametry, te są przekazywane jako atrybuty elementu.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]element listy i właściwości mogą być używane jako parametry. Na przykład poniższy kod wywołania `MakeDir` zadań i ustawia wartość `Directories` właściwość `MakeDir` wartości z obiektu `BuildDir` właściwości zadeklarowany w poprzednim przykładzie.  
  
```xml  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Zadania można także wrócić informacji do pliku projektu, które mogą być przechowywane w elementach lub właściwości do późniejszego użycia. Na przykład poniższy kod wywołania `Copy` zadań oraz przechowuje te informacje z `CopiedFiles` output właściwości w `SuccessfullyCopiedFiles` listy elementów.  
  
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
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]dostarczany z wielu zadań, takich jak [kopiowania](../msbuild/copy-task.md), który kopiuje pliki, [makedir —](../msbuild/makedir-task.md), co powoduje katalogów, i [Csc](../msbuild/csc-task.md), który kompiluje [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plików kodu źródłowego. Aby uzyskać pełną listę dostępnych zadań i informacje o użyciu zobacz [odwołanie do zadania](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Zastąpione zadania  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]Wyszukuje zadań w kilku lokalizacjach. Pierwszy znajduje się w plikach z rozszerzeniem. OverrideTasks przechowywanych w katalogach platformy .NET Framework. Zadania w tych plikach zastąpienie innych zadań pod tą samą nazwą, łącznie z zadaniami w pliku projektu. Drugi znajduje się w plikach z rozszerzeniem. Zadania w katalogach platformy .NET. Jeśli zadanie nie zostanie znaleziony w jednej z tych lokalizacji, używane jest zadanie w pliku projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md)   
 [Wpisywanie zadania](../msbuild/task-writing.md)   
 [Zadania wbudowane](../msbuild/msbuild-inline-tasks.md)