---
title: 'Porady: Tworzenie szablonów elementów wielu plików | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de6d2fd4decc4d71fce1fe4f417f429c837deb7f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680580"
---
# <a name="how-to-create-multi-file-item-templates"></a>Porady: tworzenie szablonów elementów wielu plików
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Tworzenie szablonów elementów wielu plików](https://docs.microsoft.com/visualstudio/ide/how-to-create-multi-file-item-templates).  
  
Szablony elementów może określić tylko jeden element, ale czasami element składa się z wielu plików. Na przykład szablon elementu formularzy Windows w języku Visual Basic wymaga następujących trzech plików:  
  
-   Plik .vb, który zawiera kod dla formularza.  
  
-   Odp. plik designer.vb, który zawiera informacje o projektancie formularza.  
  
-   Plik Resx zawierający zasoby osadzone w formularzu.  
  
 Szablony elementów wielu plików wymagają parametry w celu zapewnienia rozszerzeń nazw plików poprawne są używane, gdy element zostanie utworzony w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jeśli utworzysz szablon elementu za pomocą **Eksportuj szablon** kreatora, parametry te są generowane automatycznie i nie dalszej edycji jest wymagany. Poniższe kroki wyjaśniają jak używać parametrów aby upewnić się, że rozszerzeń nazw plików poprawne są tworzone.  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>Ręczne tworzenie szablonów elementów wielu plików  
  
1.  Utwórz szablon elementu, jak należy utworzyć szablon elementu pojedynczego pliku. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md).  
  
2.  Dodaj `TargetFileName` atrybuty do każdego `ProjectItem` elementu. Ustaw wartości `TargetFileName` atrybuty $fileinputname $. *FileExtension*, gdzie *FileExtension* jest rozszerzeniem nazwy pliku w pliku, który jest uwzględniane w szablonie. Na przykład:  
  
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
  
     Gdy element pochodzące z tego szablonu zostanie dodany do projektu, nazwy plików będzie zależeć od nazwy, wpisany przez użytkownika w **Dodaj nowy element** okno dialogowe.  
  
3.  Wybierz pliki do uwzględnienia w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, kliknij przycisk **Wyślij do**, a następnie kliknij przycisk **skompresowany Folder (zip)**. Wybrane pliki są kompresowane w pliku zip.  
  
4.  Umieść plik zip w lokalizacji szablonów elementów użytkownika. Domyślnie katalog jest \My Studio *wersji*\Templates\ItemTemplates\\. Aby uzyskać więcej informacji, zobacz [jak: Znajdź i organizowania szablony](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonu Windows Forms. Gdy element zostanie utworzony na podstawie tego szablonu, nazwy trzy utworzone pliki będą zgodne nazwy wprowadzone w **Dodaj nowy element** okno dialogowe.  
  
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
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Porady: Tworzenie szablonów elementu](../ide/how-to-create-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Instrukcje: Zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md)



