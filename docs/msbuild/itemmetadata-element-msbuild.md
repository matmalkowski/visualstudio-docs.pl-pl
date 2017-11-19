---
title: "Itemmetadata — Element (MSBuild) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: "17"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: c48e85d299ed55de9eee286ca0f7a853cc4c669e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata — Element (MSBuild)
Zawiera klucz metadanych elementu zdefiniowane przez użytkownika, który zawiera wartość metadanych elementu. Element może mieć dowolną liczbę par klucz wartość metadanych.  

 \<Projekt >  
 \<ItemGroup >  
 \<Element >  

## <a name="syntax"></a>Składnia  

```  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do sprawdzenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Element](../msbuild/item-element-msbuild.md)|Element zdefiniowane przez użytkownika, który definiuje dane wejściowe dla procesu kompilacji.|  

## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest opcjonalna.  

 Ten tekst Określa wartość elementu metadanych, które mogą być tekstem lub XML.  

## <a name="remarks"></a>Uwagi  

## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób dodawania `Culture` metadanych z wartością `fr` do elementu `CSFile`.  

```xml  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  

## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementy](../msbuild/msbuild-items.md)
