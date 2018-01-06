---
title: "Porady: Użycie zmiennych środowiskowych w kompilacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: "15"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b1a9999c38ef89416a2669f2e6e77226df38c9c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Porady: użycie zmiennych środowiskowych w kompilacji
Podczas tworzenia projektów często należy ustawić opcje kompilacji za pomocą informacji, która nie znajduje się w pliku projektu lub pliki wchodzące w skład projektu. Te informacje są zwykle przechowywane w zmiennych środowiskowych.  
  
## <a name="referencing-environment-variables"></a>Odwołanie do zmiennych środowiskowych  
 Wszystkie zmienne środowiskowe są dostępne dla [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) pliku projektu jako właściwości.  
  
> [!NOTE]
>  Jeśli plik projektu zawiera jawna definicja właściwości, która ma taką samą nazwę jak zmiennej środowiskowej, właściwość w pliku projektu zastępuje wartość zmiennej środowiskowej.  
  
#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Aby użyć zmiennej środowiskowej w projekcie programu MSBuild  
  
-   Odwołanie do zmiennej środowiska tak samo jak Zmienna zadeklarowana w pliku projektu. Na przykład następujący kod odwołuje się do zmiennej środowiskowej BIN_PATH:  
  
     `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
 Można użyć `Condition` atrybut, aby podać wartość domyślną dla właściwości, jeśli nie ustawiono zmiennej środowiskowej.  
  
#### <a name="to-provide-a-default-value-for-a-property"></a>Aby podać wartości domyślnej właściwości.  
  
-   Użyj `Condition` atrybutu dla właściwości ustawić wartość tylko wtedy, gdy właściwość nie ma wartości. Na przykład poniższy kod ustawia `ToolsPath` c:\tools tylko wtedy, gdy dla właściwości `ToolsPath` nie ustawiono zmiennej środowiskowej:  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  Nazwy właściwości nie jest rozróżniana tak zarówno `$(ToolsPath)` i `$(TOOLSPATH)` odwoływać się do tej samej zmiennej właściwości lub środowiska.  
  
## <a name="example"></a>Przykład  
 Następujące plik projektu używa zmiennych środowiskowych, aby określić lokalizację katalogów.  
  
```xml  
<Project DefaultTargets="FakeBuild">  
    <PropertyGroup>  
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>  
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">  
            C:\Tools  
        </ToolsPath>  
    </PropertyGroup>  
    <Target Name="FakeBuild">  
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
    [MSBuild ](../msbuild/msbuild.md)
    [MSBuild Properties](../msbuild/msbuild-properties.md)
 [Instrukcje: Kompilacja tych samych plików źródłowych przy użyciu różnych opcji](../msbuild/how-to-build-the-same-source-files-with-different-options.md)