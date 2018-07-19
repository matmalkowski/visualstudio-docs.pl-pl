---
title: Program MSBuild. Jest przeznaczony dla plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/24/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 835d6e80c650a18b3e595d1c6dc0c8bafd6b958a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080015"
---
# <a name="msbuild-targets-files"></a>MSBuild — pliki .targets
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zawiera kilka *.targets* pliki, które zawierają elementy, właściwości, cele i zadania dla typowych scenariuszy. Te pliki są automatycznie importowane do większości [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pliki w celu uproszczenia konserwacji i czytelności projektu.  

 Projekty zazwyczaj importują jeden lub więcej *.targets* pliki, aby zdefiniować ich proces kompilacji. Na przykład [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projekt utworzony w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zaimportuje *Microsoft.CSharp.targets* które importuje *Microsoft.Common.targets*. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Sam projekt Definiowanie elementów i właściwości określonych do tego projektu, ale standard tworzenia reguł dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu są zdefiniowane w zaimportowanych *.targets* plików.  

 `$(MSBuildToolsPath)` Określa ścieżkę dla tych wspólnych *.targets* plików. Jeśli `ToolsVersion` 4.0, pliki znajdują się w następującej lokalizacji:  *\<WindowsInstallationPath > \Microsoft.NET\Framework\v4.0.30319\\*  

> [!NOTE]
>  Aby uzyskać informacje o sposobie tworzenia własnych elementów docelowych, zobacz [cele](../msbuild/msbuild-targets.md). Aby uzyskać informacje o sposobie używania `Import` element, aby wstawić plik projektu do innego pliku projektu, zobacz [Import — element (MSBuild)](../msbuild/import-element-msbuild.md) i [porady: użycie tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  

## <a name="common-targets-files"></a>Wspólne pliki .targets  

|*.TARGETS* pliku|Opis|  
|-------------------|-----------------|  
|*Microsoft.Common.targets*|Definiuje kroki w standardowym procesem kompilacji dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektów.<br /><br /> Zaimportowany przez *Microsoft.CSharp.targets* i *Microsoft.VisualBasic.targets* pliki zawierające następującą instrukcję: `<Import Project="Microsoft.Common.targets" />`|  
|*Microsoft.CSharp.targets*|Definiuje kroki ze standardowym procesem kompilacji dla projektów języka Visual C#.<br /><br /> Zaimportowanych przez pliki projektu Visual C# (*.csproj*), który obejmuje następującą instrukcję: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|*Microsoft.VisualBasic.targets*|Definiuje kroki w standardowym procesem kompilacji dla projektów języka Visual Basic.<br /><br /> Zaimportowanych przez pliki projektu w języku Visual Basic (*.vbproj*), który obejmuje następującą instrukcję: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|

## <a name="directorybuildtargets"></a>Directory.Build.targets
*Directory.Build.targets* jest plikiem zdefiniowanych przez użytkownika zawiera dostosowania do projektów w katalogu. Ten plik jest automatycznie importowany z *Microsoft.Common.targets* chyba że właściwość **ImportDirectoryBuildTargets** ustawiono **false**.

## <a name="see-also"></a>Zobacz także  
 [Import — element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
