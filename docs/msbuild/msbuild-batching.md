---
title: Przetwarzanie wsadowe MSBuild | Dokumentacja firmy Microsoft
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
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: "9"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 68977ca672aae84cd65ca169c4ca13feda6d7887
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-batching"></a>Przetwarzanie wsadowe w programie MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]ma możliwość dzielenia list elementów na różne kategorie lub partie, na podstawie metadanych elementu i uruchom docelowej lub zadania z każdej z partii.  
  
## <a name="task-batching"></a>Przetwarzanie wsadowe zadań  
 Przetwarzanie wsadowe zadań umożliwia uproszczenie plików projektu, zapewniając sposobu dzielenia list elementów na różnych partii, a następnie przekaż każdego z tych partie osobno do zadania. Oznacza to, że plik projektu tylko musi mieć zadania i jego atrybuty zadeklarowany raz, mimo że można go uruchamiać kilka razy.  
  
 Możesz określić, że [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do wykonania, przetwarzanie wsadowe z zadaniem przy użyciu %(*ItemMetaDataName*) Notacja w jeden z atrybutów zadania. Poniższy przykład dzieli `Example` na podstawie listy elementów w partiach `Color` wartość metadane elementu i przekazuje partii do `MyTask` zadań oddzielnie.  
  
> [!NOTE]
>  Jeśli użytkownik nie odwołuj się do listy elementów w innym miejscu w atrybutach zadań lub nazwa metadanych może być niejednoznaczna, możesz użyć %(*ItemCollection.ItemMetaDataName*) notacji do pełnej kwalifikacji wartość elementu metadanych do użycia na potrzeby przetwarzania wsadowego.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Aby uzyskać bardziej szczegółowe przykłady przetwarzanie wsadowe, zobacz [metadane elementu w przetwarzaniu wsadowym zadań](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Przetwarzanie wsadowe obiektów docelowych  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]sprawdza, jeśli wejściami i wyjściami obiektu docelowego są aktualne przed uruchomieniem obiektu docelowego. Jeśli zarówno wejściami i wyjściami są aktualne, element docelowy zostanie pominięty. Jeśli zadanie wewnątrz elementu docelowego korzysta z przetwarzania wsadowego [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] musi określić, czy wejścia i wyjścia dla każdej partii elementów jest aktualny. W przeciwnym razie element docelowy jest wykonywana za każdym razem, gdy jest kliknij przycisk.  
  
 W poniższym przykładzie przedstawiono `Target` element, który zawiera `Outputs` atrybutem %(*ItemMetaDataName*) notacji. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]Dzieli `Example` na podstawie listy elementów w partiach `Color` element metadanych i analizować sygnatury czasowe plików wyjściowych dla każdej partii. Jeśli dane wyjściowe z partii nie są aktualne, element docelowy jest uruchamiany. W przeciwnym razie element docelowy został pominięty.  
  
```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Aby uzyskać inny przykład przetwarzaniu wsadowym obiektów docelowych, zobacz [metadane elementu w przetwarzaniu wsadowym obiektów docelowych](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Funkcje właściwości przy użyciu metadanych  
 Przetwarzanie wsadowe mogą być kontrolowane przez funkcje właściwości, które obejmują metadanych. Na przykład  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 używa <xref:System.IO.Path.Combine%2A> połączyć ścieżkę folderu głównego ze ścieżką elementu kompilacji.  
  
 Funkcje właściwości nie może występować w wartości metadanych.  Na przykład  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 nie jest dozwolone.  
  
 Aby uzyskać więcej informacji na temat właściwości funkcji, zobacz [funkcje właściwości](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Itemmetadata — Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)