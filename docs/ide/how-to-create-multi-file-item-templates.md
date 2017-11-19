---
title: "Porady: Tworzenie szablonów elementów wielu plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e3e1f6c6e62494f040e2f52180c5588688f460db
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-multi-file-item-templates"></a>Porady: tworzenie szablonów elementów wielu plików
Szablony elementów może określać tylko jeden element, ale czasami element składa się z wielu plików. Szablon elementu formularzy systemu Windows dla języka Visual Basic wymaga na przykład trzy następujące pliki:  
  
-   Plik .vb, który zawiera kod dla formularza.  
  
-   A. plik designer.vb projektanta informacje w formularzu.  
  
-   Plik .resx, który zawiera zasoby osadzone w formularzu.  
  
 Szablony elementów wielu plików wymaga parametrów, aby upewnić się, rozszerzenia nazw plików poprawne są używane, gdy element jest tworzony w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Jeśli tworzysz szablon elementu za pomocą **Eksportuj szablon** kreatora te parametry są generowane automatycznie, a żadne dodatkowe edycji jest wymagana. Poniższych krokach opisano sposób użycia parametrów, aby upewnić się, czy rozszerzenia nazw plików poprawne są tworzone.  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>Ręczne tworzenie szablonów elementów wielu plików  
  
1.  Utwórz szablon elementu, czy podczas tworzenia szablonu elementu pojedynczego pliku. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md).  
  
2.  Dodaj `TargetFileName` atrybutów do każdego `ProjectItem` elementu. Ustaw wartości `TargetFileName` atrybuty do $fileinputname$. *FileExtension*, gdzie *FileExtension* jest rozszerzeniem pliku jest zawarta w szablonie. Na przykład:  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     Gdy element uzyskanych z tego szablonu zostanie dodany do projektu, nazwy będą oparte na nazwę użytkownika wpisanych w **Dodaj nowy element** okno dialogowe.  
  
3.  Wybierz pliki do uwzględnienia w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, kliknij przycisk **Wyślij do**, a następnie kliknij przycisk **skompresowany Folder (zip)**. Wybrane pliki są kompresowane do pliku zip.  
  
4.  Umieść plik zip w lokalizacji szablonu elementu użytkownika. Domyślnie, katalog jest \My Studio *wersji*\Templates\ItemTemplates\\. Aby uzyskać więcej informacji, zobacz [porady: Znajdź i organizowanie szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablonu formularzy systemu Windows. Gdy element jest tworzony na podstawie tego szablonu, nazwy trzy pliki tworzone będzie zgodna z nazwą, wprowadzona w **Dodaj nowy element** okno dialogowe.  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Porady: Tworzenie szablonów elementu](../ide/how-to-create-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Porady: parametry zastępcze w szablonie](../ide/how-to-substitute-parameters-in-a-template.md)