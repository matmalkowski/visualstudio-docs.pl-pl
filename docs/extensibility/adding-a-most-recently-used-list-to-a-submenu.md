---
title: Dodawanie listy ostatnio używanych do podmenu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67eb08feff5d8edd1251c8fcff09d8f148b51b96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>Dodawanie większość ostatnio używane do podmenu
Ten przewodnik jest oparty na pokazów w [dodawanie do Menu podmenu](../extensibility/adding-a-submenu-to-a-menu.md)oraz przedstawiono sposób dodawania listy dynamicznych do podmenu. Lista dynamiczna stanowi podstawę do tworzenia listy najbardziej ostatnio używanych.  
  
 Lista menu dynamiczne rozpoczyna się od symbolu zastępczego w menu. Za każdym razem, gdy menu jest wyświetlany, Visual Studio zintegrowane środowisko programistyczne (IDE) żąda pakiet VSPackage dla wszystkich poleceń, które mają być wyświetlane na symbol zastępczy. Dynamiczne listy mogą występować wszędzie w menu. Jednak dynamicznej listy są zwykle przechowywane i wyświetlane przez siebie w podmenu lub u dołu menu. Przy użyciu tych wzorców projektowych, należy włączyć dynamiczne listę poleceń, aby rozwinąć lub zwinąć bez wpływu na pozycję innych poleceń menu. W tym przewodniku listy ostatnio używanych elementów dynamicznych jest wyświetlane w dolnej części istniejących podmenu, oddzielone od pozostałej części podmenu wiersza.  
  
 Z technicznego punktu widzenia listy dynamicznej można również będą stosowane do paska narzędzi. Jednak firma Microsoft zniechęcić wykorzystanie, ponieważ paska narzędzi powinien pozostać bez zmian, chyba że użytkownik wykona wykonania określonych kroków, aby go zmienić.  
  
 W tym przewodniku tworzy listę MRU cztery elementy, które zmieniają ich kolejność, za każdym razem, gdy niż jeden z nich jest wybrane (Przenosi wybrany element na początku listy).  
  
 Aby uzyskać więcej informacji na temat menu i vsct plików, zobacz [polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby użyć tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-an-extension"></a>Tworzenie rozszerzenia  
  
-   Postępuj zgodnie z procedurami w [dodawanie do Menu podmenu](../extensibility/adding-a-submenu-to-a-menu.md) utworzyć podmenu, który jest modyfikowany w poniższych procedurach.  
  
 Procedury przedstawione w tym przewodniku przyjęto, że nazwa pakiet VSPackage zostało `TopLevelMenu`, która jest nazwa, która jest używana w [Dodawanie Menu na pasku Menu programu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="creating-a-dynamic-item-list-command"></a>Tworzenie polecenia List elementów dynamicznych  
  
1.  Open TestCommandPackage.vsct.  
  
2.  W `Symbols` sekcji w `GuidSymbol` węzła o nazwie guidTestCommandPackageCmdSet, dodać symbol `MRUListGroup` grupy i `cmdidMRUList` polecenia w następujący sposób.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  W `Groups` sekcji, Dodaj grupę zadeklarowane po pozycji istniejącej grupy.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  W `Buttons` Dodaj węzeł do reprezentowania polecenia nowo zadeklarowane, po istniejącej pozycji przycisku.  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     `DynamicItemStart` Flaga umożliwia polecenia ma być generowany dynamicznie.  
  
5.  Skompiluj projekt i uruchomić debugowania do testowania nowego polecenia.  
  
     Na **TestMenu** menu, kliknij przycisk nowe podmenu **pod Menu**, aby wyświetlić nowe polecenie **symbolu zastępczego MRU**. Po zaimplementowaniu dynamicznej listy ostatnio używanych poleceń w następnej procedurze etykieta polecenia zostanie zastąpione przez tę listę, każdym otwarciu podmenu.  
  
## <a name="filling-the-mru-list"></a>Wypełnianie listy ostatnio używanych  
  
1.  W TestCommandPackageGuids.cs, Dodaj następujące wiersze po istniejących identyfikatory poleceń w `TestCommandPackageGuids` definicji klasy.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  W TestCommand.cs Dodaj następującą instrukcję using.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  Dodaj następujący kod w Konstruktorze TestCommand po ostatnim wywołaniu AddCommand. `InitMRUMenu` Zostanie zdefiniowana później  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Dodaj następujący kod w klasie TestCommand. Ten kod inicjuje lista ciągów reprezentujących elementów, który będzie wyświetlany na liście MRU.  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  Po `InitializeMRUList` metody, Dodaj `InitMRUMenu` metody. Polecenia menu listy ostatnio używanych elementów jest inicjowana.  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     Należy utworzyć obiekt polecenia menu dla każdego elementu możliwe na listę MRU. Wywołania IDE `OnMRUQueryStatus` metody dla każdego elementu na liście MRU, dopóki nie zostaną nie ma więcej elementów. W kodzie zarządzanym jedynym sposobem IDE dowiedzieć się, że nie ma więcej elementów jest najpierw utwórz wszystkie możliwe elementy. Jeśli chcesz, dodatkowe elementy jako nie są widoczne w można oznaczyć najpierw za pomocą `mc.Visible = false;` po utworzeniu polecenia menu. Elementy te można następnie być widoczne później za pomocą `mc.Visible = true;` w `OnMRUQueryStatus` metody.  
  
6.  Po `InitMRUMenu` metody, Dodaj następujący `OnMRUQueryStatus` metody. To jest program obsługi, który ustawia tekst dla każdego elementu MRU.  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  Po `OnMRUQueryStatus` metody, Dodaj następujący `OnMRUExec` metody. Jest to zaznaczenie elementu MRU programu obsługi. Ta metoda Przenosi wybrany element na początku listy, a następnie wyświetla wybrany element w oknie komunikatu.  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>Testowanie listy ostatnio używanych  
  
#### <a name="to-test-the-mru-menu-list"></a>Aby sprawdzić listę ostatnio używanych elementów menu  
  
1.  Skompiluj projekt i uruchomić debugowania  
  
2.  Na **TestMenu** menu, kliknij przycisk **TestCommand wywołania**. W ten sposób wyświetla komunikat wskazujący, że polecenie zostało wybrane.  
  
    > [!NOTE]
    >  Ten krok jest wymagany, aby wymusić pakiet VSPackage do ładowania i poprawne wyświetlanie listy ostatnio używanych. Jeśli pominiesz ten krok nie jest wyświetlana na liście MRU.  
  
3.  Na **Test Menu** menu, kliknij przycisk **pod Menu**. Zostanie wyświetlona lista elementów cztery na końcu podmenu, poniżej separatora. Po kliknięciu **3 elementu**, okno komunikatu powinno występować i wyświetlenie tekst "Wybrany element 3". (Jeśli nie zostanie wyświetlona lista cztery elementy, upewnij się, że zostały wykonane z instrukcjami wyświetlanymi w poprzednim kroku.)  
  
4.  Otwórz ponownie podmenu. Zwróć uwagę, że **3 elementu** jest teraz na początku listy i inne elementy zostały przesuwana jedną pozycję. Kliknij przycisk **3 elementu** ponownie i zwróć uwagę że pola wiadomości nadal wyświetlana "Wybrany element 3", co oznacza, że tekst poprawnie został przeniesiony do nowej pozycji wraz z etykietą polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Dynamiczne dodawanie elementów menu](../extensibility/dynamically-adding-menu-items.md)