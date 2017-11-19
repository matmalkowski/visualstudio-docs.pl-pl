---
title: "Porady: Tworzenie szablonów elementu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ecd17694e65c6273f8e73a321a72bc209038922
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-item-templates"></a>Porady: tworzenie szablonów elementu
Kroki opisane w [Pierwsza procedura](../ide/how-to-create-item-templates.md#export_template) w tym temacie opisano sposób tworzenia szablonu elementu przy użyciu **Eksportuj szablon** kreatora. Jeśli szablon będzie składać się z wielu plików, zobacz [porady: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md).  

 Kreator wykona dużo pracy można utworzyć szablon podstawowy, ale w wielu przypadkach należy ręcznie zmodyfikować plik .vstemplate po wyeksportowaniu szablonu. Na przykład, jeśli element ma się pojawiać **Dodaj nowy element** okno dialogowe [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projektu aplikacji, musisz wykonać kilka dodatkowych czynności. [Drugiej procedury](../ide/how-to-create-item-templates.md#modify_template) w tym temacie ułatwia wykonywanie tego zadania.  

 Aby określić, czy szablon powinien pojawić się tylko dla tylko niektórych podrzędnych typów projektów, takich jak Office, bazy danych lub sieci Web, zobacz [w tej sekcji](#enable_templates).  

 W niektórych przypadkach może mają lub należy ręcznie utworzyć szablon elementu od początku. [Trzeci procedury](../ide/how-to-create-item-templates.md#create_template) pokazuje, jak to zrobić.  

 Zobacz [odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md) informacji o elementach, które mogą być używane w pliku .vstemplate.  

### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>Aby dodać szablon elementu projektu niestandardowych do okna dialogowego Dodaj nowy element  

1.  Utwórz lub Otwórz projekt w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  

2.  Dodaj element do projektu, a następnie zmodyfikować go, jeśli chcesz.  

3.  Zmodyfikuj kod wskaż, gdzie parametr zastąpienia powinno mieć miejsce. Aby uzyskać więcej informacji, zobacz [porady: parametry zastępczych w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).  

4.  Na **projektu** menu, kliknij przycisk **Eksportuj szablon**.  

5.  Kliknij przycisk **szablon elementu**, a następnie wybierz projekt, który zawiera element i kliknij przycisk **dalej**.  

6.  Wybierz element, dla którego chcesz utworzyć szablon, a następnie kliknij przycisk **dalej**.  

7.  Odwołania do zestawów do uwzględnienia w szablonie, a następnie kliknij przycisk Wybierz **dalej**.  

8.  Wpisz nazwy pliku ikony, podglądu, szablon nazwę i opis szablonu, a następnie kliknij przycisk **Zakończ**.  

     Pliki szablonu zostaną dodane do pliku zip i skopiowany do katalogu, niezależnie od określonej w oknie dialogowym. Domyślna lokalizacja to **... \Users\\< nazwa_użytkownika\>\Documents\Visual Studio \<wersji > Szablony wyeksportowane \My\\**  folderu.  

    > [!WARNING]
    >  We wcześniejszych wersjach programu Visual Studio, domyślna lokalizacja to **... \Users\\< nazwa_użytkownika\>\Documents\Visual Studio \<wersji > \Templates\ItemTemplates**.  

### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>Aby włączyć szablon elementu, który ma być używany w projekcie magazynu  

1.  Wykonaj kroki opisane w poprzedniej procedurze, aby wyeksportować szablon elementu.  

2.  Wyodrębnij plik .vstemplate z pliku zip, który został skopiowany do... \Users\\*username*\Documents\Visual Studio *wersji*\Templates\ItemTemplates\ (lub **Moje szablony wyeksportowane**) folderu.  

3.  Otwórz plik .vstemplate w programie Visual Studio.  

4.  Dla uniwersalnych systemu Windows C# projektu w pliku .vstemplate dodać następujący kod XML w granicach otwarcia `<TemplateData>` tag: `<TemplateID>Microsoft.CSharp.Class</TemplateID>`. 

    Windows 8.1 przechowywania projektu C# w pliku .vstemplate, Dodaj następujące XML w otwarcia i zamknięcia `<TemplateData>` tag: `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`.  

    Projekt Sklepu Windows 8.1 C++ została użyta wartość `WinRT-Native-6.3`. Dla systemu Windows 10 i innych typów projektów, zobacz [TemplateGroupID — Element (szablony Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md).  

    Poniższy przykład przedstawia całą zawartość pliku .vstemplate po wierszu kodu XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` został dodany do niego. W tym przykładzie jest specyficzne dla projektów C#. Można zmodyfikować <ProjectTpe> i \< [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)> elementy, aby określić inne typy języka i projektu.  

    ```xml  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>MyItemStoreTemplate.xaml</DefaultName>  
        <Name>MyItemStoreTemplate</Name>  
        <Description>This is an example itemtemplate</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>10</SortOrder>  
        <Icon>__TemplateIcon.ico</Icon>  
        <TemplateGroupID>WinRT-Managed</TemplateGroupID>  
      </TemplateData>  
      <TemplateContent>  
        <References />  
        <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>  
        <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  

     Dla innych możliwych wartości TemplateGroupID [TemplateGroupID — Element (szablony Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md)). Aby .vstemplate pełne informacje, zobacz [odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)  

5.  W programie Visual Studio Zapisz plik .vstemplate i zamknij go.  

6.  Skopiuj i Wklej do pliku zip, znajduje się w pliku .vstemplate. \Users\\*username*\Documents\Visual Studio *wersji*\Templates\ItemTemplates\ folderu.  

     Jeśli **kopiowania pliku** zostanie wyświetlone okno dialogowe, wybierz **Kopiuj i Zamień** opcji.  

 Teraz można dodać elementu na podstawie tego szablonu do [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projektu przy użyciu **Dodaj nowy element** okno dialogowe.  

 Aby uzyskać więcej informacji na temat nazw parametrów, zobacz [parametrów szablonu](../ide/template-parameters.md).  
  
 
### <a name="enable_templates"></a>Aby włączyć szablonów dla określonego projektu podtypów  

1.  Środowisko projektowe umożliwia udostępnianie elementów projektu z okna dialogowego Dodawanie elementu niektórych projektów. Użyj tej procedury, aby udostępnić niestandardowe elementy dla systemu Windows, sieci Web, Office lub projektów bazy danych.  

     Znajdź ProjectType element w pliku .vstemplate szablonu elementu.  

     Dodaj [projectsubtype —](../extensibility/projectsubtype-element-visual-studio-templates.md) element natychmiast po elemencie typ projektu.  

2.  Ustaw wartość tekstowego elementu do jednego z następujących wartości:  

    1.  Windows  

    2.  Office  

    3.  Baza danych  

    4.  sieć Web  

     Na przykład: `<ProjectSubType>Database</ProjectSubType>`.  

     W poniższym przykładzie przedstawiono szablon elementu dostępne dla projektów pakietu Office.  

    ```  
    <VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">  
        <TemplateData>  
            <Name>Class</Name>  
            <Description>An empty class file</Description>  
            <Icon>Class.ico</Icon>  
            <ProjectType>CSharp</ProjectType>  
            <ProjectSubType>Office</ProjectSubType>  
            <DefaultName>Class.cs</DefaultName>  
        </TemplateData>  
        <TemplateContent>  
            <ProjectItem>Class1.cs</ProjectItem>  
        </TemplateContent>  
    </VSTemplate>  

    ```  

### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Aby ręcznie utworzyć szablon elementu bez użycia Kreatora eksportowania szablonu  

1.  Tworzenie projektu i elementu projektu.  

2.  Element projektu należy modyfikować, dopóki będzie gotowy do zapisania jako szablon.  

3.  Zgodnie z potrzebami należy zmodyfikować plik kodu, wskaż, gdzie powinien wystąpić wymiany parametru. Aby uzyskać więcej informacji na temat wymiany parametru, zobacz [porady: parametry zastępczych w szablonie.](../ide/how-to-substitute-parameters-in-a-template.md)

4.  Tworzenie pliku XML i zapisz go przy użyciu rozszerzenie nazwy pliku .vstemplate w tym samym katalogu co nowego szablonu elementu.  

5.  Tworzenie pliku XML .vstemplate do udostępnienia metadanych szablonu elementu. Aby uzyskać więcej informacji, zobacz [odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md) i przykładowe w poprzedniej sekcji.  

6.  Zapisz plik .vstemplate i zamknij go.  

7.  W Eksploratorze Windows zaznacz pliki, które chcesz uwzględnić w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, kliknij przycisk Wyślij do, a następnie kliknij Folder skompresowane. Wybrane pliki są kompresowane do pliku zip.  

8.  Skopiuj plik zip i wklej go w lokalizacji szablonu elementu użytkownika. W programie Visual Studio 2017 r domyślnym katalogiem jest... \Users\\< nazwa_użytkownika\>\Documents\Visual 2017\Templates\ItemTemplates w Studio\\. Aby uzyskać więcej informacji, zobacz porady: Znajdź i organizowanie szablony projektów i elementów.  

## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Porady: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
