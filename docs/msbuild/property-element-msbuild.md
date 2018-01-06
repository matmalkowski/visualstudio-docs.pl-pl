---
title: "Property — Element (MSBuild) | Dokumentacja firmy Microsoft"
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
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: "17"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a93b339a062bd2e0c8dc1bf626c4ad109fa2af2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="property-element-msbuild"></a>Property — Element (MSBuild)
Zawiera nazwę użytkownika zdefiniowanych właściwości i wartości. Dla każdej właściwości używane w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekt musi być określony jako element podrzędny `PropertyGroup` elementu.  

 \<Projekt >  
 \<PropertyGroup >  

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
