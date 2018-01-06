---
title: "Przy użyciu programu MSBuild | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3b9d05b85cacfcdf90a883ffd08d4dec316eaafc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-msbuild"></a>Przy użyciu programu MSBuild
MSBuild dostarcza dobrze zdefiniowany, rozszerzony format XML do tworzenia plików projektu, w pełni opisujące elementy projektu można utworzyć zadania kompilacji i konfiguracje kompilacji.  
  
## <a name="general-msbuild-considerations"></a>Zagadnienia ogólne MSBuild  
 Pliki projektu programu MSBuild, na przykład [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] pliki vbproj zawierają dane, które jest używane w czasie kompilacji, ale także zawierać dane, które jest używane w czasie projektowania. Dane dotyczące czasu kompilacji jest przechowywany przy użyciu programu MSBuild w nim elementów podstawowych, w tym [Item — Element (MSBuild)](../../msbuild/item-element-msbuild.md) i [Property — Element (MSBuild)](../../msbuild/property-element-msbuild.md). Danych czasu projektowania, czyli danych specyficznych dla typu projektu i żadnych podtypów powiązany projekt jest przechowywany w dowolnych XML zarezerwowano dla niej.  
  
 MSBuild nie jest obsługiwany dla obiekt konfiguracji, ale zawiera atrybuty warunkowe dla określenia dane specyficzne dla konfiguracji. Na przykład:  
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Aby uzyskać więcej informacji na atrybuty warunkowe, zobacz [konstrukcje warunkowe](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Rozszerzanie MSBuild dla danego typu projektu  
 Interfejsów API i interfejsów MSBuild mogą ulec zmianie w przyszłych wersjach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W związku z tym rozsądne jest używać klas framework (MPF) zarządzanego pakietu, ponieważ udostępniają one osłony ze zmian.  
  
 Framework pakietu zarządzania dla projektów (MPFProj) udostępnia klasy pomocy dotyczące tworzenia i zarządzania nowy system projektu. Instrukcje można znaleźć źródła kodu i kompilacji w [MPF projektów — Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Klasy specyficzne dla projektu MPF są następujące:  
  
|Class|Implementacja|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement`Klasa jest otoki dla elementów MSBuild.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Vs generatory pojedynczego pliku. Zadania programu MSBuild  
 Pojedynczy plik generatory są dostępne tylko w czasie projektowania, ale zadania programu MSBuild, może być używany w czasie projektowania i czas kompilacji. Maksymalna elastyczność w związku z tym umożliwia zadania programu MSBuild transformacji i generowania kodu. Aby uzyskać więcej informacji, zobacz [niestandardowego narzędzia](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do MSBuild](../../msbuild/msbuild-reference.md)   
 [MSBuild](../../msbuild/msbuild.md)   
 [Narzędzia niestandardowe](../../extensibility/internals/custom-tools.md)