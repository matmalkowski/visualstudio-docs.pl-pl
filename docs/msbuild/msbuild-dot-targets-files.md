---
title: "MSBuild. Celem plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/24/2017
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
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: "17"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 0811a2f32ae9834c1141265a936e67c6a04adbcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-targets-files"></a>MSBuild — Pliki .Targets
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]obejmuje kilka pliki .targets, zawierające elementy, właściwości, cele i zadania dla typowych scenariuszy. Te pliki są automatycznie importowane do większości [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pliki, aby uprościć konserwację i czytelność projektu.  

 Projekty zwykle zaimportować co najmniej jeden plik .targets do definiowania procesu kompilacji. Na przykład [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu utworzonych przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zaimportuje Microsoft.CSharp.targets importującego Microsoft.Common.targets. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Projektu zostaną zdefiniowane elementy i właściwości specyficzne do tego projektu, ale reguły dla kompilacji standardowego [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu są zdefiniowane w plikach TARGETS zaimportowany.  

 `$(MSBuildToolsPath)` Określa ścieżkę te wspólne pliki .targets. Jeśli `ToolsVersion` 4.0, pliki znajdują się w następującej lokalizacji:`WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  

> [!NOTE]
>  Aby uzyskać informacje o sposobie tworzenia własnych elementów docelowych, zobacz [cele](../msbuild/msbuild-targets.md). Aby uzyskać informacje o sposobie używania `Import` elementu, aby wstawić plik projektu do innego pliku projektu, zobacz [Import — Element (MSBuild)](../msbuild/import-element-msbuild.md) i [porady: Użyj tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  

## <a name="common-targets-files"></a>Typowe. Pliki obiektów docelowych  

|. Plik elementów docelowych|Opis|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Definiuje kroki procesu kompilacji standardowe [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów.<br /><br /> Zaimportowane pliki Microsoft.CSharp.targets i Microsoft.VisualBasic.targets, które obejmują następująca instrukcja:`<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Definiuje kroki w procesie standardowe kompilacji w projektach Visual C#.<br /><br /> Zaimportowane przez Visual C# pliki projektu (csproj), które obejmują następująca instrukcja:`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Definiuje kroki w procesie kompilacji standardowe dla projektów języka Visual Basic.<br /><br /> Zaimportowane przez pliki projektu Visual Basic (.vbproj), które obejmują następująca instrukcja:`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|

## <a name="directorybuildtargets"></a>Directory.Build.targets
Directory.Build.targets jest zdefiniowane przez użytkownika pliku, który zawiera dostosowania do projektów w katalogu. Ten plik jest automatycznie importowany z Microsoft.Common.targets, chyba że właściwość **ImportDirectoryBuildTargets** ustawiono **false**.

## <a name="see-also"></a>Zobacz też  
 [Import — Element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
