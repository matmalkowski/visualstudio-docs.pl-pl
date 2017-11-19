---
title: "Choose — Element (MSBuild) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: e199dbfc171688cd0970cf340aef0dfd3584155a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="choose-element-msbuild"></a>Choose — Element (MSBuild)
Oblicza elementy podrzędne, aby wybrać jeden zestaw `ItemGroup` elementów i/lub `PropertyGroup` elementy do oceny.  

 \<Projekt >  
 \<Wybierz >  
 \<Gdy >  
 \<Wybierz >  
 ...  
 \<W przeciwnym razie >  
 \<Wybierz >  
 ...  

## <a name="syntax"></a>Składnia  

```  
<Choose>  
    <When Condition="'StringA'=='StringB'">... </When>  
    <Otherwise>... </Otherwise>  
</Choose>  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  
 Brak.  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[W przeciwnym razie](../msbuild/otherwise-element-msbuild.md)|Element opcjonalny.<br /><br /> Określa blok kodu `PropertyGroup` i `ItemGroup` elementy do oceny, czy wszystkie warunki `When` obliczać elementy `false`. Może być zero lub jeden `Otherwise` elementów w `Choose` elementu, a musi być ostatnim elementem.|  
|[Kiedy](../msbuild/when-element-msbuild.md)|Element wymagany.<br /><br /> Określa możliwe blok kodu dla `Choose` element, aby wybrać. Może istnieć co najmniej jeden `When` elementów w `Choose` elementu.|  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[W przeciwnym razie](../msbuild/otherwise-element-msbuild.md)|Określa blok kodu do wykonania, jeśli wszystkie warunki `When` obliczać elementy `false`.|  
|[Projekt](../msbuild/project-element-msbuild.md)|Wymaganego głównego elementu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu.|  
|[Kiedy](../msbuild/when-element-msbuild.md)|Określa możliwe blok kodu dla `Choose` element, aby wybrać.|  

## <a name="remarks"></a>Uwagi  
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
