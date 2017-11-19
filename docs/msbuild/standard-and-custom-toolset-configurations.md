---
title: "Konfiguracje standardowego i niestandardowego zestawu narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: "31"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: a1b0b6e2cc44193a684c6f411df908b0a54d31f1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="standard-and-custom-toolset-configurations"></a>Konfiguracje standardowego i niestandardowego zestawu narzędzi
Zestaw narzędzi MSBuild zawiera odwołania do zadań, elementy docelowe i narzędzi, które służy do tworzenia aplikacji projektu. MSBuild obejmuje standardowych narzędzi, ale można również utworzyć niestandardowe procesami. Aby uzyskać informacje o określaniu zestawu narzędzi, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)  
  
## <a name="standard-toolset-configurations"></a>Konfiguracje standardowego zestawu narzędzi  
 MSBuild 12.0 obejmuje następujące procesami standardowe:  
  
|ToolsVersion|Ścieżka zestawu narzędzi (określoną we właściwości kompilacji MSBuildToolsPath lub MSBuildBinPath)|  
|------------------|--------------------------------------------------------------------------------------------|  
|2.0|*Ścieżka instalacji systemu Windows*\Microsoft.Net\Framework\v2.0.50727\|  
|3.5|*Ścieżka instalacji systemu Windows*\Microsoft.NET\Framework\v3.5\|  
|4.0|*Ścieżka instalacji systemu Windows*\Microsoft.NET\Framework\v4.0.30319\|  
|12.0|*% ProgramFiles %*\MSBuild\12.0\bin|  
  
 `ToolsVersion` Wartość określa, który zestaw narzędzi jest używany przez projekt, który generuje Visual Studio. W [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] wartością domyślną jest "12.0" (niezależnie od tego, jakie wersja określona w pliku projektu), ale ten atrybut można zastąpić przy użyciu **/toolsversion** przełącznik w wierszu polecenia. Informacje dotyczące tego atrybutu i inne sposoby określ `ToolsVersion`, zobacz [Zastępowanie ustawienia ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 Jeśli `ToolsVersion` nie zostanie określona, klucz rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\\< numer wersji\>\DefaultToolsVersion** definiuje `ToolsVersion`, który jest zawsze 2.0.  
  
 Następujące klucze rejestru, określ ścieżkę instalacji programu MSBuild.exe.  
  
|Klucz rejestru|Nazwa klucza|Wartość klucza ciągu|  
|------------------|--------------|----------------------|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0\|MSBuildToolsPath|Ścieżka instalacji programu .NET framework 2.0|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\|MSBuildToolsPath|Ścieżka instalacji programu .NET framework 3.5|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\|MSBuildToolsPath|Ścieżka instalacji programu .NET framework 4|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\12.0\|MSBuildToolsPath|Ścieżka instalacji programu MSBuild|  
  
### <a name="sub-toolsets"></a>Podzestawach  
 Jeśli klucz rejestru w poprzedniej tabeli podklucz, MSBuild używa go określić ścieżkę sub zestawu narzędzi mogą zastąpić ścieżki w zestawie narzędzi nadrzędnej. Przykładem jest następujący podklucz:  
  
 \HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  
  
 Jeśli wszystkie właściwości są zdefiniowane zarówno podstawowy zestaw narzędzi i wybranych narzędzi sub, są używane w zestawie narzędzi sub definicji właściwości. Na przykład definiuje zestaw narzędzi MSBuild 4.0 `SDK40ToolsPath` wskaż 7.0a zestawu SDK, ale MSBuild 4.0\11.0 zestawu narzędzi definiuje tej właściwości, aby wskazywał 8.0a zestawu SDK. Jeśli `VisualStudioVersion` jest nieustawioną `SDK40ToolsPath` mogą wskazywać na 7.0a, ale jeśli `VisualStudioVersion` ustawiono 11.0, właściwość zamiast tego mogą wskazywać na 8.0a.  
  
 `VisualStudioVersion` Kompilacji właściwość wskazuje, czy narzędzi sub staje się aktywny. Na przykład `VisualStudioVersion` wartość "12.0" Określa zestaw narzędzi sub MSBuild 12.0. Aby uzyskać więcej informacji, zobacz sekcję podzestawach [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
> [!NOTE]
>  Zaleca się unikać zmiany tych ustawień. Można jednak dodać własne ustawienia i zdefiniuj definicje komputera niestandardowego zestawu narzędzi, zgodnie z opisem w następnej sekcji.  
  
## <a name="custom-toolset-definitions"></a>Definicje niestandardowego zestawu narzędzi  
 Podczas standardowych narzędzi nie spełnia wymagań kompilacji, można utworzyć niestandardowego zestawu narzędzi. Na przykład może być scenariusza laboratorium kompilacji musi mieć oddzielnym systemie na potrzeby tworzenia [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów. Przy użyciu niestandardowego zestawu narzędzi, można przypisać wartości niestandardowych w celu `ToolsVersion` atrybutu podczas tworzenia projektów lub uruchom MSBuild.exe. W ten sposób można także użyć `$(MSBuildToolsPath)` właściwości, aby zaimportować pliki .targets z tego katalogu, a także definiowanie własnych właściwości niestandardowego zestawu narzędzi, które mogą być używane dla każdego projektu, który korzysta z tego zestawu narzędzi.  
  
 Określ niestandardowego zestawu narzędzi w pliku konfiguracyjnym MSBuild.exe (lub narzędzia niestandardowego, który jest hostem aparat MSBuild, jeśli jest to, co w przypadku korzystania). Na przykład pliku konfiguracyjnego MSBuild.exe mogą obejmować następującej definicji zestawu narzędzi, jeśli zamierza zastępują domyślne zachowanie ToolsVersion 12.0.  
  
```xml  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 `<msbuildToolsets>`musi także być zdefiniowany w pliku konfiguracji, w następujący sposób.  
  
```xml  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  Odczyt poprawnie, `<configSections>` musi być pierwszym podsekcji w `<configuration>` sekcji.  
  
 `ToolsetConfigurationSection`jest sekcji konfiguracji niestandardowej, które mogą być używane przez każdego hosta MSBuild dla konfiguracji niestandardowej. Jeśli używasz niestandardowego zestawu narzędzi hosta nie trzeba wykonywać żadnych czynności można zainicjować aparatu kompilacji, z wyjątkiem Podaj wpisy w pliku konfiguracji. Definiując wpisy w rejestrze, można określić procesami komputera, które mają zastosowanie do MSBuild.exe, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], a wszystkie hosty programu MSBuild.  
  
> [!NOTE]
>  Jeśli plik konfiguracji definiuje ustawienia `ToolsVersion` została już zdefiniowana w rejestrze, dwie definicje nie zostały scalone. Definicja w pliku konfiguracji ma pierwszeństwo i ustawienia w rejestrze tego `ToolsVersion` są ignorowane.  
  
 Następujące właściwości są specyficzne dla wartości `ToolsVersion` który jest używany w projektach:  
  
-   **$(MSBuildBinPath)** ustawiono `ToolsPath` wartości określonej w rejestrze lub w pliku konfiguracyjnym gdzie `ToolsVersion` jest zdefiniowany. `$(MSBuildToolsPath)` Ustawienie w rejestrze lub w pliku konfiguracyjnym Określa lokalizację do podstawowych zadań i elementów docelowych. W pliku projektu mapowany do właściwości $(MSBuildBinPath), a także z właściwością $(MSBuildToolsPath).  
  
-   `$(MSBuildToolsPath)`jest zastrzeżony właściwość, która jest dostarczana przez właściwość MSBuildToolsPath, która została określona w pliku konfiguracji. (Ta właściwość zastępuje `$(MSBuildBinPath)`. Jednak `$(MSBuildBinPath)` jest przenoszone zgodność.) Zdefiniuj niestandardowego zestawu narzędzi, albo `$(MSBuildToolsPath)` lub `$(MSBuildBinPath)` , ale nie obu, chyba że mają taką samą wartość.  
  
 Można również dodać właściwości niestandardowe, specyficzne dla ToolsVersion do pliku konfiguracji przy użyciu takiej samej składni, który umożliwia dodawanie właściwości MSBuildToolsPath. Aby udostępnić te właściwości niestandardowe do pliku projektu, użyj takiej samej nazwie jak nazwa wartość, która została określona w pliku konfiguracji. Procesami, ale nie podzestawach mogą określić w pliku konfiguracji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)