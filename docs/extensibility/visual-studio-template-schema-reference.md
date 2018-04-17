---
title: Odwołanie do schematu szablonu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- VSTEMPLATE files
- Visual Studio templates, schema
- .vstemplate files
ms.assetid: 6f74a2d5-3811-43d6-8b10-eb5823ad8995
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08e0758638bbb73cb999fb6b8aba2f195b603b42
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-template-schema-reference"></a>Odwołanie do schematu szablonu Visual Studio
Ten rozdział zawiera informacje o elementach języka XML w plikach .vstemplate. Pliki te zawierają metadane szablonów projektów, szablonów elementów i zestawów początkowych.  
  
 Pliki vstemplate.xsd mogą służyć do sprawdzania poprawności niestandardowych plików .vstemplate. Ten plik znajduje się w temacie. \\ *Folder instalacji programu visual Studio*\Xml\Schemas\1033\vstemplate.xsd.  
  
|Element|Elementy podrzędne|Atrybuty|  
|-------------|--------------------|----------------|  
|[Element appliesTo](../extensibility/appliesto-element-visual-studio-templates.md)|Brak|Brak|  
|[Zestaw (szablonu)](../extensibility/assembly-element-visual-studio-templates.md)|--|--|  
|[Zestaw (rozszerzenie kreatora)](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|--|--|  
|[BuildProjectOnload](../extensibility/buildprojectonload-element-visual-studio-templates.md)|--|--|  
|[CreateInPlace](../extensibility/createinplace-visual-studio-templates.md)|--|--|  
|[Createnewfolder —](../extensibility/createnewfolder-element-visual-studio-templates.md)|--|--|  
|[Customdatasignature —](../extensibility/customdatasignature-element-visual-studio-templates.md)|--|--|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|--|Nazwa<br /><br /> Wartość|  
|[Customparameters —](../extensibility/customparameters-element-visual-studio-templates.md)|CustomParameter|--|  
|[Defaultname —](../extensibility/defaultname-element-visual-studio-templates.md)|--|--|  
|[Opis](../extensibility/description-element-visual-studio-templates.md)|--|Package<br /><br /> ID|  
|[EnableEditOfLocationField](../extensibility/enableeditoflocationfield-element-visual-studio-templates.md)|--|--|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|--|--|  
|[Folder](../extensibility/folder-element-visual-studio-project-templates.md)|ProjectItem<br /><br /> Folder|Nazwa|  
||[przestarzały]|--|  
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|--|--|  
|[Ukryte](../extensibility/hidden-element-visual-studio-templates.md)|--|--|  
|[Ikona](../extensibility/icon-element-visual-studio-templates.md)|--|Package<br /><br /> ID|  
|[Locationfield —](../extensibility/locationfield-element-visual-studio-project-templates.md)|--|--|  
|[Locationfieldmruprefix —](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|--|--|  
|[Maxframeworkversion —](../extensibility/maxframeworkversion-element-visual-studio-templates.md)|--|--|  
|[Nazwa](../extensibility/name-element-visual-studio-templates.md)|--|Package<br /><br /> ID|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|--|--|  
|[Previewimage —](../extensibility/previewimage-element-visual-studio-templates.md)|--|--|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Folder<br /><br /> ProjectItem|Plik<br /><br /> TargetFileName<br /><br /> ReplaceParameters|  
|[Projectcollection —](../extensibility/projectcollection-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|--|  
|[ProjectItem (szablony elementów)](../extensibility/projectitem-element-visual-studio-item-templates.md)|--|SubType<br /><br /> CustomTool<br /><br /> ItemType<br /><br /> ReplaceParameters<br /><br /> TargetFileName|  
|[ProjectItem (szablony projektów)](../extensibility/projectitem-element-visual-studio-project-templates.md)|--|TargetFileName<br /><br /> ReplaceParameters<br /><br /> OpenInEditor<br /><br /> OpenOrder<br /><br /> OpenInWebBrowser<br /><br /> OpenInHelpBrowser|  
|[Projectsubtype —](../extensibility/projectsubtype-element-visual-studio-templates.md)|--|--|  
|[Projecttemplatelink —](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|--|ProjectName|  
|[Typ projektu](../extensibility/projecttype-element-visual-studio-templates.md)|--|--|  
|[Promptforsaveoncreation —](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|--|--|  
|[Providedefaultname —](../extensibility/providedefaultname-element-visual-studio-templates.md)|--|--|  
|[Dokumentacja](../extensibility/reference-element-visual-studio-templates.md)|Zestaw|--|  
|[Odwołania](../extensibility/references-element-visual-studio-templates.md)|Tematy pomocy|--|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|--|--|  
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|--|Wersja|  
|[SDKReference](../extensibility/sdkreference-element-visual-studio-templates.md)|--|Package|  
|[ShowByDefault](../extensibility/showbydefault-visual-studio-templates.md)|--|--|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|Nazwa|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|--|--|  
|[Supportscodeseparation —](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|--|--|  
|[Supportslanguagedropdown —](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|--|--|  
|[Supportsmasterpage —](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|--|--|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|RequiredPlatformVersion|--|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|ProjectCollection<br /><br /> Projekt<br /><br /> Odwołania<br /><br /> ProjectItem<br /><br /> CustomParameters|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Nazwa<br /><br /> Opis<br /><br /> Ikona<br /><br /> PreviewImage<br /><br /> ProjectType<br /><br /> ProjectSubType<br /><br /> TemplateID<br /><br /> TemplateGroupID<br /><br /> SortOrder<br /><br /> CreateNewFolder<br /><br /> DefaultName<br /><br /> ProvideDefaultName<br /><br /> PromptForSaveOnCreation<br /><br /> EnableLocationBrowseButton<br /><br /> EnableEditOfLocationField<br /><br /> Hidden<br /><br /> DisplayInParentCategories<br /><br /> LocationFieldMRUPrefix<br /><br /> NumberOfParentCategoriesToRollUp<br /><br /> CreateInPlace<br /><br /> BuildOnLoad<br /><br /> BuildProjectOnload<br /><br /> ShowByDefault<br /><br /> LocationField<br /><br /> SupportsMasterPage<br /><br /> SupportsCodeSeparation<br /><br /> SupportsLanguageDropDown<br /><br /> RequiredFrameworkVersion<br /><br /> FrameworkVersion<br /><br /> MaxFrameworkVersion<br /><br /> CustomDataSignature<br /><br /> TargetPlatformName|--|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|--|--|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|--|--|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|TemplateData<br /><br /> TemplateContent<br /><br /> WizardExtension<br /><br /> WizardData|Typ<br /><br /> Wersja|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|--|Nazwa|  
|[Wizardextension —](../extensibility/wizardextension-element-visual-studio-templates.md)|Zestaw<br /><br /> FullClassName|--|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Instrukcje: Tworzenie pakietów startowych](../ide/how-to-create-starter-kits.md)