---
title: Element metadanych w przetwarzaniu wsadowym obiektów docelowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 486169788ad4533f5d45bf48c979ce3d0f5f7920
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081062"
---
# <a name="item-metadata-in-target-batching"></a>Metadane elementu w przetwarzaniu wsadowym obiektów docelowych
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zdolność przeprowadzania analizy zależności wejść i wyjść docelowej kompilacji. Jeśli okaże się, że dane wejściowe lub wyjściowe, obiektu docelowego są aktualne, element docelowy zostanie pominięta, a kompilacja będzie kontynuowana. `Target` Użyj elementów `Inputs` i `Outputs` atrybutów, aby określić elementy, aby sprawdzić podczas analizy zależności.  
  
 Jeśli obiekt docelowy zawiera zadania, które używa elementy w partii jako danych wejściowych lub wyjściowych, `Target` elementu docelowego należy używać, przetwarzanie wsadowe w jego `Inputs` lub `Outputs` atrybutów, aby umożliwić [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do pominięcia instancji elementów, które są już aktualne.  
  
## <a name="batch-targets"></a>Cele usługi Batch  
 Poniższy przykład zawiera listę elementów o nazwie `Res` który jest podzielony na dwie partie na podstawie `Culture` metadanych elementu. Każda z tych partii jest przekazywana do `AL` zadania, które tworzy zestaw danych wyjściowych dla każdej partii. Za pomocą adapterów przetwarzania wsadowego na `Outputs` atrybutu `Target` elementu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] można określić, czy jest każdej partii poszczególnych aktualne przed uruchomieniem element docelowy. Bez użycia przetwarzaniu wsadowym obiektów docelowych, zarówno partie elementów zostałoby uruchomione przez zadanie podrzędne, za każdym razem, gdy element docelowy został wykonany.  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Porady: kompilacja przyrostowa](../msbuild/how-to-build-incrementally.md)   
 [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)   
 [TARGET — element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Metadane elementu w przetwarzaniu wsadowym zadań](../msbuild/item-metadata-in-task-batching.md)