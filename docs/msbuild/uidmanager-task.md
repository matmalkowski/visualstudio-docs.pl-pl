---
title: "Uidmanager — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 806e924738b7ce01eb13bbbb357bf4013ad01d33
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="uidmanager-task"></a>UidManager — Zadanie
<xref:Microsoft.Build.Tasks.Windows.UidManager> Zadanie sprawdza, aktualizuje lub usuwa unikatowe identyfikatory (UID), aby zlokalizować wszystkie [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] elementów zawartych w źródle [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`IntermediateDirectory`|Opcjonalne **ciąg** parametru.<br /><br /> Określa katalog, który służy do tworzenia kopii zapasowych źródła [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki, które są określone przez **MarkupFiles** parametru.|  
|`MarkupFiles`|Wymagane **[ITaskItem]** parametru.<br /><br /> Określa źródło [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki, aby objąć UID sprawdzania, aktualizowanie lub usuwanie.|  
|`Task`|Wymagane **ciąg** parametru.<br /><br /> Określa identyfikator UID zadanie zarządzania, które chcesz wykonać. Prawidłowe opcje to **Sprawdź**, **aktualizacji**, lub **Usuń**.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:Microsoft.Build.Tasks.Windows.UidManager> zadań, aby sprawdzić, czy określone źródło [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki zawierają [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] elementów, które mają odpowiednie UID.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UidManagerTask">  
    <UidManager  
      Task="Check"  
      MarkupFiles="Page1.xaml;Page2.xaml"  
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Porady: lokalizowanie aplikacji](/dotnet/framework/wpf/advanced/how-to-localize-an-application)