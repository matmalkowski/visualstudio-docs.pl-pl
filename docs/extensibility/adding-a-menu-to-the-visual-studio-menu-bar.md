---
title: Dodawanie Menu na pasku Menu programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: "51"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e4a2485b7e702844a037787234ef3a1ab66495d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Dodawanie Menu na pasku Menu programu Visual Studio
W tym przewodniku przedstawiono sposób dodawania menu na pasku menu programu Visual Studio zintegrowane środowisko programistyczne (IDE). Na pasku menu IDE zawiera menu Kategorie, takie jak **pliku**, **Edytuj**, **widoku**, **okna**, i **Pomoc** .  
  
 Przed dodaniem nowego menu na pasku menu programu Visual Studio, rozważ, czy poleceniach powinna zostać umieszczona w ramach istniejącego menu. Aby uzyskać więcej informacji o umieszczaniu polecenia, zobacz [menu i poleceń programu Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 Menu został zadeklarowany w pliku vsct projektu. Aby uzyskać więcej informacji na temat menu i vsct plików, zobacz [polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Wykonując tego przewodnika, można utworzyć menu o nazwie **TestMenu** zawiera jedno polecenie.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Tworzenie projektu VSIX, który zawiera szablon elementu polecenia niestandardowych  
  
1.  Tworzenie projektu VSIX o nazwie `TopLevelMenu`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C#** / **rozszerzalności**.  Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Po otwarciu projektu Dodawanie polecenia niestandardowego szablonu elementu o nazwie **TestCommand**. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **polecenia niestandardowych**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby **TestCommand.cs**.  
  
## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Tworzenie Menu na pasku Menu IDE  
  
#### <a name="to-create-a-menu"></a>Aby utworzyć menu  
  
1.  W **Eksploratora rozwiązań**, otwórz TestCommandPackage.vsct.  
  
     Na końcu pliku, Brak \<symbole > węzeł, który zawiera kilka \<GuidSymbol > węzłów. W węźle o nazwie guidTestCommandPackageCmdSet Dodaj nowy symbol w następujący sposób:  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  Utwórz pustą \<menu > w węźle \<polecenia > węzła, bezpośrednio przed \<grupy >. W \<menu > węzła, Dodaj \<Menu > węzła, w następujący sposób:  
  
    ```xml  
    <Menus>  
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">  
            <Parent guid="guidSHLMainMenu"  
                    id="IDG_VS_MM_TOOLSADDINS" />  
            <Strings>  
              <ButtonText>TestMenu</ButtonText>  
              <CommandName>TestMenu</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     `guid` i `id` wartości menu określają zestaw poleceń i menu określonych w zestawie polecenia.  
  
     `guid` i `id` wartości elementu nadrzędnego pozycji menu w sekcji paska menu programu Visual Studio, która zawiera menu Narzędzia i dodatki.  
  
     Wartość `CommandName` ciąg Określa, czy tekst powinien być wyświetlany w elemencie menu.  
  
3.  W \<grup > sekcji, Znajdź \<grupy > i zmień \<nadrzędnej > element, aby wskazywał właśnie dodaliśmy menu:  
  
    ```csharp  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     Dzięki temu grupy część nowego menu.  
  
4.  Znajdź `Buttons` sekcji. Zwróć uwagę, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wygenerowała szablonu pakietu `Button` element, który ma nadrzędnego ustawioną `MyMenuGroup`. W związku z tym tego polecenia będą wyświetlane w menu.  
  
## <a name="building-and-testing-the-extension"></a>Tworzenie i testowanie rozszerzenia  
  
1.  Skompiluj projekt i Rozpocznij debugowanie. Wystąpienie eksperymentalne wystąpienie powinny być wyświetlane.  
  
2.  Na pasku menu w eksperymentalnym wystąpieniu powinna zawierać **TestMenu** menu.  
  
3.  Na **TestMenu** menu, kliknij przycisk **wywołania polecenia testowego**.  
  
     Okno komunikatu powinno są wyświetlane i wyświetlenie komunikatu "TestCommand pakietu wewnątrz TopLevelMenu.TestCommand.MenuItemCallback()". Oznacza to, że nowe polecenie działa.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)