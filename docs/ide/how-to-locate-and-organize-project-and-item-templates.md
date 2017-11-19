---
title: "Porady: lokalizowanie i organizowanie projektu i elementu szablonów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1846b145833a7474e8662442313d0e39a262e67c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Porady: lokalizowanie i organizowanie szablonów projektów i elementów
Pliki szablonów muszą znajdować się w lokalizacji, która rozpoznaje programu Visual Studio, aby szablony będą wyświetlane w **nowy projekt** i **Dodaj nowy element** okien dialogowych. Podkategorie niestandardowy dla szablonów można tworzyć, aby podkategorii są również wyświetlane w interfejsie użytkownika.  

## <a name="locating-templates"></a>Lokalizowanie szablonów  
 Domyślnie program Visual Studio wyszukuje dwie lokalizacje szablonów projektów i elementów. Jeśli istnieje skompresowany plik, który zawiera plik .vstemplate w tych lokalizacjach, szablon pojawi się w **nowy projekt** lub **Dodaj nowy element** okien dialogowych.  

### <a name="installed-templates"></a>Zainstalowane szablony  
 Domyślnie szablony zainstalowane razem z produktu znajdują się w:  

-   \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*języka*\\*ustawień regionalnych*\  

-   \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*języka*\\*ustawień regionalnych\\*  

 Na przykład następujący katalog zawiera [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablony projektu w języku angielskim:  

 C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\  

### <a name="custom-templates"></a>Szablony niestandardowe  
 Domyślnie szablony niestandardowe znajdują się w:  

-   Studio \My *wersji*\Templates\ProjectTemplates\\*języka*\  

-   Studio \My *wersji*\Templates\ItemTemplates\\*języka*\  

 Na przykład następujący katalog zawiera niestandardowe [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablony projektu:  

 C:\Documents and Settings\NazwaUżytkownika\Moje Documents\Visual Studio *wersji*\Templates\ProjectTemplates\Visual C# \  

 Szablony niestandardowe nie dołączaj podkatalogu zlokalizowanych szablonów. Można zmienić domyślny katalog niestandardowych szablonów w **opcje** okna dialogowego, w obszarze **Environment\Projects i rozwiązań**.  

## <a name="organizing-templates"></a>Organizowanie szablonów  
 Kategorie w **nowy projekt** i **Dodaj nowy element** okien dialogowych odzwierciedlić struktur katalogów, które istnieją w lokalizacjach zainstalowanych i niestandardowego szablonu. Można zmodyfikować te struktury katalogu tak, aby uporządkować w taki sposób, który ma sens dla Ciebie.  

> [!NOTE]
>  Nie można utworzyć nową kategorię na poziomie języka programowania. Nowych kategorii można tworzyć tylko w ramach każdego języka.  

 Jeśli struktur katalogów dla zainstalowanych szablonów niestandardowych dla określonego języka nie mają tej samej struktury (to znaczy istnieją katalogi w ramach jednego folderu, które nie istnieją w drugiej) zestaw kategorii, które są widoczne w **nowy Projekt** okno dialogowe będzie połączeniem wszystkich kategorii.  

### <a name="organizing-installed-templates"></a>Organizowanie zainstalowane szablony  
 Zainstalowane szablony można określić, tworząc podkatalogów w folderze języka programowania. Te podkatalogi są wyświetlane w **nowy projekt** i **Dodaj nowy element** okien dialogowych jako wirtualny folderów w ramach każdego języka.  

##### <a name="to-create-new-installed-project-template-categories"></a>Aby utworzyć nowy projekt zainstalowanych kategorie szablonów  

1.  Utwórz folder katalogu szablonu zainstalowany folder języka. Na przykład, aby utworzyć kategorii Office [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablony, należy utworzyć następującego katalogu projektu:  

     \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\  

2.  Umieść wszystkie szablony dla tej kategorii w nowym folderze.  

3.  Zamknij wszystkie wystąpienia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  

4.  Na **Start** menu, kliknij przycisk **Uruchom**, typ **cmd**i kliknij przycisk **OK**.  

5.  W wierszu polecenia zlokalizować katalogu, który zawiera devenv.exe i typ **devenv/installvstemplates**.  

6.  Run [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  

7.  Na **pliku** menu, kliknij przycisk **nowy**, a następnie kliknij przycisk **projektu**.  

8.  Sprawdź, czy kategoria Office jest wyświetlany w **nowy projekt** okna dialogowego, **typy projektów** okienku w obszarze [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  

 Można także grupować podzbiór szablony elementów projektu do folderu niestandardowych.  

##### <a name="to-create-new-installed-item-template-categories"></a>Aby utworzyć nowy element zainstalowanych kategorie szablonów  

1.  Utwórz folder katalogu szablonu zainstalowany folder języka. Na przykład, aby utworzyć kategorię sieci Web [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] elementu szablonów, należy utworzyć następującego katalogu:  

     \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\  

2.  Umieść wszystkie szablony dla tej kategorii w nowym folderze.  

3.  Zamknij wszystkie wystąpienia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  

4.  Na **Start** menu, kliknij przycisk **Uruchom**, typ **cmd**i kliknij przycisk **OK**.  

5.  W wierszu polecenia zlokalizować katalogu, który zawiera devenv.exe i typ **devenv/Setup**.  

6.  Run [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  

7.  Tworzenie projektu lub otworzyć istniejącego projektu.  

8.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  

9. Sprawdź, czy kategoria sieci Web jest wyświetlany w **Dodaj nowy element** okna dialogowego, **typy projektów** okienka.  

### <a name="organizing-custom-templates"></a>Organizowanie szablonów niestandardowych  
 Szablony niestandardowe można można podzielić na ich własnych kategorii, dodając nowe foldery w lokalizacji szablonu niestandardowego. **Nowy projekt** okno dialogowe odzwierciedla wszystkie zmiany wprowadzone do kategorii szablonu.  

##### <a name="to-create-new-custom-project-template-categories"></a>Aby utworzyć nowy projekt niestandardowe kategorie szablonów  

1.  Utwórz folder folder języka w katalogu projektu niestandardowego szablonu. Na przykład, aby utworzyć kategorię HelloWorld [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonów, należy utworzyć następującego katalogu:  

     Studio \My *wersji*\Templates\ProjectTemplates\CSharp\HelloWorld\  

2.  Umieść wszystkie szablony dla tej kategorii w nowym folderze.  

3.  Na **pliku** menu, kliknij przycisk **nowy**, a następnie kliknij przycisk **projektu**.  

4.  Sprawdź, czy kategoria HelloWorld jest wyświetlany w **nowy projekt** okna dialogowego, **typy projektów** okienku w obszarze [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  

 Można także grupować podzbiór szablonów niestandardowych elementów do folderu niestandardowych.  

##### <a name="to-create-new-custom-item-template-categories"></a>Aby utworzyć nowy element niestandardowego szablonu kategorii  

1.  Utwórz folder folder języka w katalogu szablonu niestandardowego elementu. Na przykład, aby utworzyć kategorię HelloWorld [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonów należy utworzyć następującego katalogu:  

     Studio \My *wersji*\Templates\ItemTemplates\CSharp\HelloWorld\  

2.  Umieść wszystkie szablony dla tej kategorii w nowym folderze.  

3.  Tworzenie projektu lub otworzyć istniejącego projektu.  

4.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  

5.  Sprawdź, czy kategoria HelloWorld jest wyświetlany w **Dodaj nowy element** okna dialogowego, **typy projektów** okienka.  

### <a name="displaying-templates-in-parent-categories"></a>Wyświetlanie szablonów w kategorii nadrzędnych  
 Można włączyć szablonów w podkategoriach mają być wyświetlane w ich kategorii nadrzędnych za pomocą `NumberOfParentCategoriesToRollUp` elementu w pliku .vstemplate. Te kroki są identyczne dla szablonów elementów i szablonów projektu.  

##### <a name="to-display-templates-in-parent-categories"></a>Aby wyświetlić szablony w kategorii nadrzędnych  

1.  Zlokalizuj plik zip, który zawiera szablon.  

2.  Wyodrębnij plik zip.  

3.  Otwórz plik .vstemplate w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  

4.  W `TemplateData` elementu, Dodaj `NumberOfParentCategoriesToRollUp` elementu. Na przykład następujący kod sprawia, że szablon widoczne w kategorii nadrzędnej, ale nie jest wyższa.  

    ```  
    <TemplateData>  
        ...  
        <NumberOfParentCategoriesToRollUp>  
            1  
        </NumberOfParentCategoriesToRollUp>  
        ...  
    </TemplateData>  
    ```  

5.  Zapisz i zamknij plik .vstemplate.  

6.  Wybierz pliki do szablonu, kliknij prawym przyciskiem myszy zaznaczenie, kliknij przycisk **Wyślij do**, a następnie kliknij przycisk **skompresowany Folder (zip)**. Pliki są kompresowane do pliku zip.  

7.  Usuń pliki szablonów wyodrębnionego i stary plik zip szablonu.  

8.  Umieść nowy plik zip w katalogu, który miał plik zip usunięte.  

## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [NumberOfParentCategoriesToRollUp (szablony Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)   
 [Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)   
 [Porady: Tworzenie szablonów elementu](../ide/how-to-create-item-templates.md)
