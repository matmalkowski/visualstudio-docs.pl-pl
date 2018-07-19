---
title: Mergelocalizationdirectives — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 78cf1405cf3a09d43aab21c53e64644db29af0de
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077704"
---
# <a name="mergelocalizationdirectives-task"></a>Mergelocalizationdirectives — zadanie
<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> Zadań scala atrybuty lokalizacji i komentarze, co najmniej jednego [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików binarnych w jeden plik dla całego zestawu.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Wymagane **[] ITaskItem** parametru.<br /><br /> Określa listę plików dyrektywy lokalizacji dla poszczególnych plików w [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] format binarny.|  
|`OutputFile`|Wymagane **ciąg** parametr wyjściowy.<br /><br /> Określa ścieżkę wyjściową zestawu skompilowanego dyrektywy lokalizacji.|  
  
## <a name="remarks"></a>Uwagi  
 Możesz dodać atrybuty lokalizacji i komentarze, aby [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] zawartości. Za pomocą [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] obsługi lokalizacji, możesz usunąć atrybuty lokalizacji i komentarze i umieść je w *.loc* pliku, który jest oddzielony od wygenerowanego zestawu. Można to zrobić za pomocą **LocalizationPropertyStorage** atrybutu. Aby uzyskać więcej informacji na temat atrybuty lokalizacji i komentarze a **LocalizationPropertyStorage**, zobacz [lokalizacja atrybutów i komentarzy](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład scala lokalizacji kilku [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików binarnych w jedną *.loc* pliku.  
  
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
  
## <a name="see-also"></a>Zobacz także  
[Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)  
[Odwołanie do zadania WPF MSBuild](../msbuild/wpf-msbuild-task-reference.md)  
[Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)  
[Odwołanie do zadania MSBuild](../msbuild/msbuild-task-reference.md)  
[Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
