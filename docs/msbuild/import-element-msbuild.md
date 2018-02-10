---
title: "Import — Element (MSBuild) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1d13f376068d7f5f32a55768dbd02520152f0a30
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="import-element-msbuild"></a>Import — Element (MSBuild)
Importuje zawartość pliku jeden projekt do innego pliku projektu.  

 \<Project>  
 \<Import >  

## <a name="syntax"></a>Składnia  

```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`Project`|Atrybut wymagany.<br /><br /> Ścieżka pliku projektu do zaimportowania. Nazwa ścieżki może zawierać symboli wieloznacznych. Pasujące pliki są importowane posortowane. Za pomocą tej funkcji, można dodać kod do projektu po prostu dodając pliku kodu do katalogu.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do sprawdzenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementy podrzędne  
 Brak  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Wymaganego głównego elementu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu.|  
|[Importgroup —](../msbuild/importgroup-element.md)|Zawiera kolekcję `Import` elementy zgrupowane w opcjonalny warunek.|  

## <a name="remarks"></a>Uwagi  
 Za pomocą `Import` elementu, można użyć ponownie kod, który jest wspólny dla wielu plików projektu. Ułatwia utrzymanie kodu, ponieważ wszelkie aktualizacje wprowadzone do udostępnionego kodu uzyskać propagowane do wszystkich projektów, które go zaimportować.  

 Według Konwencji projektu udostępnionego zaimportowane pliki są zapisywane jako pliki .targets, ale są standardowe [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliki projektu. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]nie uniemożliwiają importowanie projektu, który ma rozszerzenie nazwy pliku różne, ale zalecane jest użycie rozszerzenia .targets w celu zachowania spójności.  

 Ścieżki względne w projektach importowanych interpretowania względem katalogu projektu importowania. W związku z tym jeśli plik projektu jest importowany do wielu plików projektu w różnych lokalizacjach, ścieżek względnych w zaimportowanego pliku projektu zostanie potraktowany inaczej dla każdego zaimportowanego projektu.  

 Wszystkie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zastrzeżone właściwości, które odnoszą się do pliku projektu, na przykład `MSBuildProjectDirectory` i `MSBuildProjectFile`, który odwołuje się do zaimportowanego projektu są przypisane wartości na podstawie importowania pliku projektu.  

 Jeśli importowany projekt nie ma `DefaultTargets` atrybutu zaimportowane projekty są poddawane inspekcji w kolejności, są one importowane, a wartość pierwszego odnalezione `DefaultTargets` atrybut jest używany. Na przykład, jeśli ProjectA importuje ProjectB i ProjectC (w tej kolejności) i ProjectB importuje ProjectD [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] najpierw szuka `DefaultTargets` określone na ProjectA, a następnie ProjectB, a następnie ProjectD, a na końcu ProjectC.  

 Schemat zaimportowanego projektu jest identyczna jak standardowe projektu. Mimo że [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może być zdolny do skompilowania zaimportowanego projektu, jest mało prawdopodobne, ponieważ zwykle zaimportowanego projektu nie zawiera informacji na temat właściwości do zestawu lub kolejność elementów docelowych uruchomienia. Importowany projekt zależy od projektu, do którego jest importowany do Przekaż te informacje.  

> [!NOTE]
>  Podczas importowania warunkowe instrukcje pracy w MSBuilds wiersza polecenia, nie działają przy użyciu programu MSBuild w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE). Importy warunkowego są oceniane przy użyciu wartości configuration i platform, które są ustawiane po załadowaniu projektu. Jeśli następnie wprowadzono zmiany wymagające ponownej oceny warunków w pliku projektu, na przykład zmiana platformy, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] reevaluates warunki właściwości i elementów, ale nie w przypadku importów. Import został pominięty, ponieważ nie jest ponownie szacowane warunkowego importu.  
>   
>  Aby obejść ten problem, umieść warunkowego Importy w plikach TARGETS lub umieść kod w bloku warunkowego, takich jak [wybierz Element (MSBuild)](../msbuild/choose-element-msbuild.md) bloku.  

## <a name="wildcards"></a>Symbole wieloznaczne  
 W .NET Framework 4 MSBuild umożliwia symbole wieloznaczne w atrybucie projektu. W przypadku symboli wieloznacznych wszystkich znalezionych dopasowań sortowania (w przypadku powtarzalności), a następnie są importowane w kolejności, jeśli kolejność miały jawnie ustawiona.  

 Jest to przydatne, jeśli chcesz zaoferować punkcie rozszerzenia, aby ktoś inny mógł zaimportować pliku bez konieczności jawnie dodać nazwę pliku do importowania pliku. W tym celu Microsoft.Common.Targets zawiera następujący wiersz w górnej części pliku.  

```xml  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  

## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono projekt, który zawiera kilka elementów i właściwości, a następnie importuje plik ogólnego projektu.  

```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <PropertyGroup>  
        <resourcefile>Strings.resx</resourcefile>  

        <compiledresources>  
            $(O)\$(MSBuildProjectName).Strings.resources  
        </compiledresources>  
    </PropertyGroup>  

    <ItemGroup>  
        <CSFile Include="*.cs" />  

        <Reference Include="System" />  
        <Reference Include="System.Data" />  
    </ItemGroup>  

    <Import Project="$(CommonLocation)\General.targets" />  
</Project>  
```  

## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Instrukcje: Użycie tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
