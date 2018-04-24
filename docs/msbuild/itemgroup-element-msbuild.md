---
title: ItemGroup — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 963c53ed0cd1e74e3e641ac04012e5d0380980fe
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="itemgroup-element-msbuild"></a>ItemGroup — Element (MSBuild)
Zawiera zestaw zdefiniowanych przez użytkownika [elementu](../msbuild/item-element-msbuild.md) elementów. Każdy element używany w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt musi być określony jako element podrzędny `ItemGroup` elementu.  
  
 \<Project>  
 \<ItemGroup>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Condition`|Atrybut opcjonalny. Warunek do sprawdzenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Element](../msbuild/item-element-msbuild.md)|Określa dane wejściowe dla procesu kompilacji. Może wynosić zero lub więcej `Item` elementów w `ItemGroup`.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Wymaganego głównego elementu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu.|  
|[docelowy](../msbuild/target-element-msbuild.md)|W programie .NET Framework 3.5, `ItemGroup` element może występować wewnątrz `Target` elementu. Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md).|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje kolekcji zdefiniowane przez użytkownika elementu `Res` i `CodeFiles` zadeklarowana wewnątrz `ItemGroup` elementu. Każdy z elementów w `Res` elementu Kolekcja zawiera element podrzędny użytkownika [itemmetadata —](../msbuild/itemmetadata-element-msbuild.md) elementu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementy](../msbuild/msbuild-items.md)   
 [Wspólne elementy projektów MSBuild](../msbuild/common-msbuild-project-items.md)