---
title: "Fileclassifier — zadanie | Dokumentacja firmy Microsoft"
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
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 007a8332e741fe6c043b4444fcaf4447effdcd76
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="fileclassifier-task"></a>FileClassifier — Zadanie
<xref:Microsoft.Build.Tasks.Windows.FileClassifier> Zadań klasyfikuje zestaw zasobów źródła jako te, które zostaną osadzone w zestawie. Jeśli zasób nie jest Lokalizowalny, jest osadzony w zestawie aplikacji głównej; w przeciwnym razie jest osadzony w zestawie satelickim.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`CLREmbeddedResource`|Nieużywane.|  
|`CLRResourceFiles`|Nieużywane.|  
|`CLRSatelliteEmbeddedResource`|Nieużywane.|  
|`Culture`|Opcjonalne **ciąg** parametru.<br /><br /> Określa kulturę dla kompilacji. Ta wartość może być **null** Jeśli kompilacja jest niemożliwe do zlokalizowania. Jeśli **null**, wartością domyślną jest wartość małe **wartość CultureInfo.InvariantCulture** zwraca.|  
|`MainEmbeddedFiles`|Opcjonalne **[ITaskItem]** parametru wyjściowego.<br /><br /> Określa zasoby niemożliwe do zlokalizowania, które są osadzone w zestawie głównym.|  
|`OutputType`|Wymagane **ciąg** parametru.<br /><br /> Określa typ pliku do plików źródłowych określonej do osadzenia. Prawidłowe wartości to **exe**, **winexe**, lub **biblioteki**.|  
|`SatelliteEmbeddedFiles`|Opcjonalne **[ITaskItem]** parametru wyjściowego.<br /><br /> Określa Lokalizowalny pliki, które są osadzone w zestawu satelickiego dla kultury określonej przez **kultury** parametru.|  
|`SourceFiles`|Wymagane **[ITaskItem]** parametru.<br /><br /> Określa listę plików do klasyfikowania.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli **kultury** parametru nie jest ustawiona, wszystkie zasoby, które są określone za pomocą **SourceFiles** parametru są niemożliwe do zlokalizowania; w przeciwnym razie są one Lokalizowalny, chyba że są one powiązane z  **Lokalizowalny** atrybut, który ma ustawioną wartość **false**.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie klasyfikuje pliku jednego źródła jako zasób i osadza go w zestawie satelickim dla kultury French-Canadian (fr-CA).  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <ItemGroup>  
    <Resource Include="Resource1.bmp" />  
  </ItemGroup>  
  <Target Name="FileClassifierTask">  
    <FileClassifier  
      SourceFiles="Resource1.bmp"  
      Culture="fr-CA"  
      OutputType="exe" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)