---
title: "Porady: odwołania projektu MSBuild zestawu SDK | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/25/2018
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: jeffkl
ms.author: jeffkl
manager: angerlic
ms.workload:
- multiple
ms.openlocfilehash: 28027b21d3f562e3eda94dc91de16ddb38362d3c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-use-msbuild-project-sdks"></a>Porady: Użyj zestawów SDK projektu programu MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 15.0 wprowadzono koncepcję "Projekt zestawu SDK", który upraszcza przy użyciu software development kit wymagających właściwości i obiekty docelowe do zaimportowania.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```  
  
Podczas obliczania projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dodaje niejawne importów u góry i u dołu projektu:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>  
```  

## <a name="referencing-a-project-sdk"></a>Odwołanie do projektu zestawu SDK
 Istnieją trzy sposoby odwoływać się do projektu zestawu SDK

1. Użyj `Sdk` atrybutu `<Project/>` elementu:
    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```
    Niejawne importu jest dodawany do góry i u dołu projektu, zgodnie z powyższym opisem.  Format `Sdk` atrybutu `Name[/Version]` których wersja jest opcjonalne.  Na przykład można określić `My.Custom.Sdk/1.2.3`.

2. Użyj najwyższego poziomu `<Sdk/>` elementu:
    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```
   Niejawne importu jest dodawany do góry i u dołu projektu, zgodnie z powyższym opisem.  `Version` Atrybut nie jest wymagana.

3. Użyj `<Import/>` element w dowolnym miejscu w projekcie:
    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```
   Jawnie w tym elemencie imports w projekcie umożliwia pełną kontrolę nad kolejności.

   Korzystając z `<Import/>` elementu, można określić opcjonalny `Version` również atrybutu.  Na przykład można określić `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Jak są rozwiązywane zestawów SDK projektu
Podczas obliczania importu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dynamicznie rozpoznaje ścieżkę do zestawu SDK na podstawie nazwy i wersji określonego projektu.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]zawiera także listę zarejestrowanych mechanizmów rozpoznawania zestawu SDK, które wtyczek, które zlokalizować projektu zestawów SDK na tym komputerze.  Te wtyczki obejmują:

1. Na podstawie NuGet program rozpoznawania nazw który odpytuje pakietu skonfigurowanych źródeł danych na potrzeby pakiety NuGet zgodne, identyfikator i wersji określonego zestawu SDK.<br/>
   Ten mechanizm rozpoznawania jest aktywna tylko po wybraniu wersji opcjonalny i może służyć do każdego projektu niestandardowego zestawu SDK.  
2. Mechanizm rozpoznawania do .NET interfejsu wiersza polecenia, która rozpoznaje zestawy SDK, które są instalowane z interfejsu wiersza polecenia platformy .NET.<br/>
   Ten mechanizm rozpoznawania zestawów SDK projektu lokalizuje takich jak `Microsoft.NET.Sdk` i `Microsoft.NET.Sdk.Web` będące częścią produktu.
3. Domyślny program rozpoznawania nazw rozwiązujący zestawów SDK, które zostały zainstalowane przy użyciu programu MSBuild.

Program rozpoznawania nazw na podstawie NuGet SDK obsługuje określanie wersji w Twojej [global.json](https://docs.microsoft.com/en-us/dotnet/core/tools/global-json) która pozwala na kontrolowanie zestawu SDK w wersji projektu w jednym miejscu zamiast w każdego pojedynczego projektu:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```
Tylko jedna wersja każdy projekt zestawu SDK można użyć podczas kompilacji.  Jeśli odwołuje się dwie różne wersje tego samego projektu zestawu SDK, MSBuild będzie wysyłać ostrzeżenie.  Zaleca się **nie** Określ wersję w projektach, jeśli określono wersję w Twojej `global.json`.  

## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Dostosowywanie kompilacji](../msbuild/customize-your-build.md)   
