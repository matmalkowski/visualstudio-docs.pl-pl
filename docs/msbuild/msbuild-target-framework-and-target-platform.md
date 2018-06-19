---
title: Platforma docelowa programu MSBuild i platformy docelowej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93eff2375e9b1cab043a30acaf5ebec31ba8e89f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31578279"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Platforma docelowa programu MSBuild
Projekt można wbudować do uruchomienia na *platformy docelowej*, czyli określonej wersji programu .NET Framework i *platformy docelowej*, czyli architektura konkretnego oprogramowania.  Na przykład możesz zastosować aplikacji do uruchamiania na .NET Framework 2.0 na platformie 32-bitowego, która jest zgodna z rodziny procesorów 802 x 86 ("x86"). Kombinacja platformy docelowej i platforma docelowa jest nazywany *kontekst docelowy*.  
  
## <a name="target-framework-and-profile"></a>Platforma docelowa i profilu  
 Platforma docelowa jest konkretnej wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] skompilowanego projektu do uruchamiania na. Specyfikacja platformy docelowej jest wymagana, ponieważ dzięki funkcji kompilatora i odwołania do zestawów, które są na wyłączność dla tej wersji platformy.  
  
 Obecnie dostępne są następujące wersje programu .NET Framework:  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 (dołączone do programu Visual Studio 2005)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0 (objęte [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 (objęte [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.2  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6 (objęte [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.1  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6.2  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7  

-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.7.1  
  
 Na liście zestawów, że każdy udostępnia odwołanie do wersji programu .NET Framework różnią się między sobą. Na przykład nie można utworzyć aplikacji Windows Presentation Foundation (WPF), chyba, że projekt jest przeznaczony dla platformy .NET Framework w wersji 3.0 lub nowszym.  
  
 Platforma docelowa jest określona w `TargetFrameworkVersion` właściwość w pliku projektu. Za pomocą stron właściwości projektu w programie Visual Studio zintegrowane środowisko programistyczne (IDE), można zmienić platformę docelową dla projektu. Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Dostępne wartości `TargetFrameworkVersion` są `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v.4.6.1`, `v4.6.2`, `4.7`, i `4.7.1`.  
  
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
  
-   `x86` Określa 32-bitowy system operacyjny Windows jest uruchomiona na z procesorem Intel 80 x 86 lub jego odpowiednik.  

-   `x64` Określa 64-bitowy system operacyjny Windows jest uruchomiona na z procesorem Intel x64 lub równoważnej.
  
-   `Xbox` Określa platformę Microsoft konsoli Xbox 360.  
  
 A *platformy docelowej* czy platforma określonego projektu jest oparty na. Platforma docelowa jest określona w `PlatformTarget` kompilacji właściwość w pliku projektu. Za pomocą stron właściwości projektu można zmienić platformę docelową lub **programu Configuration Manager** w IDE.  
  
```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
</PropertyGroup>  
  
```  
  
 A *konfiguracji docelowej* to podzbiór platformy docelowej. Na przykład `x86``Debug` konfiguracji nie zawiera większości optymalizacji kodu. Konfiguracja obiektu docelowego jest określona w `Configuration` kompilacji właściwość w pliku projektu. Można zmienić konfiguracji docelowej za pomocą stron właściwości projektu lub **programu Configuration Manager**.  
  
```xml  
<PropertyGroup>  
   <PlatformTarget>x86</PlatformTarget>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przeznaczanie dla wielu platform](../msbuild/msbuild-multitargeting-overview.md)