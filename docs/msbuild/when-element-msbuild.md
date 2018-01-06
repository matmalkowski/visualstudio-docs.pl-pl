---
title: Gdy Element (MSBuild) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#When
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <When> Element [MSBuild]
- When Element [MSBuild]
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
caps.latest.revision: "9"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ed1fee60a7cda6d260833ba60d37a7a7a762d58e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="when-element-msbuild"></a>When — Element (MSBuild)
Określa możliwe blok kodu dla `Choose` element, aby wybrać.  
  
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
<When Condition="'StringA'=='StringB'">  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</When>  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|Warunek|Atrybut wymagany.<br /><br /> Warunek do oceny. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Wybierz pozycję](../msbuild/choose-element-msbuild.md)|Element opcjonalny.<br /><br /> Oblicza elementy podrzędne, aby wybrać jedną sekcję kod do wykonania. Może wynosić zero lub więcej `Choose` elementów w `When` elementu.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw zdefiniowanych przez użytkownika [elementu](../msbuild/item-element-msbuild.md) elementów. Może wynosić zero lub więcej `ItemGroup` elementów w `When` elementu.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Element opcjonalny.<br /><br /> Zawiera zestaw zdefiniowanych przez użytkownika [właściwości](../msbuild/property-element-msbuild.md) elementów. Może wynosić zero lub więcej `PropertyGroup` elementów w `When` elementu.|  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Choose, element (MSBuild)](../msbuild/choose-element-msbuild.md)|Oblicza elementy podrzędne, aby wybrać jedną sekcję kod do wykonania.|  

## <a name="remarks"></a>Uwagi  
 Jeśli `Condition` atrybutu zwraca wartość true, obiekt podrzędny `ItemGroup` i `PropertyGroup` elementy `When` elementu są wykonywane i wszystkie kolejne `When` elementy są pomijane.  

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
