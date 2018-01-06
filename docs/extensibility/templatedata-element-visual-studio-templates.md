---
title: "TemplateData — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords: TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 85dba252eedaeafbffdc58eadac91386ff6cac98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData — Element (szablony Visual Studio)
Kategoryzuje szablonu i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.  
  
 \<VSTemplate >  
 \<TemplateData >  
  
## <a name="syntax"></a>Składnia  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Nazwa](../extensibility/name-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa nazwę szablonu, pojawiającą się w jednej **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
|[Opis](../extensibility/description-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa opis szablonu, pojawiającą się w jednej **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
|[Ikona](../extensibility/icon-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa ścieżkę i nazwę pliku obrazu, który służy jako ikonę, która jest wyświetlana w jednym **nowy projekt** lub **Dodaj nowy element** okno dialogowe szablonu.|  
|[Typ projektu](../extensibility/projecttype-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablon projektu, aby był on wyświetlany w obszarze określonej grupy w **nowy projekt** okno dialogowe.|  
|[Projectsubtype —](../extensibility/projectsubtype-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Klasyfikuje szablon projektu, aby był on wyświetlany w obszarze określonej podkategorii w **nowy projekt** okno dialogowe.|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa identyfikator szablonu.|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa identyfikator szablonu grupy.|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa wartość, która służy do rozmieszczania szablonu, między innymi szablony w tej samej kategorii, pojawiającą się w jednej **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
|[Createnewfolder —](../extensibility/createnewfolder-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa, czy tworzony jest folder zawierający przy tworzeniu wystąpienia projektu.|  
|[Defaultname —](../extensibility/defaultname-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa nazwę, która spowoduje wygenerowanie system projektu programu Visual Studio dla projektów lub elementów, podczas jego tworzenia.|  
|[Providedefaultname —](../extensibility/providedefaultname-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa, czy system projektu programu Visual Studio wygeneruje domyślną nazwę dla projektu lub elementu podczas jego tworzenia.|  
|[Promptforsaveoncreation —](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa, czy można utworzyć projektu jako projektu tymczasowego.|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa, czy **Przeglądaj** przycisk jest dostępny w **nowy projekt** okna dialogowego, dzięki czemu użytkownicy mogą łatwo modyfikować domyślny katalog, w której jest zapisywany nowy projekt.|  
|[Ukryte](../extensibility/hidden-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa, czy szablon jest wyświetlany w jednym **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa liczbę kategorii nadrzędnych, zawierające szablonu w **nowy projekt** okno dialogowe.|  
|[Locationfieldmruprefix —](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|Element opcjonalny.|  
|[Locationfield —](../extensibility/locationfield-element-visual-studio-project-templates.md)|Element opcjonalny.<br /><br /> Określa, czy **lokalizacji** polu tekstowym **nowy projekt** okno dialogowe jest włączona, wyłączona albo ukryte szablonu projektu.|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Użyj tego elementu, jeśli szablon obsługuje tylko określonych minimalnej wersji i nowszymi wersjami, jeśli występują programu .NET Framework.|  
|[Supportsmasterpage —](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa, czy szablon obsługuje stronę wzorcową dla projektów sieci web.|  
|[Supportscodeseparation —](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa, czy szablon obsługuje separację kodu lub modelu strony związane z kodem, dla projektów sieci web.|  
|[Supportslanguagedropdown —](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa, czy szablon jest identyczny dla wielu języków oraz czy **języka** opcja jest dostępna z **nowy projekt** okno dialogowe.|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa platformę, które obiekty docelowe szablonu projektu. Ten element określa, że szablon projektu jest używany do tworzenia [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Zawiera wszystkie metadane szablonu projektu, szablon elementu lub startowy.|  
  
## <a name="remarks"></a>Uwagi  
 `TemplateData`jest wymagany element.  
  
 Jeśli opcjonalny element nie zostanie uwzględniony, zostanie użyta domyślna wartość dla tego elementu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metadane szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)