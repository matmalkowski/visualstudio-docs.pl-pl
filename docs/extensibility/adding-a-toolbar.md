---
title: "Dodawanie paska narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da6ea8eac18151f0efbaefb3e9f910b695630669
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-toolbar"></a>Dodawanie paska narzędzi
W tym przewodniku przedstawiono sposób dodawania paska narzędzi do środowiska IDE programu Visual Studio.  
  
 Pasek narzędzi jest poziomy lub pionowy pasek zawierający przyciski, które są powiązane z poleceń. W zależności od jej implementacja paska narzędzi w IDE mogą być położenia, zadokowane na dowolnej stronie okna głównego IDE lub wprowadzone pozostanie przed innymi oknami.  
  
 Ponadto użytkownicy można dodać polecenia do paska narzędzi lub usuń je z niego przy użyciu **Dostosuj** okno dialogowe. Zazwyczaj pasków narzędzi w VSPackages są użytkownika można dostosowywać. Wszystkie dostosowania obsługuje IDE, a pakiet VSPackage reaguje na polecenia. Pakiet VSPackage nie musi wiedzieć, gdzie fizycznie znajduje się polecenie.  
  
 Aby uzyskać więcej informacji na temat menu, zobacz [polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-toolbar"></a>Tworzenie rozszerzenia z paska narzędzi  
 Tworzenie projektu VSIX o nazwie `IDEToolbar`. Dodaj szablon elementu menu polecenie o nazwie **ToolbarTestCommand**. Aby dowiedzieć się, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="creating-a-toolbar-for-the-ide"></a>Tworzenie paska narzędzi dla IDE  
  
1.  ToolbarTestCommandPackage.vsct poszukaj w sekcji symboli. W elemencie GuidSymbol o nazwie guidToolbarTestCommandPackageCmdSet Dodaj deklaracje dla paska narzędzi i grupę narzędzi, w następujący sposób.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  W górnej części sekcji Commands Utwórz części menu. Dodaj Menu element do sekcji menu, aby zdefiniować paska narzędzi.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     Nie można zagnieżdżać paski narzędzi takich jak podmenu. W związku z tym nie trzeba przypisać grupie nadrzędnej. Ponadto nie masz można ustawić priorytet, ponieważ użytkownik może przenieść pasków narzędzi. Zazwyczaj początkowe położenie paska narzędzi zdefiniowano programowo, ale kolejne zmiany przez użytkownika są zachowywane.  
  
3.  W [grup](../extensibility/groups-element.md) po istniejący wpis grupy sekcji, zdefiniuj [grupy](../extensibility/group-element.md) element, aby zawierał polecenia na pasku narzędzi.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  Utwórz przycisk są wyświetlane na pasku narzędzi. W sekcji przycisków Zastąp nadrzędny blok przycisku w pasku narzędzi. Wynikowa bloku przycisk powinien wyglądać następująco:  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Domyślnie jeśli pasek narzędzi nie ma żadnych poleceń nie ma.  
  
5.  Skompiluj projekt i Rozpocznij debugowanie. Eksperymentalne wystąpienie powinny być wyświetlane.  
  
6.  Kliknij prawym przyciskiem myszy na pasku menu programu Visual Studio można pobrać listy paski narzędzi. Wybierz **Test narzędzi**.  
  
7.  Powinien zostać wyświetlony pasek narzędzi z prawej strony, Znajdź w plikach ikona w postaci ikony. Po kliknięciu ikony, powinien zostać wyświetlony komunikat informujący o **ToolbarTestCommandPackage. Wewnątrz IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)