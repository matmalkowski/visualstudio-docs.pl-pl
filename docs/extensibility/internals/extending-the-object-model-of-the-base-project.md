---
title: Rozszerzanie modelu obiektu podstawowego projektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b92fe7fece58dd2006507f0285d3c440af437ee4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-object-model-of-the-base-project"></a>Rozszerzanie modelu obiektu podstawowego projektu
Podtyp projektu może rozszerzyć modelu obiektu automatyzacji podstawowego projektu w następujących miejscach:  
  
-   Project.Extender ("\<ProjectSubtypeName >") — umożliwia to podtypu projektu do zaoferowania obiektu za pomocą metod niestandardowego z <xref:EnvDTE.Project>. Podtyp projektu można użyć rozszerzeń automatyzacji do udostępnienia `Project` obiektu. <xref:EnvDTE80.IInternalExtenderProvider>Interfejsu zaimplementowanego w agregatorze podtypu projektu powinno oferować jego obiektu dla `VSHPROPID_ExtObjectCATID` z <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (odpowiadający `itemid` wartość VSITEMID_ROOT, z `VSITEMID`) CATID.  
  
-   ProjectItem.Extender ("\<ProjectSubtypeName >") — umożliwia to podtypu projektu do zaoferowania obiektu za pomocą metod niestandardowego z określonego <xref:EnvDTE.ProjectItem> obiektu w projekcie. Podtyp projektu można użyć rozszerzeń automatyzacji do udostępnienia tego obiektu. <xref:EnvDTE80.IInternalExtenderProvider> Interfejsu zaimplementowanego w agregatorze podtypu projektu musi oferować jego obiektu dla `VSHPROPID_ExtObjectCATID` z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpowiadający do żądanej `VSITEMID`) CATID.  
  
-   Project.Properties - tej kolekcji opisuje konfiguracji niezależnie od właściwości `Project` obiektu. Aby uzyskać więcej informacji na temat właściwości projektu, zobacz <xref:EnvDTE.Project.Properties%2A>. Podtyp projektu umożliwia dodawanie właściwości do tej kolekcji rozszerzeń automatyzacji. <xref:EnvDTE80.IInternalExtenderProvider> Interfejsu zaimplementowanego w agregatorze podtypu projektu musi oferować jego obiektu dla `VSHPROPID_BrowseObjectCATID` z VSHPROPID2 (odpowiadający `itemid` wartość VSITEMID_ROOT, z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
-   Configuration.Properties - tej kolekcji przedstawia zależne właściwości konfiguracji projektu dla określonej konfiguracji (na przykład debugowania). Aby uzyskać więcej informacji, zobacz <xref:EnvDTE.Configuration>. Podtyp projektu umożliwia dodawanie właściwości do tej kolekcji rozszerzeń automatyzacji. <xref:EnvDTE80.IInternalExtenderProvider> Interfejsu zaimplementowanego w agregatorze podtypu projektu udostępnia własnego obiektu CATID `VSHPROPID_CfgBrowseObjectCATID` (odpowiadający `itemid` wartość <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Interfejs jest używany do odróżnienia jednego obiektu przeglądania konfiguracji z innej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>