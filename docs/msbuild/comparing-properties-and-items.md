---
title: Porównanie właściwości i elementów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d2464acb75d8ea8a309d788aa95dc86b44d47e9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="comparing-properties-and-items"></a>Porównanie właściwości i elementów
Właściwości programu MSBuild i elementy jest używany zarówno do przekazywania informacji do zadania, oceny warunków i przechowywać wartości, które można odwoływać się w pliku projektu.  
  
-   Właściwości są pary nazwa wartość. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).  
  
-   Obiekty, które zwykle odpowiadają pliki są elementy. Element obiekty można skojarzyć kolekcje metadanych. Metadane są pary nazwa wartość. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  
  
## <a name="scalars-and-vectors"></a>Wartości skalarne i wektorów  
 Ponieważ właściwości programu MSBuild pary nazwa wartość, które mieć tylko jedną wartość ciągu, są często opisane jako *skalarne*. Ponieważ typów elementów MSBuild to listy elementów, często są opisane jako *wektor*. Jednak w praktyce właściwości może reprezentować wiele wartości, a typy elementów może mieć elementów zero lub jeden.  
  
### <a name="target-dependency-injection"></a>Iniekcji zależności docelowych  
 Aby zobaczyć, jak właściwości może reprezentować wiele wartości, należy wziąć pod uwagę wspólnego wzorca użycia dla dodanie miejsca docelowego do listy elementów docelowych, które ma zostać utworzony. Ta lista jest zazwyczaj reprezentowany przez wartość właściwości z nazwy obiektów docelowych, oddzielonych średnikami.  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 `BuildDependsOn` Właściwość jest zwykle używana jako argument elementu docelowego `DependsOnTargets` atrybutu skutecznie konwertowanie do listy elementów. Tej właściwości można przesłonić, aby dodać element docelowy lub zmienić kolejność wykonywania docelowej. Na przykład  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Dodaje element docelowy CustomBuild listę docelową, podając `BuildDependsOn` wartość `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.  
  
 Począwszy od programu MSBuild 4.0 iniekcji zależności docelowych jest przestarzały. Użyj `AfterTargets` i `BeforeTargets` zamiast atrybutów. Aby uzyskać więcej informacji, zobacz [kolejność kompilacji docelowej](../msbuild/target-build-order.md).  
  
### <a name="conversions-between-strings-and-item-lists"></a>Konwertowanie pomiędzy ciągami a list elementów  
 MSBuild wykonuje konwersje do i z typów elementów i wartości ciągu, zgodnie z potrzebami. Aby zobaczyć, jak listy elementów może stać się wartość ciągu, należy rozważyć, co się dzieje, gdy typ elementu jest używany jako wartość właściwości programu MSBuild:  
  
```xml  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 Typ elementu OutputDir ma `Include` atrybutu o wartości "plików klucza\\; Certyfikaty\\". MSBuild analizuje ten ciąg do dwóch elementów: KeyFiles\ i certyfikatów\\. W przypadku typu elementu OutputDir jako wartość właściwości OutputDirList MSBuild konwertuje lub "spłaszcza" typ elementu w ciągu oddzielonych średnikami "plików klucza\\; Certyfikaty\\".  
  
## <a name="properties-and-items-in-tasks"></a>Właściwości i elementów w zadaniach  
 Właściwości i elementy są używane jako dane wejściowe i dane wyjściowe zadania programu MSBuild. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
 Właściwości są przekazywane do zadań jako atrybuty. W ramach zadania właściwość MSBuild jest reprezentowana przez typ właściwości, której wartość mogą być konwertowane do i z ciągu. Właściwość obsługiwane typy `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string`, i dowolny typ <xref:System.Convert.ChangeType%2A> może obsłużyć.  
  
 Elementy są przekazywane do zadań, jak <xref:Microsoft.Build.Framework.ITaskItem> obiektów. W ramach zadania <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> reprezentuje wartość elementu i <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> pobiera jego metadanych.  
  
 Listy elementów typu elementu mogą być przekazywane jako tablica `ITaskItem` obiektów. Począwszy od programu .NET Framework 3.5, elementy można usunąć z listy elementów w celu za pomocą `Remove` atrybutu. Ponieważ można ją usunąć elementy z listy elementów, istnieje możliwość dla typu elementu zawierały elementów. Jeśli listy elementów zostanie przekazany do zadania, kodu w zadaniu należy sprawdzić, czy tej możliwości.  
  
## <a name="property-and-item-evaluation-order"></a>Właściwości i elementu kolejność obliczania  
 W fazie oceny kompilacji zaimportowane pliki są włączone do kompilacji w kolejności ich występowania. Właściwości i elementów są zdefiniowane w trzech przebiegów w następującej kolejności:  
  
-   Właściwości są zdefiniowane i modyfikować w kolejności ich występowania.  
  
-   Definicje elementów są zdefiniowane i modyfikować w kolejności ich występowania.  
  
-   Elementy są zdefiniowane i modyfikować w kolejności ich występowania.  
  
 Podczas fazy wykonywania kompilacji właściwości i elementy, które są zdefiniowane w obiekty docelowe są oceniane razem w jednej fazie w kolejności ich występowania.  
  
 Jednak nie jest pełną wątku. Jeśli jest zdefiniowana właściwość, definicja elementu lub elementów, jego wartość jest szacowana. Ewaluator wyrażeń rozszerza ciąg, który określa wartość. Ciąg rozszerzenia jest zależna od fazy kompilacji. Poniżej przedstawiono bardziej szczegółowe kolejność obliczania właściwości i elementu:  
  
-   W fazie oceny kompilacji:  
  
    -   Właściwości są zdefiniowane i modyfikować w kolejności ich występowania. Funkcje właściwości są wykonywane. Wartości właściwości w postaci $(PropertyName) są rozwijane w wyrażeniach. Wartość właściwości jest równa rozwinięte wyrażenia.  
  
    -   Definicje elementów są zdefiniowane i modyfikować w kolejności ich występowania. Funkcje właściwości już zostały rozszerzone w wyrażeniach. Metadane wartości są ustawiane na rozszerzonych wyrażenia.  
  
    -   Typy elementów są zdefiniowane i modyfikować w kolejności, w jakiej widnieją. Element wartości w postaci @(ItemType) zostaną rozwinięte. Element przekształcenia również zostaną rozwinięte. Funkcje właściwości i wartości już zostały rozszerzone w wyrażeniach. Wartości elementów listy i metadanych są ustawiane na rozszerzonych wyrażenia.  
  
-   Podczas fazy wykonywania kompilacji:  
  
    -   Właściwości i elementy, które są zdefiniowane w obiekty docelowe są oceniane razem w kolejności ich występowania. Funkcje właściwości są wykonywane i wartości właściwości są rozwijane w wyrażeniach. Wartości elementów i przekształcenia elementu również zostaną rozwinięte. Wartości właściwości elementu typu wartości i wartości metadanych są ustawione na rozszerzonych wyrażenia.  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>Niewielkie skutków kolejność obliczania  
 W fazie oceny kompilacji obliczania właściwości poprzedza obliczania elementu. Niemniej jednak właściwości może mieć wartości, które wydają się zależą od wartości elementu. Rozważmy poniższy skrypt.  
  
```xml  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Wykonywanie zadania komunikat wyświetla ten komunikat:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 Jest to spowodowane wartość `KeyFileVersion` jest rzeczywiście ciągiem "@(KeyFile ->"% (wersja)")". Element i przekształcenia elementu nie zostały rozwinięte podczas najpierw definiowania właściwości, więc `KeyFileVersion` właściwość została przypisana wartość nierozwiniętego ciągu.  
  
 Podczas fazy wykonywania kompilacji podczas przetwarzania zadania komunikat MSBuild rozszerza ciąg "@(KeyFile ->"% (wersja)")" umożliwiające uzyskanie "1.0.0.3".  
  
 Należy zauważyć, że ten sam komunikat pojawiały się nawet wtedy, gdy właściwości i elementu grup zostały wycofane w kolejności.  
  
 Jako drugi przykład rozważ, co może się zdarzyć, gdy grupy właściwości i elementu znajdują się w obrębie obiektów docelowych:  
  
```xml  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Zadanie wiadomości wyświetla ten komunikat:  
  
```  
KeyFileVersion:   
```  
  
 Jest to spowodowane podczas fazy wykonywania kompilacji właściwości i elementu grup zdefiniowanych w obiekty docelowe są oceniane góry do dołu w tym samym czasie. Gdy `KeyFileVersion` jest zdefiniowany, `KeyFile` jest nieznany. W związku z tym transformacji elementu rozwijany do pustego ciągu.  
  
 W takim przypadku odwracanie kolejności grup właściwości i elementu przywraca oryginalnej wiadomości:  
  
```xml  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Wartość `KeyFileVersion` jest ustawiona na "1.0.0.3", a nie "@(KeyFile ->"% (wersja)")". Zadanie wiadomości wyświetla ten komunikat:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)