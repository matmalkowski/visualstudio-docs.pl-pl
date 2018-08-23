---
title: Property — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
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
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9f3494cb46aa18d9b79d29aa2936d31ae55997b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678195"
---
# <a name="property-element-msbuild"></a>Property — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Property — Element (MSBuild)](https://docs.microsoft.com/visualstudio/msbuild/property-element-msbuild).  
  
  
Zawiera użytkownika zdefiniowane nazwy i wartości właściwości. Dla każdej właściwości używana w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekt musi być określony jako element podrzędny elementu `PropertyGroup` elementu.  
  
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
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczone. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element grupujący właściwości.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest opcjonalna.  
  
 Ten tekst Określa wartość właściwości i może zawierać kod XML.  
  
## <a name="remarks"></a>Uwagi  
 Nazwy właściwości są ograniczone do tylko znaki ASCII. Wartości właściwości są przywoływane w projekcie, umieszczając nazwę właściwości między "`$(`"i"`)`". Na przykład `$(builddir)\classes` rozwiąże "build\classes", jeśli `builddir` właściwość ma wartość `build`. Aby uzyskać więcej informacji na temat właściwości, zobacz [właściwości programu MSBuild](msbuild-properties1.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod ustawia `Optimization` właściwości `false` i `DefaultVersion` właściwości `1.0` Jeśli `Version` właściwość jest pusta.  
  
```  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Zobacz też
[Właściwości programu MSBuild](msbuild-properties1.md)  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)



