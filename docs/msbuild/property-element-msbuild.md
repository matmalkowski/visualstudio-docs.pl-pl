---
title: Property — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f98e1cc8b3ce016580e477dfa648a493df1c1e8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="property-element-msbuild"></a>Property — Element (MSBuild)
Zawiera nazwę użytkownika zdefiniowanych właściwości i wartości. Dla każdej właściwości używane w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt musi być określony jako element podrzędny `PropertyGroup` elementu.  

 \<Project>  
 \<PropertyGroup>  

## <a name="syntax"></a>Składnia  

```  
<Property Condition="'String A' == 'String B'">  
    Property Value  
</Property>  
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
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element GROUPING dla właściwości.|  

## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest opcjonalna.  

 Ten tekst Określa wartość właściwości i może zawierać kod XML.  

## <a name="remarks"></a>Uwagi  
 Nazwy właściwości są ograniczone do tylko znaki ASCII. Wartości właściwości odwołuje się do projektu wprowadzania nazwy właściwości między "`$(`"i"`)`". Na przykład `$(builddir)\classes` rozwiąże "build\classes", jeśli `builddir` właściwość ma wartość `build`. Aby uzyskać więcej informacji na temat właściwości, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).  

## <a name="example"></a>Przykład  
 Poniższy kod ustawia `Optimization` właściwości `false` i `DefaultVersion` właściwości `1.0` Jeśli `Version` właściwość jest pusta.  

```xml  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  

## <a name="see-also"></a>Zobacz też
[Właściwości programu MSBuild](../msbuild/msbuild-properties.md)  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
