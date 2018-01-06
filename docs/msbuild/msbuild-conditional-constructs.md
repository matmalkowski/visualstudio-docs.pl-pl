---
title: Konstrukcje warunkowe MSBuild | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
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
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: "9"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c95420accf377cc4debaae88e1290c3056b5001a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-conditional-constructs"></a>Konstrukcje warunkowe MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]udostępnia mechanizm dla dowolnego / lub przetwarzania z [wybierz](../msbuild/choose-element-msbuild.md), [podczas](../msbuild/when-element-msbuild.md), i [w przeciwnym razie](../msbuild/otherwise-element-msbuild.md) elementów.  
  
## <a name="using-the-choose-element"></a>Przy użyciu Choose — Element  
 `Choose` Element zawiera szereg `When` elementy o `Condition` atrybuty, które są sprawdzane w kolejności od góry do dołu, dopóki jeden daje w wyniku `true`. Jeśli istnieje więcej niż jedna `When` daje w wyniku element `true`, tylko pierwszy z nich jest używana. `Otherwise` Elementu, jeśli istnieje, zostanie obliczone w razie żadnego warunku w `When` daje w wyniku element `true`.  
  
 `Choose`elementy mogą być używane jako elementy podrzędne `Project`, `When` i `Otherwise` elementy. `When`i `Otherwise` elementy mogą mieć `ItemGroup`, `PropertyGroup`, lub `Choose` elementy podrzędne.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Choose` i `When` elementy albo / lub przetwarzania. W zależności od wartości są ustawione właściwości i elementów dla projektu `Configuration` właściwości.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='Debug' ">  
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
    </Choose>  
    <!-- Rest of Project -->  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Choose — Element (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [Gdy Element (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Otherwise — Element (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)