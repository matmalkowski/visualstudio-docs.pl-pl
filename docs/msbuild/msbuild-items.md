---
title: Elementy programu MSBuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6df8e21ad47ba2c307ba2d3c531a28ff8a2bdb0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="msbuild-items"></a>Elementy programu MSBuild
Elementy programu MSBuild są dane wejściowe w systemie kompilacji i zwykle odpowiadają pliki. Elementy są pogrupowane w typy elementów na podstawie ich nazw elementu. Typy elementów są nazywane listę elementów, które mogą być używane jako parametry dla zadania. Zadań użyj wartości elementu, aby wykonać kroki procesu kompilacji.  
  
 Ponieważ elementy są reprezentowane przez typ elementu, do których one należą, warunki "item" i "wartość elementu" można zamiennie.  
  
 **W tym temacie**  
  
-   [Tworzenie elementów w pliku projektu](#BKMK_Creating1)  
  
-   [Tworzenie elementów podczas wykonywania](#BKMK_Creating2)  
  
-   [Odwołania do elementów w pliku projektu](#BKMK_ReferencingItems)  
  
-   [Przy użyciu symboli wieloznacznych, aby określić elementy](#BKMK_Wildcards)  
  
-   [Za pomocą atrybutu wykluczania](#BKMK_ExcludeAttribute)  
  
-   [Metadane elementu](#BKMK_ItemMetadata)  
  
    -   [Odwołanie do metadanych elementu w pliku projektu](#BKMK_ReferencingItemMetadata)  
  
    -   [Metadane dobrze znanego elementu](#BKMK_WellKnownItemMetadata)  
  
    -   [Przekształcanie przy użyciu metadanych typów elementów](#BKMK_Transforming)  
  
-   [Definicje elementów](#BKMK_ItemDefinitions)  
  
-   [Atrybuty dla elementów w ItemGroup obiektu docelowego](#BKMK_AttributesWithinTargets)  
  
    -   [Usuń atrybut](#BKMK_RemoveAttribute)  
  
    -   [KeepMetadata Attribute](#BKMK_KeepMetadata)  
  
    -   [RemoveMetadata Attribute](#BKMK_RemoveMetadata)  
  
    -   [Atrybut KeepDuplicates](#BKMK_KeepDuplicates)  
  
##  <a name="BKMK_Creating1"></a> Tworzenie elementów w pliku projektu  
 Można zadeklarować elementów w pliku projektu jako podrzędne elementy [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Nazwa elementu podrzędnego jest typ elementu. `Include` Atrybut elementu określa elementy (pliki) mają zostać dołączone do tego typu elementu. Na przykład następujący kod XML tworzy typ elementu o nazwie `Compile`, która obejmuje dwa pliki.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Element "file2.cs" nie zastępuje element "file1.cs"; Zamiast tego, nazwa pliku jest dołączany do listy wartości dla `Compile` typ elementu. Nie można usunąć elementu z typu elementu kompilacji w fazie oceny.  
  
 Następujący kod XML tworzy ten sam typ elementu przez zadeklarowanie oba pliki w jednym `Include` atrybutu. Zwróć uwagę, że nazwy plików są oddzielone średnikami.  
  
```xml  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="BKMK_Creating2"></a> Tworzenie elementów podczas wykonywania  
 Elementy, które są poza [docelowej](../msbuild/target-element-msbuild.md) elementy mają przypisane wartości kompilacji w fazie oceny. Podczas fazy wykonywania kolejnych elementów można utworzyć lub zmodyfikować w następujący sposób:  
  
-   Wszystkie zadania można wyemitować elementu. Można wyemitować elementu [zadań](../msbuild/task-element-msbuild.md) element musi mieć element podrzędny [dane wyjściowe](../msbuild/output-element-msbuild.md) element, który ma `ItemName` atrybutu.  
  
-   [Createitem —](../msbuild/createitem-task.md) zadań można wyemitować elementu. Takie użycie jest przestarzałe.  
  
-   W programie .NET Framework 3.5, `Target` elementy mogą zawierać [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementy, które mogą zawierać elementu elementów.  
  
##  <a name="BKMK_ReferencingItems"></a> Odwołania do elementów w pliku projektu  
 Aby odwołać typów elementów w pliku projektu, należy użyć składni @(`ItemType`). Na przykład, czy odwołania typu elementu w poprzednim przykładzie przy użyciu `@(Compile)`. Przy użyciu tej składni, można przekazać elementów do zadania przez określenie typu elementu jako parametr tego zadania. Aby uzyskać więcej informacji, zobacz [porady: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md).  
  
 Domyślnie elementy typu elementu są rozdzielone średnikami (;), po jego rozwinięciu. Można użyć składni @(*ItemType*, "*separatora*") można określić separatora innej niż domyślna. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie listy elementów rozdzielanych przecinkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="BKMK_Wildcards"></a> Przy użyciu symboli wieloznacznych, aby określić elementy  
 Można użyć **, \*, a? symboli wieloznacznych, aby określić grupy plików jako dane wejściowe dla kompilacji zamiast wyświetlania każdego pliku osobno.  
  
-   ? znaki wieloznaczne zastępuje pojedynczy znak.  
  
-   * Wieloznacznego dopasowuje zero lub więcej znaków.  
  
-   ** Sekwencja znaków wieloznacznych ścieżka częściowa jest zgodna.  
  
 Na przykład można określić wszystkie pliki .cs w katalogu, który zawiera plik projektu przy użyciu następującego elementu w pliku projektu.  
  
```xml  
<CSFile Include="*.cs"/>  
```  
  
 Następujący element wybiera wszystkie pliki .vb na dysku D::  
  
```xml  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [porady: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="BKMK_ExcludeAttribute"></a> Za pomocą atrybutu wykluczania  
 Element może zawierać `Exclude` atrybut, który wyklucza określone elementy (pliki) z typu elementu. `Exclude` Atrybut jest zwykle używana wraz z symboli wieloznacznych. Na przykład następujący kod XML dodaje każdego pliku .cs w katalogu do typu elementu CSFile, z wyjątkiem `DoNotBuild.cs` pliku.  
  
```xml  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 `Exclude` Atrybut ma wpływ tylko elementy, które są dodawane przez `Include` atrybutu elementu, który je zawiera. Poniższy przykład nie Wyklucz plik pliku Form1.cs, która została dodana w elemencie poprzedniego elementu.  
  
```xml  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Aby uzyskać więcej informacji, zobacz [porady: wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="BKMK_ItemMetadata"></a> Metadane elementu  
 Elementy mogą zawierać metadane oprócz informacji w `Include` i `Exclude` atrybutów. Te metadane mogą posłużyć zadania, które wymagają więcej informacji o zapasach lub zadania wsadowego i obiektów docelowych. Aby uzyskać więcej informacji, zobacz [wsadowe](../msbuild/msbuild-batching.md).  
  
 Metadane są kolekcję par klucz wartość, które są zadeklarowane w pliku projektu jako elementy podrzędne elementu. Nazwa elementu podrzędnego jest nazwą metadanych i wartości elementu podrzędnego jest wartość metadanych.  
  
 Metadane są skojarzone z elementu, który go zawiera. Na przykład następujący kod XML dodaje `Culture` metadanych, który ma wartość `Fr` zarówno "one.cs" i "two.cs" elementy CSFile typ elementu.  
  
```xml  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Element może mieć zero lub więcej wartości metadanych. W dowolnym momencie można zmienić wartości metadanych. Jeśli metadane ustawiono pustą wartość, można efektywnie go usunąć z kompilacji.  
  
###  <a name="BKMK_ReferencingItemMetadata"></a> Odwołanie do metadanych elementu w pliku projektu  
 Metadane elementu w pliku projektu można odwoływać się przy użyciu składni %(`ItemMetadataName`). Istnieje niejednoznaczność, może kwalifikować się odwołanie za pomocą nazwy typu elementu. For example, możesz określić %(*ItemType.ItemMetaDataName*). W poniższym przykładzie użyto Wyświetla metadane do przetwarzania wsadowego zadania wiadomości. Aby uzyskać więcej informacji o sposobie używania metadanych elementu dla przetwarzania wsadowego, zobacz [metadane elementu w przetwarzaniu wsadowym zadań](../msbuild/item-metadata-in-task-batching.md).  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="BKMK_WellKnownItemMetadata"></a> Metadane dobrze znanego elementu  
 Gdy element zostanie dodany do typu elementu, ten element jest przypisany niektóre metadane dobrze znanego. Na przykład wszystkie elementy mają dobrze znanego metadanych `%(Filename)`, którego wartość jest nazwą pliku elementu. Aby uzyskać więcej informacji, zobacz [metadane dobrze znanego elementu](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="BKMK_Transforming"></a> Przekształcanie przy użyciu metadanych typów elementów  
 Przy użyciu metadanych, można przekształcić list elementów do nowego elementu listy. Na przykład można przekształcać typ elementu `CppFiles` zawierającej elementy, które reprezentują .cpp pliki na odpowiedniej liście plików .obj przy użyciu wyrażenia `@(CppFiles -> '%(Filename).obj')`.  
  
 Poniższy kod tworzy `CultureResource` typ, który zawiera wszystkie kopie elementu `EmbeddedResource` elementy `Culture` metadanych. `Culture` Wartości metadanych staje się wartością z nowymi metadanymi `CultureResource.TargetDirectory`.  
  
```xml  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Aby uzyskać więcej informacji, zobacz [przekształca](../msbuild/msbuild-transforms.md).  
  
##  <a name="BKMK_ItemDefinitions"></a> Definicje elementów  
 Począwszy od programu .NET Framework 3.5, można dodać domyślnego metadanych do dowolnego typu elementu za pomocą [ItemDefinitionGroup — element](../msbuild/itemdefinitiongroup-element-msbuild.md). Jak metadanych dobrze znanego metadanych domyślny jest skojarzony z wszystkich elementów tego typu elementu, który określisz. Można jawnie przesłonić domyślny metadanych w definicji elementu. Na przykład następujący kod XML daje `Compile` elementów "one.cs" i "three.cs" metadanych `BuildDay` o wartości "Poniedziałek". Kod zawiera element "two.cs" metadanych `BuildDay` o wartości "Wtorek".  
  
```xml  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 Aby uzyskać więcej informacji, zobacz [definicje elementów](../msbuild/item-definitions.md).  
  
##  <a name="BKMK_AttributesWithinTargets"></a> Atrybuty dla elementów w ItemGroup obiektu docelowego  
 W programie .NET Framework 3.5, `Target` elementy mogą zawierać [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementy, które mogą zawierać elementu elementów. Atrybuty w tej sekcji są prawidłowe w przypadku, gdy są one określone dla elementu `ItemGroup` w `Target`.  
  
###  <a name="BKMK_RemoveAttribute"></a> Usuń atrybut  
 Elementy w `ItemGroup` obiektu docelowego, może zawierać `Remove` atrybut, który usuwa określone elementy (pliki) z typu elementu. Ten atrybut został wprowadzony w .NET Framework 3.5.  
  
 Poniższy przykład umożliwia usunięcie każdego pliku .config z typu elementu kompilacji.  
  
```xml  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="BKMK_KeepMetadata"></a> Atrybut KeepMetadata  
 Jeśli element zostanie wygenerowany wewnątrz elementu docelowego, może zawierać elementu `KeepMetadata` atrybutu. Jeśli ten atrybut jest określony, metadane, określonego w Rozdzielana średnikami lista nazw zostanie przeniesiona z elementu źródłowego do elementu docelowego. Pusta wartość dla tego atrybutu jest odpowiednikiem nieokreślenie go. `KeepMetadata` Atrybut została wprowadzona w programie .NET Framework 4.5.  
  
 Poniższy przykład przedstawia sposób użycia `KeepMetadata` atrybutu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="BKMK_RemoveMetadata"></a> Atrybut RemoveMetadata  
 Jeśli element zostanie wygenerowany wewnątrz elementu docelowego, może zawierać elementu `RemoveMetadata` atrybutu. Jeśli ten atrybut jest określony, wszystkie metadane jest przenoszona z elementu źródłowego do docelowego elementu z wyjątkiem metadanych których nazwy są zawarte w Rozdzielana średnikami lista nazw. Pusta wartość dla tego atrybutu jest odpowiednikiem nieokreślenie go. `RemoveMetadata` Atrybut została wprowadzona w programie .NET Framework 4.5.  
  
 Poniższy przykład przedstawia sposób użycia `RemoveMetadata` atrybutu.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="BKMK_KeepDuplicates"></a> Atrybut KeepDuplicates  
 Jeśli element zostanie wygenerowany wewnątrz elementu docelowego, może zawierać elementu `KeepDuplicates` atrybutu. `KeepDuplicates` jest `Boolean` atrybut, który określa, czy element należy dodać do grupy docelowej, jeśli element jest identyczna z istniejącym elementem.  
  
 Jeśli element źródłowy i docelowy mają taką samą wartość Include, ale różne metadane, dodawania elementu nawet wtedy, gdy `KeepDuplicates` ma ustawioną wartość `false`. Pusta wartość dla tego atrybutu jest odpowiednikiem nieokreślenie go. `KeepDuplicates` Atrybut została wprowadzona w programie .NET Framework 4.5.  
  
 Poniższy przykład przedstawia sposób użycia `KeepDuplicates` atrybutu.  
  
```xml  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild.md)   
 [Porady: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md)   
 [Porady: wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Porady: wyświetlanie listy elementów rozdzielanych przecinkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Definicje elementów](../msbuild/item-definitions.md)   
 [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)   
 [Item, element (MSBuild)](../msbuild/item-element-msbuild.md)