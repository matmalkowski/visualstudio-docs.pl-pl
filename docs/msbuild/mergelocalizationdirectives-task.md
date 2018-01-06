---
title: "Mergelocalizationdirectives — zadanie | Dokumentacja firmy Microsoft"
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
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7f67c122a879df51708852925a63008cfb190318
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives — Zadanie
<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> Zadań łączy atrybuty lokalizacji i komentarze co najmniej jednego [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików binarnych w jednym pliku dla całego zestawu.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Wymagane **[ITaskItem]** parametru.<br /><br /> Określa listę plików dyrektywy lokalizacji dla poszczególnych plików w [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] format binarny.|  
|`OutputFile`|Wymagane **ciąg** parametru wyjściowego.<br /><br /> Ścieżka danych wyjściowych zestawu skompilowanego dyrektywy lokalizacji.|  
  
## <a name="remarks"></a>Uwagi  
 Można dodawać atrybuty lokalizacji i komentarze do [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] zawartości. Z [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] lokalizacja pomocy technicznej, można usunąć atrybuty lokalizacji i komentarze i umieść je w pliku .loc, który różni się od wygenerowanym zestawie. Można to zrobić za pomocą **LocalizationPropertyStorage** atrybutu. Aby uzyskać więcej informacji o lokalizacji atrybutów i komentarze i **LocalizationPropertyStorage**, zobacz [atrybuty lokalizacji i komentarze](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład scala lokalizacja kilku [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików binarnych w .loc pojedynczy plik.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)