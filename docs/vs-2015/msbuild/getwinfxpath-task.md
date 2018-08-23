---
title: Getwinfxpath — zadanie | Dokumentacja firmy Microsoft
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
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21aa8cd81465917c33709b751ba2e206e7d7484d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676675"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [getwinfxpath — zadanie](https://docs.microsoft.com/visualstudio/msbuild/getwinfxpath-task).  
  
  
<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> Zadanie zwraca katalogu bieżącego [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] środowiska uruchomieniowego.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`WinFXPath`|Opcjonalnie **ciąg** parametr wyjściowy.<br /><br /> Określa ścieżkę rzeczywistych [!INCLUDE[TLA2#tla_winfx](../includes/tla2sharptla-winfx-md.md)] środowiska uruchomieniowego.|  
|`WinFXNativePath`|Wymagane **ciąg** parametru.<br /><br /> Określa ścieżkę do natywnych [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)] środowiska uruchomieniowego.|  
|`WinFXWowPath`|Wymagane **ciąg** parametru.<br /><br /> Określa ścieżkę do [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] zestawów w 32-bitowych **Windows na Windows** modułu w systemach 64-bitowych.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> zadanie jest wykonywane na 64-bitowy procesor, **WinFXPath** parametr ma wartość ścieżki, która jest przechowywana w **WinFXWowPath** parametru; w przeciwnym razie **WinFXPath**  parametr ma wartość ścieżki, która jest przechowywana w **WinFXNativePath** parametru.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać **getwinfxpath —** zadanie, aby wykryć ścieżką natywną do [!INCLUDE[TLA2#tla_titlewinfx](../includes/tla2sharptla-titlewinfx-md.md)] środowiska uruchomieniowego.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Kompilowanie aplikacji WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)



