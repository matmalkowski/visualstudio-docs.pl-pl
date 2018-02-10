---
title: "LC — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bf308bb5693363406bb954cdb63ab5fd25772cb9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="lc-task"></a>LC — Zadanie
LC.exe zawija generuje plik .license z .licx — plik. Aby uzyskać więcej informacji o LC.exe, zobacz [Lc.exe (kompilator licencji)](/dotnet/framework/tools/lc-exe-license-compiler).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametrów dla `LC` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`LicenseTarget`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa, dla których są generowane pliki .licenses — plik wykonywalny.|  
|`NoLogo`|Opcjonalne `Boolean` parametru.<br /><br /> Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|`OutputDirectory`|Opcjonalne `String` parametru.<br /><br /> Określa katalog, w którym można umieścić pliki wyjściowe .licenses —.|  
|`OutputLicense`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru wyjściowego.<br /><br /> Określa nazwę .licenses — plik. Jeśli nazwa nie zostanie określona, zostanie użyta nazwa .licx — plik i .licenses — plik znajduje się w katalogu, który zawiera .licx — plik.|  
|`ReferencedAssemblies`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa składniki do którego istnieje odwołanie do załadowania podczas generowania pliku .license.|  
|`SdkToolsPath`|Opcjonalne `String` parametru.<br /><br /> Określa ścieżkę do narzędzia zestawu SDK, takich jak resgen.exe.|  
|`Sources`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa elementy, które zawierają licencjonowane składniki do uwzględnienia w .licenses — plik. Aby uzyskać więcej informacji, zobacz dokumentację `/complist` przełącznika w [Lc.exe (kompilator licencji)](/dotnet/framework/tools/lc-exe-license-compiler).|  
  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.ToolTaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [tooltaskextension — klasa podstawowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `LC` zadań do kompilacji licencji.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)