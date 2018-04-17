---
title: Rozszerzanie modelu obiektu podstawowego projektu | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9cffbecf585f6f8be4174531a91e466f65ab9a72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-object-model-of-the-base-project"></a>Rozszerzanie modelu obiektu podstawowego projektu

Podtyp projektu może rozszerzyć modelu obiektu automatyzacji podstawowego projektu w następujących miejscach:

-   Project.Extender ("\<ProjectSubtypeName >") — umożliwia to podtypu projektu do zaoferowania obiektu za pomocą metod niestandardowego z <xref:EnvDTE.Project>. Podtyp projektu można użyć rozszerzeń automatyzacji do udostępnienia `Project` obiektu. <xref:EnvDTE80.IInternalExtenderProvider> Interfejsu zaimplementowanego w agregatorze podtypu projektu powinno oferować jego obiektu dla `VSHPROPID_ExtObjectCATID` z <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (odpowiadający `itemid` wartość [VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID.

-   ProjectItem.Extender ("\<ProjectSubtypeName >") — umożliwia to podtypu projektu do zaoferowania obiektu za pomocą metod niestandardowego z określonego <xref:EnvDTE.ProjectItem> obiektu w projekcie. Podtyp projektu można użyć rozszerzeń automatyzacji do udostępnienia tego obiektu. <xref:EnvDTE80.IInternalExtenderProvider> Interfejsu zaimplementowanego w agregatorze podtypu projektu musi oferować jego obiektu dla `VSHPROPID_ExtObjectCATID` z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (odpowiadający do żądanej <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Project.Properties - tej kolekcji opisuje właściwości niezależny od konfiguracji `Project` obiektu. Aby uzyskać więcej informacji na temat właściwości projektu, zobacz <xref:EnvDTE.Project.Properties%2A>. Podtyp projektu umożliwia dodawanie właściwości do tej kolekcji rozszerzeń automatyzacji. <xref:EnvDTE80.IInternalExtenderProvider> Interfejsu zaimplementowanego w agregatorze podtypu projektu musi oferować jego obiektu dla `VSHPROPID_BrowseObjectCATID` z VSHPROPID2 (odpowiadający `itemid` wartość [VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>), z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.

-   Configuration.Properties - tej kolekcji opisuje właściwości zależne od konfiguracji projektu dla określonej konfiguracji (na przykład debugowania). Aby uzyskać więcej informacji, zobacz <xref:EnvDTE.Configuration>. Podtyp projektu umożliwia dodawanie właściwości do tej kolekcji rozszerzeń automatyzacji. <xref:EnvDTE80.IInternalExtenderProvider> Interfejsu zaimplementowanego w agregatorze podtypu projektu udostępnia własnego obiektu CATID `VSHPROPID_CfgBrowseObjectCATID` (odpowiadający `itemid` wartość [VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Interfejs jest używany do odróżnienia jednego obiektu przeglądania konfiguracji z innej.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>