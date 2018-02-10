---
title: "Element metadanych w przetwarzaniu wsadowym obiektów docelowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c15870bb47d1f53f1943882ed0685c222e82b326
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="item-metadata-in-target-batching"></a>Metadane elementu w przetwarzaniu wsadowym obiektów docelowych
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ma możliwość wykonywania analizy zależności w danych wejściowych i wyjściowych elementu docelowego kompilacji. Jeśli okaże się, że wejściowych i wyjściowych elementu docelowego są aktualne, element docelowy zostanie pominięta i kompilacji będzie kontynuować. `Target`Użyj elementów `Inputs` i `Outputs` atrybutów, aby określić elementy, aby sprawdzić podczas analizy zależności.  
  
 Jeśli element docelowy zawiera zadania, które wykorzystuje wsadów elementów jako danych wejściowych lub wyjściowych, `Target` elementu docelowego należy użyć, przetwarzanie wsadowe w jego `Inputs` lub `Outputs` atrybutów w celu włączenia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pomijania partie elementy, które są już aktualne.  
  
## <a name="batching-targets"></a>Przetwarzanie wsadowe obiektów docelowych  
 Poniższy przykład zawiera listy elementów o nazwie `Res` które jest podzielony na dwie partie na podstawie `Culture` metadanych elementu. Każdy z tych instancji są przekazywane do `AL` zadania, które tworzy zestawu wyjściowego dla każdej partii. Za pomocą przetwarzanie wsadowe `Outputs` atrybutu `Target` elementu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] można określić, czy jest każdej poszczególnych partii aktualne przed uruchomieniem obiektu docelowego. Bez użycia w przetwarzaniu wsadowym obiektów docelowych, zarówno partie elementów może działać przez zadanie każdorazowego wykonano obiektu docelowego.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: kompilacja przyrostowa](../msbuild/how-to-build-incrementally.md)   
 [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)   
 [TARGET — Element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Metadane elementu w przetwarzaniu wsadowym zadań](../msbuild/item-metadata-in-task-batching.md)