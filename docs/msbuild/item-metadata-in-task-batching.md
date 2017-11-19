---
title: "Element metadanych w przetwarzaniu wsadowym zadań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: daa41beb487020dcaeccba692ace97b057a6b3ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="item-metadata-in-task-batching"></a>Metadane elementu w przetwarzaniu wsadowym zadań
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]ma możliwość dzielenia list elementów na różne kategorie lub partie, na podstawie metadanych elementu i uruchom zadanie z każdej z partii. Może być trudne do zrozumienia dokładnie elementy jest przekazywany z partii, które. W tym temacie omówiono następujące typowe scenariusze, które obejmują przetwarzanie wsadowe.  
  
-   Podział na partie listy elementów  
  
-   Podział kilka list elementów w partiach  
  
-   Przetwarzanie wsadowe jeden element w czasie  
  
-   Filtrowanie list elementów  
  
 Aby uzyskać więcej informacji na partie z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], zobacz [wsadowe](../msbuild/msbuild-batching.md).  
  
## <a name="dividing-an-item-list-into-batches"></a>Podział na partie listy elementów  
 Przetwarzanie wsadowe służy do dzielenia listy elementów na różnych partii na podstawie metadanych elementu, a następnie przekaż każdej partii osobno do zadania. Jest to przydatne w przypadku tworzenia zestawy satelickie.  
  
 Poniższy przykład pokazuje, jak do dzielenia listy elementów na partie na podstawie metadanych elementu. `ExampColl` Listy elementów jest podzielone na trzy partie na podstawie `Number` metadanych elementu. Obecność `%(ExampColl.Number)`w `Text` powiadamia atrybutu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] że powinny zostać wykonane przetwarzanie wsadowe. `ExampColl` Listy elementów jest podzielone na trzy partie na podstawie `Number` metadanych i każdej z partii jest oddzielnie przekazany do zadania.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [Zadanie wiadomości](../msbuild/message-task.md) zadanie zawiera następujące informacje:  
  
 `Number: 1 -- Items in ExampColl: Item1;Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2;Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3;Item6`  
  
## <a name="dividing-several-item-lists-into-batches"></a>Wyświetla dzielenia kilka elementów w partiach  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]można podzielić wiele list elementów w partiach oparte na tych samych metadanych. Ułatwia to dzielenia innego elementu list na partie, aby utworzyć wiele zestawów. Na przykład może mieć listy elementów plików .cs podzielone na partii aplikacji i partii zestawu i listy elementów podzielony na partii aplikacji i partii zestawu plików zasobów. Przetwarzanie wsadowe można następnie użyć do przekazania tych list elementów do jednego zadania i kompilacji zestawu i aplikacji.  
  
> [!NOTE]
>  Jeśli listy elementów przekazywany do zadania nie zawiera elementów z metadanymi, do którego istnieje odwołanie, każdy element tej listy elementów jest przekazywany do każdej partii.  
  
 Poniższy przykład pokazuje, jak do dzielenia wielu listy elementów na partie na podstawie metadanych elementu. `ExampColl` i `ExampColl2` list elementów każdego podzielone na trzy partie na podstawie `Number` metadanych elementu. Obecność `%(Number)`w `Text` powiadamia atrybutu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] że powinny zostać wykonane przetwarzanie wsadowe. `ExampColl` i `ExampColl2` list elementów są podzielone na trzy partie na podstawie `Number` metadanych i każdej z partii jest oddzielnie przekazany do zadania.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
  
        <ExampColl2 Include="Item4">  
            <Number>1</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item5">  
            <Number>2</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item6">  
            <Number>3</Number>  
        </ExampColl2>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>  
    </Target>  
  
</Project>  
```  
  
 [Zadanie wiadomości](../msbuild/message-task.md) zadanie zawiera następujące informacje:  
  
 `Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`  
  
## <a name="batching-one-item-at-a-time"></a>Przetwarzanie wsadowe jeden element w czasie  
 Przetwarzanie wsadowe można także wykonać na metadane dobrze znanego elementu, który jest przypisany do każdego elementu po jego utworzeniu. Gwarantuje to, że każdy element w kolekcji będzie miało niektórych metadanych do użycia na potrzeby przetwarzania wsadowego. `Identity` Wartość metadanych jest unikatowy dla każdego elementu i jest przydatne w przypadku dzielenia każdej pozycji listy elementów do oddzielnych partii. Aby uzyskać pełną listę metadane dobrze znanego elementu, zobacz [metadane dobrze znanego elementu](../msbuild/msbuild-well-known-item-metadata.md).  
  
 Poniższy przykład pokazuje, jak dzielić na partie każdego elementu w jednym listy elementów naraz. Ponieważ `Identity` wartość metadanych każdy element jest unikatowa, `ExampColl` listy elementów jest podzielona na partie sześciu każdej partii zawierające jeden element z listy elementów. Obecność `%(Identity)`w `Text` powiadamia atrybutu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] że powinny zostać wykonane przetwarzanie wsadowe.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1"/>  
        <ExampColl Include="Item2"/>  
        <ExampColl Include="Item3"/>  
        <ExampColl Include="Item4"/>  
        <ExampColl Include="Item5"/>  
        <ExampColl Include="Item6"/>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Identity: "%(Identity)" -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [Zadanie wiadomości](../msbuild/message-task.md) zadanie zawiera następujące informacje:  
  
```  
Identity: "Item1" -- Items in ExampColl: Item1  
Identity: "Item2" -- Items in ExampColl: Item2  
Identity: "Item3" -- Items in ExampColl: Item3  
Identity: "Item4" -- Items in ExampColl: Item4  
Identity: "Item5" -- Items in ExampColl: Item5  
Identity: "Item6" -- Items in ExampColl: Item6  
```  
  
## <a name="filtering-item-lists"></a>Wyświetla listę elementów filtrowania  
 Przetwarzanie wsadowe może służyć do filtrowania niektórych elementów z listy elementów przed przekazaniem go do zadania. Na przykład filtrowanie `Extension` wartość metadane dobrze znanego elementu umożliwia uruchamianie zadania na tylko pliki z określonym rozszerzeniem.  
  
 Poniższy przykład pokazuje, jak do dzielenia listy elementów na partie na podstawie metadanych elementu, a następnie przeprowadź filtrowanie te partie, gdy są one przekazywane do zadania. `ExampColl` Listy elementów jest podzielone na trzy partie na podstawie `Number` metadanych elementu. `Condition` Atrybut zadania określa, że tylko partii z `Number` wartość metadanych z elementu `2` zostaną przekazane do zadania  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
  
    </ItemGroup>  
  
    <Target Name="Exec">  
        <Message  
            Text = "Items in ExampColl: @(ExampColl)"  
            Condition="'%(Number)'=='2'"/>  
    </Target>  
  
</Project>  
```  
  
 [Zadanie wiadomości](../msbuild/message-task.md) zadanie zawiera następujące informacje:  
  
```  
Items in ExampColl: Item2;Item5  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Metadane dobrze znanego elementu](../msbuild/msbuild-well-known-item-metadata.md)   
 [Item — Element (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Itemmetadata — Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)