---
title: Element funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1bdb115168e2090448588866ba23ce934fc847c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="item-functions"></a>Funkcje elementów
Począwszy od programu MSBuild 4.0, kod w zadań i elementów docelowych można wywołać funkcji element, aby uzyskać informacje na temat elementów w projekcie. Te funkcje upraszczają pobierania elementów Distinct() i szybsze niż w pętli elementy.  
  
## <a name="string-item-functions"></a>Funkcje elementu ciągów  
 Można użyć właściwości i metod ciągów w programie .NET Framework do działania na dowolną wartość elementu. Aby uzyskać <xref:System.String> metod, określ nazwę metody. Aby uzyskać <xref:System.String> właściwości, należy określić nazwę właściwości po "get_".  
  
 Dla elementów, które mają wiele ciągów ciąg metody lub właściwości jest uruchamiany na każdym ciągu.  
  
 Poniższy przykład przedstawia sposób używania tych funkcji elementu ciągu.  
  
```xml  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## <a name="intrinsic-item-functions"></a>Funkcje wewnętrzne elementów  
 W poniższej tabeli przedstawiono funkcje wewnętrzne dostępne dla elementów.  
  
|Funkcja|Przykład|Opis|  
|--------------|-------------|-----------------|  
|`Count`|`@(MyItem->Count())`|Zwraca liczbę elementów.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|Zwraca odpowiednikiem `Path.DirectoryName` dla każdego elementu.|  
|`Distinct`|`@(MyItem->Distinct())`|Zwraca elementy, które mają różne `Include` wartości. Metadane jest ignorowana. Wynik porównania ma bez uwzględniania wielkości liter.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Zwraca elementy, które mają różne `itemspec` wartości. Metadane jest ignorowana. Porównanie jest uwzględniana wielkość liter.|  
|`Reverse`|`@(MyItem->Reverse())`|Zwraca elementy w odwrotnej kolejności.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Zwraca `boolean` wskazująca, czy dowolny element ma określonych metadanych, nazwę i wartość. Wynik porównania ma bez uwzględniania wielkości liter.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Zwraca elementy z ich metadanych wyczyszczone. Tylko `itemspec` są zachowywane.|  
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Zwraca elementy o nazwach określonych metadanych. Wynik porównania ma bez uwzględniania wielkości liter.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Zwraca wartości metadanych, których nazwa metadanych.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Zwraca elementy, które mają określone metadane nazwą i wartością. Wynik porównania ma bez uwzględniania wielkości liter.|  
  
 Poniższy przykład przedstawia użycie funkcji wewnętrznych elementów.  
  
```xml  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy](../msbuild/msbuild-items.md)
