---
title: "Przy użyciu aspnetcompiler — zadanie wstępnej kompilacji aplikacji programu ASP.NET | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
ms.openlocfilehash: b1528cd71c689876cd2c496e9cfdaaf0a97f0186
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler — Zadanie
`AspNetCompiler` Zadań opakowuje aspnet_compiler.exe, narzędzie do wstępnego kompilowania [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `AspNetCompiler` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AllowPartiallyTrustedCallers`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli ten parametr ma `true`,, zestawu o silnej nazwie umożliwi częściowo zaufanych wywołań.|  
|`Clean`|Opcjonalne `Boolean` parametru<br /><br /> Jeśli ten parametr ma `true`, wstępnie skompilowana aplikacja zostanie skompilowany oczyszczania. Wszystkie składniki skompilowane wcześniej zostaną ponownie skompilowane. Wartość domyślna to `false`. Ten parametr odpowiada **- c** Włącz aspnet_compiler.exe.|  
|`Debug`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli ten parametr ma `true`, informacje o debugowaniu (. Plik PDB) są emitowane podczas kompilacji. Wartość domyślna to `false`. Ten parametr odpowiada **-d** Włącz aspnet_compiler.exe.|  
|`DelaySign`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli ten parametr ma `true`, zestaw nie jest w pełni podpisany po utworzeniu.|  
|`FixedNames`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli ten parametr ma `true`, skompilowane zestawy będą mieć stałe nazwy.|  
|`Force`|Opcjonalne `Boolean` parametru<br /><br /> Jeśli ten parametr ma `true`, zadania spowoduje zastąpienie katalog docelowy, jeśli już istnieje. Istniejąca zawartość zostanie utracona. Wartość domyślna to `false`. Ten parametr odpowiada **-f** Włącz aspnet_compiler.exe.|  
|`KeyContainer`|Opcjonalne `String` parametru.<br /><br /> Określa kontener klucza o silnej nazwie.|  
|`KeyFile`|Opcjonalne `String` parametru.<br /><br /> Określa ścieżkę fizyczną do pliku klucza silnej nazwy.|  
|`MetabasePath`|Opcjonalne `String` parametru.<br /><br /> Określa pełną ścieżkę metabazy usług IIS aplikacji. Tego parametru nie można połączyć z `VirtualPath` lub `PhysicalPath` parametrów. Ten parametr odpowiada **-m** Włącz aspnet_compiler.exe.|  
|`PhysicalPath`|Opcjonalne `String` parametru.<br /><br /> Określa ścieżkę fizyczną aplikacji do skompilowania. W przypadku braku tego parametru metabazy usług IIS jest używana do lokalizowania aplikacji. Ten parametr odpowiada **-p** Włącz aspnet_compiler.exe.|  
|`TargetFrameworkMoniker`|Opcjonalne `String` parametru.<br /><br /> Określa TargetFrameworkMoniker wskazujący, która wersja .NET Framework aspnet_compiler.exe należy używać. Akceptuje tylko monikerów .NET Framework.|  
|`TargetPath`|Opcjonalne `String` parametru.<br /><br /> Określa ścieżkę fizyczną, do której jest kompilowana aplikacja. Jeśli nie zostanie określony, aplikacja jest wstępnie skompilowaną w miejscu.|  
|`Updateable`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli ten parametr ma `true`, wstępnie skompilowana aplikacja będzie można aktualizować.  Wartość domyślna to `false`. Ten parametr odpowiada **-u** Włącz aspnet_compiler.exe.|  
|`VirtualPath`|Opcjonalne `String` parametru.<br /><br /> Ścieżka wirtualna aplikacji, która ma być kompilowana. Jeśli `PhysicalPath` określony, ścieżka fizyczna jest używana do lokalizowania aplikacji. W przeciwnym razie zostanie użyta metabaza usług IIS i aplikacji zakłada, że w domyślnej witrynie. Ten parametr odpowiada **- v** Włącz aspnet_compiler.exe.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.ToolTaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [tooltaskextension — klasa podstawowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `AspNetCompiler` zadań wstępnej kompilacji [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
