---
title: "Element — Element (MSBuild) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c57923c75d1ae62b45b6ac288e75ef4e34a2f742
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="item-element-msbuild"></a>Item — Element (MSBuild)
Zawiera element zdefiniowane przez użytkownika i jego metadanych. Każdy element, który jest używany w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt musi być określony jako element podrzędny `ItemGroup` elementu.  

 \<Project>  
 \<ItemGroup>  
 \<Element >  

## <a name="syntax"></a>Składnia  

```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  

## <a name="specify-metadata-as-attributes"></a>Określ metadanych jako atrybuty
W MSBuild 15.1 lub nowszym wszystkich metadanych o nazwie, która nie koliduje to z bieżącą listę atrybutów opcjonalnie może zostać wyrażona jako atrybut.

Na przykład aby określić listę pakietów NuGet, należy zwykle użyje przypominać następującą składnię.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Teraz, jednak można przekazać `Version` metadanych jako atrybut, taki jak następującej składni:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />  
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`Include`|Atrybut opcjonalny.<br /><br /> Plik lub symbol wieloznaczny w celu dołączenia do listy elementów.|  
|`Exclude`|Atrybut opcjonalny.<br /><br /> Plik lub symbolu wieloznacznego, aby wykluczyć z listy elementów.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczone. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`Remove`|Atrybut opcjonalny.<br /><br /> Plik lub symbolu wieloznacznego, aby usunąć z listy elementów.<br /><br />|  
|`KeepDuplicates`|Atrybut opcjonalny.<br /><br /> Określa, czy element należy dodać do grupy docelowej, jeśli jest identyczna z istniejącym elementem. Jeśli element źródłowy i docelowy mają taki sam `Include` wartość, ale różne metadane, element jest dodany, nawet jeśli `KeepDuplicates` ma ustawioną wartość `false`. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy został określony dla elementu w `ItemGroup` w `Target`.|  
|`KeepMetadata`|Atrybut opcjonalny.<br /><br /> Metadane dla elementów źródła do dodania do elementów docelowych. Metadane, których nazwy zostały określone na liście rozdzielanej średnikami są przenoszone z elementu źródłowego do elementu docelowego. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy został określony dla elementu w `ItemGroup` w `Target`.|  
|`RemoveMetadata`|Atrybut opcjonalny.<br /><br /> Metadane dla elementów źródła nie są przenoszone do elementów docelowych. Wszystkie metadane są przesyłane z elementu źródłowego do elementu docelowego, z wyjątkiem metadanych których nazwy są zawarte w Rozdzielana średnikami lista nazw. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).<br /><br /> Ten atrybut jest prawidłowy tylko wtedy, gdy został określony dla elementu w `ItemGroup` w `Target`.|  
|`Update`|Atrybut opcjonalny. (Dostępne tylko w przypadku projektów .NET Core w Visual Studio 2017 lub nowszej).<br /><br /> Umożliwia modyfikowanie metadanych pliku zawierającego przy użyciu glob.<br /><br />  Ten atrybut jest prawidłowy tylko wtedy, gdy został określony dla elementu w `ItemGroup` nie jest to w `Target`.|  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Zdefiniowane przez użytkownika elementu metadanych klucz, który zawiera wartość metadanych elementu. Może wynosić zero lub więcej `ItemMetadata` elementy w elemencie.|  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element GROUPING dla elementów.|  

## <a name="remarks"></a>Uwagi  
 `Item` elementy zdefiniować dane wejściowe w systemie kompilacji i są zgrupowane w kolekcji elementów na podstawie ich nazw kolekcji zdefiniowane przez użytkownika. Te kolekcji elementów mogą być używane jako parametry w celu [zadania](../msbuild/msbuild-tasks.md), który umożliwia poszczególnych elementów w kolekcjach wykonaj kroki procesu kompilacji. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  

 Przy użyciu notacji `@(` *Mojtyp* `)` umożliwia kolekcję elementów typu *Mojtyp* można rozszerzyć do Rozdzielana średnikami lista ciągów i przekazany do parametru. Jeśli parametr jest typu `string`, wartość parametru jest lista elementów, oddzielając je średnikami. Jeśli parametr jest tablicą ciągów (`string[]`), a następnie każdy element zostaną wstawione do tabeli na podstawie lokalizacji średnikami. Jeśli parametr zadania jest typu <xref:Microsoft.Build.Framework.ITaskItem> `[]`, wartość jest zawartość kolekcji elementów wraz z wszystkich metadanych dołączony. Aby ograniczyć każdego elementu przy użyciu znaków innych niż średnika, należy użyć składni `@(` *Mojtyp*`, '`*separatora*`')`.  

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Aparat można ocenić takie jak symbole wieloznaczne `*` i `?` i cykliczne symboli wieloznacznych, takich jak `/**/*.cs`. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  

## <a name="examples"></a>Przykłady  
 Poniższy przykładowy kod przedstawia sposób zadeklarować dwóch elementów typu `CSFile`. Drugi zadeklarowany element zawiera metadanych, który ma `MyMetadata` ustawioną `HelloWorld`.  

```xml  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
Poniższy przykładowy kod przedstawia sposób użycia `Update` atrybut do zmodyfikowania metadanych w pliku o nazwie somefile.cs, który został dostarczony przez glob. (Dostępne tylko w przypadku projektów .NET Core w Visual Studio 2017 lub nowszej).

```xml  
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>  
```  


## <a name="see-also"></a>Zobacz też  
 [Elementy](../msbuild/msbuild-items.md)   
 [Właściwości programu MSBuild](../msbuild/msbuild-properties.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
