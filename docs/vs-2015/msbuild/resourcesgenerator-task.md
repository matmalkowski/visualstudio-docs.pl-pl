---
title: Resourcesgenerator — zadanie | Dokumentacja firmy Microsoft
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
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63ee00754683156dad2bd34a93ff43f820eb37c7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42629816"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [resourcesgenerator — zadanie](https://docs.microsoft.com/visualstudio/msbuild/resourcesgenerator-task).  
  
  
<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> Zadań osadza co najmniej jeden zasób (.ico jpg, bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] w formacie binarnym, a inne typy rozszerzeń) do pliku Resources.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`OutputPath`|Wymagane **ciąg** parametru.<br /><br /> Określa ścieżkę do katalogu wyjściowego. Jeśli ścieżka nie jest ścieżką bezwzględną, jest ona traktowana jako ścieżkę, która jest określana względem katalogu głównego projektu.|  
|`OutputResourcesFile`|Wymagane **[] ITaskItem** parametr wyjściowy.<br /><br /> Określa ścieżkę i nazwę pliku wygenerowanego Resources. Jeśli ścieżka nie jest ścieżką bezwzględną, plik .resources jest generowany względem katalogu głównego projektu.|  
|`ResourcesFiles`|Wymagane **[] ITaskItem** parametru.<br /><br /> Określa co najmniej jeden zasób do osadzenia w pliku .resources wygenerowany.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje plik Resources o .bmp pojedynczy zasób. Zasób .bmp jest generowany w katalogu, który jest określana względem katalogu głównego projektu.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="ResourcesGeneratorTask">  
    <ResourcesGenerator  
      ResourceFiles="Resource1.bmp"  
      OutputPath="myresources"  
      OutputResourcesFile="myresources\my.resources" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Kompilowanie aplikacji WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)



