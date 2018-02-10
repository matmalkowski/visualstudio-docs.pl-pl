---
title: "Otherwise — Element (MSBuild) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e0b824b8be8b3697673d0d1f09a20b6a7c1cee58
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="otherwise-element-msbuild"></a>Otherwise — Element (MSBuild)
Określa blok kodu do wykonania w przypadku i tylko wtedy, gdy warunki wszystkich `When` obliczać elementy `false`.  

 \<Project>  
 \<Wybierz >  
 \<Gdy >  
 \<Wybierz >  
 ...  
 \<W przeciwnym razie >  
 \<Wybierz >  
 ...  

## <a name="syntax"></a>Składnia  

```  
<Otherwise>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</Otherwise>  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  
 Brak.  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Wybierz pozycję](../msbuild/choose-element-msbuild.md)|Element opcjonalny.<br /><br /> Oblicza elementy podrzędne, aby wybrać jedną sekcję kod do wykonania. Może wynosić zero lub więcej `Choose` elementów w `Otherwise` elementu.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw zdefiniowanych przez użytkownika [elementu](../msbuild/item-element-msbuild.md) elementów. Może wynosić zero lub więcej `ItemGroup` elementów w `Otherwise` elementu.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw zdefiniowanych przez użytkownika [właściwości](../msbuild/property-element-msbuild.md) elementów. Może wynosić zero lub więcej `PropertyGroup` elementów w `Otherwise` elementu.|  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Wybierz pozycję](../msbuild/choose-element-msbuild.md)|Oblicza elementy podrzędne, aby wybrać jedną sekcję kod do wykonania.|  

## <a name="remarks"></a>Uwagi  
 Może istnieć tylko jedna `Otherwise` element `Choose` elementu, a musi być ostatnim elementem.  

 `Choose`, `When`, I `Otherwise` elementy są używane razem w sposób, aby wybrać jedną sekcję kod do wykonania poza liczba możliwych alternatyw. Aby uzyskać więcej informacji, zobacz [konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md).  

## <a name="example"></a>Przykład  
 Następujące projektu używa `Choose` element, aby wybrać który zestaw wartości właściwości w `When` elementy, które można ustawić. Jeśli `Condition` oba atrybuty `When` elementy obliczać `false`, wartości właściwości w `Otherwise` ustawiono element.  

```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
        <Otherwise>  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\$(Configuration)\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
        </Otherwise>  
        </Choose>  
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
</Project>  
```  

## <a name="see-also"></a>Zobacz też  
 [Konstrukcje warunkowe](../msbuild/msbuild-conditional-constructs.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
