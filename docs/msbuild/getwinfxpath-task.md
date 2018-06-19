---
title: Getwinfxpath — zadanie | Dokumentacja firmy Microsoft
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
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e02d0f93dd406df170de2d4e83023fedced7d932
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31573447"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath — Zadanie
<xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> Zadań zwraca katalogu bieżącego [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] środowiska wykonawczego.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`WinFXPath`|Opcjonalne **ciąg** parametru wyjściowego.<br /><br /> Określa ścieżkę rzeczywistych [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)] środowiska wykonawczego.|  
|`WinFXNativePath`|Wymagane **ciąg** parametru.<br /><br /> Określa ścieżkę do natywnego [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] środowiska wykonawczego.|  
|`WinFXWowPath`|Wymagane **ciąg** parametru.<br /><br /> Określa ścieżkę do [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] zestawów w 32-bitowych **systemu Windows w systemie Windows** modułu w systemach 64-bitowych.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> zadanie jest wykonywane na 64-bitowy procesor, **WinFXPath** ustawiona jest ścieżką, która jest przechowywana w **WinFXWowPath** parametru; w przeciwnym razie **WinFXPath**  ustawiona jest ścieżką, która jest przechowywana w **WinFXNativePath** parametru.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **getwinfxpath —** zadanie, aby wykryć ścieżką natywną do [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] środowiska wykonawczego.  
  
```xml  
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
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)