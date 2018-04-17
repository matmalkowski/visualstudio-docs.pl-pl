---
title: Docelowych elementów MSBuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d9ab9a367352ddf7980394f8cb87823f7d163ed1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="msbuild-targets"></a>Obiekty docelowe w programie MSBuild
Obiekty docelowe grupowania zadań w określonej kolejności i pozwól, aby uwzględnić na mniejsze jednostki proces kompilacji. Na przykład jeden element docelowy może usunąć wszystkie pliki w katalogu danych wyjściowych, aby przygotować się do kompilacji, podczas gdy inny kompiluje dane wejściowe dla projektu i umieszcza je w pustych katalogów. Aby uzyskać więcej informacji na temat zadań, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
## <a name="declaring-targets-in-the-project-file"></a>Deklarowanie obiektów docelowych w pliku projektu  
 Obiekty docelowe są zadeklarowane w pliku projektu z [docelowej](../msbuild/target-element-msbuild.md) elementu. Na przykład następujący kod XML tworzy element docelowy o nazwie konstrukcji, który wywołuje CSC — zadanie o typie elementu kompilacji.  
  
```xml  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Podobnie jak właściwości programu MSBuild można ponownie zdefiniować obiekty docelowe. Na przykład  
  
```xml  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Wykonuje AfterBuild, zawiera tylko "drugie wystąpienie".  
  
## <a name="target-build-order"></a>Kolejność kompilowania obiektów docelowych  
 Obiekty docelowe muszą być uporządkowane, jeśli dane wejściowe jeden obiekt docelowy jest zależna od dane wyjściowe inny element docelowy. Istnieje kilka sposobów, aby określić kolejność, w których elementów docelowych uruchomienia.  
  
-   Początkowe obiekty docelowe  
  
-   Domyślne elementy docelowe  
  
-   Pierwszy element docelowy  
  
-   Zależności docelowych  
  
-   `BeforeTargets` i `AfterTargets` (MSBuild 4.0)  
  
 Element docelowy nigdy nie uruchamia się dwa razy podczas jednej kompilacji, nawet jeśli zależy od niego kolejnych docelowego w kompilacji. Po uruchomieniu elementu docelowego jej udziału kompilacja zostanie zakończona.  
  
 Aby uzyskać szczegóły i dodatkowe informacje o docelowej kolejność kompilowania, zobacz [kolejność kompilacji docelowej](../msbuild/target-build-order.md).  
  
## <a name="target-batching"></a>Przetwarzanie wsadowe obiektów docelowych  
 Element docelowy może mieć `Outputs` atrybut, który określa metadanych w formie % (metadanych). Jeśli tak, program MSBuild uruchamia docelowy raz dla każdej wartości metadanych unikatowy grupowania lub "przetwarzanie wsadowe" elementy, które mają tę wartość metadanych. Na przykład  
  
```xml  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 partie elementy odwołanie według ich RequiredTargetFramework metadanych. Dane wyjściowe obiektu docelowego wygląda następująco:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 Przetwarzanie wsadowe obiektów docelowych rzadko jest używany w rzeczywistych kompilacji. Przetwarzanie wsadowe zadań jest bardziej powszechne. Aby uzyskać więcej informacji, zobacz [wsadowe](../msbuild/msbuild-batching.md).  
  
## <a name="incremental-builds"></a>Kompilacje przyrostowe  
 Kompilacje przyrostowe są kompilacje, które są optymalizowane, dzięki czemu obiektów docelowych z pliki wyjściowe, które są aktualne względem odpowiadające im pliki wejściowe nie są wykonywane. Element docelowy może mieć zarówno `Inputs` i `Outputs` atrybuty, wskazującą, jakie elementy docelowy wejściową i jakie elementy go i tworzy jako dane wyjściowe.  
  
 Jeśli wszystkie elementy dane wyjściowe są aktualne, programu MSBuild pomija docelowej, co znacznie zwiększa szybkość kompilacji. Jest to wzrostowe elementu docelowego. Jeśli tylko niektóre pliki są aktualne, MSBuild wykonuje docelowego bez aktualne elementów. Jest to częściowy kompilacji przyrostowej obiektu docelowego. Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](../msbuild/incremental-builds.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Instrukcje: Użycie tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)