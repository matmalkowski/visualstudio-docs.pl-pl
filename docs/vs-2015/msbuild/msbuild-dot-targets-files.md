---
title: Program MSBuild. Jest przeznaczony dla plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93207bb46b8294fe0b4fb3d93416e2fdabe61273
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684191"
---
# <a name="msbuild-targets-files"></a>MSBuild — Pliki .Targets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [MSBuild. Jest przeznaczony dla plików](https://docs.microsoft.com/visualstudio/msbuild/msbuild-dot-targets-files).  
  
  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zawiera kilka plików .targets, które zawierają elementy, właściwości, cele i zadania dla typowych scenariuszy. Te pliki są automatycznie importowane do większości [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pliki w celu uproszczenia konserwacji i czytelności projektu.  
  
 Projekty zazwyczaj importują jeden lub więcej plików .targets, aby zdefiniować ich proces kompilacji. Na przykład [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekt utworzony w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zaimportuje Microsoft.CSharp.targets, który importuje Microsoft.Common.targets. [!INCLUDE[csprcs](../includes/csprcs-md.md)] Sam projekt Definiowanie elementów i właściwości określonych do tego projektu, ale standard tworzenia reguły [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektu są zdefiniowane w plikach .targets zaimportowane.  
  
 `$(MSBuildToolsPath)` Określa ścieżkę te wspólne pliki .targets. Jeśli `ToolsVersion` 4.0, pliki znajdują się w następującej lokalizacji: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
>  Aby uzyskać informacje o sposobie tworzenia własnych elementów docelowych, zobacz [cele](../msbuild/msbuild-targets.md). Aby uzyskać informacje o sposobie używania `Import` element, aby wstawić plik projektu do innego pliku projektu, zobacz [Import — Element (MSBuild)](../msbuild/import-element-msbuild.md) i [porady: użycie tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>Wspólne. Pliki elementów docelowych  
  
|. Plik docelowy|Opis|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Definiuje kroki w standardowym procesem kompilacji dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektów.<br /><br /> Zaimportowanych przez pliki Microsoft.CSharp.targets i Microsoft.VisualBasic.targets, które obejmują następującą instrukcję: `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Definiuje kroki ze standardowym procesem kompilacji dla projektów języka Visual C#.<br /><br /> Zaimportowany przez Visual C# pliki projektu (.csproj), które obejmują następującą instrukcję: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Definiuje kroki w standardowym procesem kompilacji dla projektów języka Visual Basic.<br /><br /> Zaimportowanych przez pliki projektu języka Visual Basic (.vbproj), które obejmują następującą instrukcję: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>Zobacz też  
 [Import — Element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)


