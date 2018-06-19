---
title: Maxframeworkversion — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4bc28fcc35a4a59852ef6864886acff4dc87ef60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139880"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion — Element (szablony Visual Studio)

Określa maksymalną wersję programu .NET Framework, która jest wymagana przez szablon. Określa wartość najwyższy dostępny w **wersja docelowego Frameworka** listy rozwijanej z **nowy projekt** okna dialogowego. Aby użytkownicy mogli wybrać wersję framework, należy także określić [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) jako minimalna wersja systemu .NET Framework dla szablonu.

> [!IMPORTANT]
> W programie Visual Studio 2017 wersji 15,6, **wersja docelowego Frameworka** listy rozwijanej nie jest już filtru dla szablonów wyświetlanych w **szablony** sekcji **nowy projekt** okna dialogowego. Zamiast tego **wersja docelowego Frameworka** listy rozwijanej działa jako selektor framework, dla wybranego szablonu.

 \<VSTemplate > \<TemplateData > \<maxframeworkversion — >

## <a name="syntax"></a>Składnia

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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

 Tekst musi być najwyższym numerze wersji programu .NET Framework, która jest dozwolona przez szablon.

## <a name="remarks"></a>Uwagi

`MaxFrameworkVersion` to opcjonalny element. `MaxFrameworkVersion` Elementu należy pominąć, chyba że jest wymagane w celu przypadkowo ograniczenia wersji obsługiwanych zakresu .NET Framework dla szablonu. Należy również pominąć, jeśli nie ma zastosowania do szablonu .NET Framework.

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

W tym przykładzie maksymalna wersja .NET Framework, która jest wymagana przez szablon, reprezentowany przez `MaxFrameworkVersion`, jest 4.7.1. Projekt utworzone za pomocą tego szablonu można kierować 4.7.1 do wersji .NET Framework.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
