---
title: SortOrder — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b963b6e74b7c24d31ddc611407df22380ff8bb60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder — Element (szablony Visual Studio)
Określa wartość, która służy do rozmieszczania szablonu, między innymi szablony w tej samej kategorii, pojawiającą się w jednej **nowy projekt** lub **Dodaj nowy element** okno dialogowe.  
  
 \<VSTemplate>  
 \<TemplateData >  
 \<SortOrder >  
  
## <a name="syntax"></a>Składnia  
  
```  
<SortOrder> ... </SortOrder>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablonu i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 `integer` Reprezentujący wartość kolejności sortowania.  
  
## <a name="remarks"></a>Uwagi  
 `SortOrder` to opcjonalny element. Wartość domyślna to 100, a wszystkie wartości musi być wielokrotnością liczby 10.  
  
 `SortOrder` Element jest ignorowany dla szablonów utworzonych przez użytkownika. Wszystkie szablony utworzone przez użytkownika są sortowane w kolejności alfabetycznej.  
  
 Szablony, które mają wartości kolejności sortowania niski pojawiają się w jednym **nowy projekt** lub **nowy element Dodaj** przed szablonów, które mają wartości kolejności sortowania wysoki — okno dialogowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia metadanych dla standardowej [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu klasy.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 W tym przykładzie `SortOrder` element jest stosunkowo wysoka. Istnieje prawdopodobieństwo, że inne [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonów elementów będzie mieć `SortOrder` wartości mniejszej niż `290` i pojawi się przed tego szablonu w **nowy element** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)