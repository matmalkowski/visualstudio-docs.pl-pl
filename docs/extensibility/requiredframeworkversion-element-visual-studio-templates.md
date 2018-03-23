---
title: RequiredFrameworkVersion — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6490c75f7ca57dbb287da818dacd02574025f00f
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion — Element (szablony Visual Studio)

Określa minimalną wersję platformy .NET, który jest wymagany przez szablon. Powoduje on **wersja docelowego Frameworka** listy rozwijanej, który będzie wyświetlany w **nowy projekt** okna dialogowego. `RequiredFrameworkVersion` Element określa również wartością najniższą dostępne w menu rozwijanym.

> [!IMPORTANT]
> W programie Visual Studio 2017 wersji 15,6, **wersja docelowego Frameworka** listy rozwijanej nie jest już filtru dla szablonów wyświetlanych w **szablony** sekcji **nowy projekt** okna dialogowego. Zamiast tego elementu dropdown działa jako selektor framework, dla wybranego szablonu.

 \<VSTemplate > \<TemplateData > \<RequiredFrameworkVersion >

## <a name="syntax"></a>Składnia

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Tekst musi być minimalna liczba wersji programu .NET Framework, która jest wymagana dla szablonu.

## <a name="remarks"></a>Uwagi

`RequiredFrameworkVersion` to opcjonalny element. Użyj tego elementu tylko wtedy, gdy szablon obsługuje minimalnej określonej wersji (i nowszych wersjach, jeśli istnieją) programu .NET Framework. Jeśli określisz `RequiredFrameworkVersion` elementu i szablonu nie obsługuje określonego minimalna wersja programu .NET Framework, **wersja docelowego Frameworka** listy rozwijanej wyświetlany, gdy nie ma zastosowania.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia metadanych dla standardowej [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu klasy.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

W tym przykładzie minimalna wersja programu .NET Framework, która jest wymagana przez szablon, reprezentowany przez `RequiredFrameworkVersion`, to 3.0. Projekt utworzone za pomocą tego szablonu można kierować wersje programu .NET Framework, zaczynając od 3.0.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
- [Określanie konkretnej wersji programu .NET Framework jako docelowej](../ide/targeting-a-specific-dotnet-framework-version.md)
