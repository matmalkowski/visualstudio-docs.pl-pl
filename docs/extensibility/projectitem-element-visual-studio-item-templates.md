---
title: Projectitem — Element (szablony elementów Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 886fc57258b4ccafaa4ab8d522fad632de455e17
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139575"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem Element (szablony elementów Visual Studio)
Określa plik, który znajduje się w szablonie elementu.  
  
> [!NOTE]
>  `ProjectItem` Element akceptuje różnych atrybutów w zależności od tego, czy szablon jest dla projektu lub elementu. W tym temacie opisano `ProjectItem` elementu dla elementu. Aby uzyskać informacje o `ProjectItem` element szablonów projektu, zobacz [projectitem — Element (Visual Studio projektu szablony)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<ProjectItem >  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`SubType`|Atrybut opcjonalny.<br /><br /> Określa podtyp elementu szablonów elementów wielu plików. Ta wartość służy do określania Edytor który [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] będzie używany do otwierania elementu.|  
|`CustomTool`|Atrybut opcjonalny.<br /><br /> Ustawia element CustomTool elementu w pliku projektu.|  
|`ItemType`|Atrybut opcjonalny.<br /><br /> Ustawia element ItemType elementu w pliku projektu.|  
|`ReplaceParameters`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element ma wartości parametrów, które muszą zostać zastąpione podczas projektu jest tworzona na podstawie szablonu. Wartość domyślna to `false`.|  
|`TargetFileName`|Atrybut opcjonalny.<br /><br /> Określa nazwę elementu, który został utworzony na podstawie szablonu. Ten atrybut jest przydatny do utworzenia nazwy elementu przy użyciu zastąpienia parametrów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Określa zawartość szablonu.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 A `string` reprezentujący nazwę pliku w pliku zip szablonu.  
  
## <a name="remarks"></a>Uwagi  
 `ProjectItem` jest opcjonalne podrzędnym `TemplateContent`.  
  
 `TargetFileName` Atrybut może służyć do zmiany nazwy plików z parametrami. Na przykład jeśli plik `MyFile.vb` istnieje w katalogu głównym pliku zip szablonu, ale ma nazwę pliku na podstawie nazwy pliku podanego przez użytkownika w **Dodaj nowy element** okno dialogowe, należy użyć następującego kodu XML:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Po utworzeniu elementu za pomocą tego szablonu, nazwa pliku będą oparte na Nazwa użytkownika wprowadzona w **Dodaj nowy element** okno dialogowe. Jest to przydatne, gdy tworzenie szablonów elementów wielu plików. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md) i [parametrów szablonu](../ide/template-parameters.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia metadane szablonu elementu standardowe dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] klasy.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Porady: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)