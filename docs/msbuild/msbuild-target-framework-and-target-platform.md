---
title: Platforma docelowa programu MSBuild i platformy docelowej | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: "10"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: cdfbe126e8a647cda4c8e29e50591a1aa229df80
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-target-framework-and-target-platform"></a>Platforma docelowa programu MSBuild
Projekt można wbudować do uruchomienia na *platformy docelowej*, czyli określonej wersji programu .NET Framework i *platformy docelowej*, czyli architektura konkretnego oprogramowania.  Na przykład możesz zastosować aplikacji do uruchamiania na .NET Framework 2.0 na platformie 32-bitowego, która jest zgodna z rodziny procesorów 802 x 86 ("x86"). Kombinacja platformy docelowej i platforma docelowa jest nazywany *kontekst docelowy*.  
  
## <a name="target-framework-and-profile"></a>Platforma docelowa i profilu  
 Platforma docelowa jest konkretnej wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] skompilowanego projektu do uruchamiania na. Specyfikacja platformy docelowej jest wymagana, ponieważ dzięki funkcji kompilatora i odwołania do zestawów, które są na wyłączność dla tej wersji platformy.  
  
 Obecnie dostępne są następujące wersje programu .NET Framework:  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 (dołączone do programu Visual Studio 2005)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0 (objęte [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 (objęte [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4 (dołączone do programu Visual Studio 2010)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5 (objęte [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.1 (objęte [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.2  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6 (objęte [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])  
  
 Na liście zestawów, że każdy udostępnia odwołanie do wersji programu .NET Framework różnią się między sobą. Na przykład nie można utworzyć aplikacji Windows Presentation Foundation (WPF), chyba, że projekt jest przeznaczony dla platformy .NET Framework w wersji 3.0 lub nowszym.  
  
 Platforma docelowa jest określona w `TargetFrameworkVersion` właściwość w pliku projektu. Za pomocą stron właściwości projektu w programie Visual Studio zintegrowane środowisko programistyczne (IDE), można zmienić platformę docelową dla projektu. Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Dostępne wartości `TargetFrameworkVersion` są `v2.0`, `v3.0`, `v3.5`, `v4.0`, `v4.5`, `v4.5.1`, `v4.5.2`, i `v4.6`.  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 A *docelowego profilu* to podzbiór platformy docelowej. Na przykład profilu klienta .NET Framework 4 nie zawiera odwołania do zestawów programu MSBuild.  
  
 Docelowy profil jest określona w `TargetFrameworkProfile` właściwość w pliku projektu. Docelowy profil można zmienić przy użyciu platformy docelowej na stronach właściwości projektu w środowisku IDE. Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Platforma docelowa  
 A *platformy* jest kombinacja sprzętu i oprogramowania, które definiuje określonego środowiska. Na przykład  
  
-   `x86`Określa 32-bitowy system operacyjny Windows jest uruchomiona na z procesorem Intel 80 x 86 lub jego odpowiednik.  
  
-   `Xbox`Określa platformę Microsoft konsoli Xbox 360.  
  
 A *platformy docelowej* czy platforma określonego projektu jest oparty na. Platforma docelowa jest określona w `Platform` kompilacji właściwość w pliku projektu. Za pomocą stron właściwości projektu można zmienić platformę docelową lub **programu Configuration Manager** w IDE.  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 A *konfiguracji docelowej* to podzbiór platformy docelowej. Na przykład `x86``Debug` konfiguracji nie zawiera większości optymalizacji kodu. Konfiguracja obiektu docelowego jest określona w `Configuration` kompilacji właściwość w pliku projektu. Można zmienić konfiguracji docelowej za pomocą stron właściwości projektu lub **programu Configuration Manager**.  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przeznaczanie dla wielu platform](../msbuild/msbuild-multitargeting-overview.md)