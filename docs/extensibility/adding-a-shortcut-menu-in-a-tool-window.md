---
title: "Dodawanie Menu skrótów okna narzędzia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4f90f5971a101b54aae1cd968d5d5dad67caec74
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Dodawanie Menu skrótów okna narzędzi
W tym przewodniku umieszcza menu skrótów okna narzędzia. Menu skrótów jest menu wyświetlanym po kliknięciu przycisku, pola tekstowego lub tło okna. Polecenia menu skrótów działają tak samo, jak polecenia w innym menu i pasków narzędzi. Aby obsługiwać menu skrótów, określ go w pliku vsct i wyświetl ją w odpowiedzi na kliknij prawym przyciskiem myszy.  
  
 Okno narzędzia składa się z formanty użytkownika WPF, w który dziedziczy z klasy okna narzędzia niestandardowego <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.  
  
 W tym przewodniku przedstawiono sposób tworzenia menu skrótów jako menu programu Visual Studio, deklarowanie elementów menu w pliku vsct, a następnie używając Framework pakietu zarządzania ich wdrażania w klasie, który definiuje okna narzędzia. Takie podejście umożliwia dostęp do poleceń programu Visual Studio, elementy interfejsu użytkownika i w modelu obiektu automatyzacji.  
  
 Alternatywnie, jeśli z menu skrótów nie będą uzyskiwać dostęp do funkcji programu Visual Studio, możesz użyć <xref:System.Windows.FrameworkElement.ContextMenu%2A> właściwość elementu XAML w formancie użytkownika. Aby uzyskać więcej informacji, zobacz [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Tworzenie pakietu Menu skrótów okna narzędzi  
  
1.  Tworzenie projektu VSIX o nazwie `TWShortcutMenu` i dodać szablon okna narzędzia o nazwie **ShortCutMenu** do niego. Aby uzyskać więcej informacji na temat tworzenia okna narzędzia, zobacz [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Określanie Menu skrótów  
 Menu skrótów, takich jak wskazano w ramach tego przewodnika użytkownicy będą mogli wybrać z listy kolorów, które są używane do wypełnienia tła okna narzędzia.  
  
1.  W ShortcutMenuPackage.vsct Znajdź w elemencie GuidSymbol o nazwie guidShortcutMenuPackageCmdSet i zadeklarować menu skrótów, grupy menu skrótów i opcji menu. GuidSymbol element powinna wyglądać następująco:  
  
    ```xml  
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here  
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />  
        <IDSymbol name="ColorMenu" value="0x1000"/>  
        <IDSymbol name="ColorGroup" value="0x1100"/>  
        <IDSymbol name="cmdidRed" value="0x102"/>  
        <IDSymbol name="cmdidYellow" value="0x103"/>  
        <IDSymbol name="cmdidBlue" value="0x104"/>  
    </GuidSymbol>  
    ```  
  
2.  Bezpośrednio przed elementem przycisków utworzyć element menu, a następnie zdefiniuj menu skrótów w nim.  
  
    ```vb  
    <Menus>  
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">  
        <Strings>  
          <ButtonText>Color change</ButtonText>  
          <CommandName>ColorChange</CommandName>  
        </Strings>  
      </Menu>  
    </Menus>  
    ```  
  
     Menu skrótów nie ma rekordu nadrzędnego, ponieważ nie jest częścią menu lub pasek narzędzi.  
  
3.  Utwórz element grupy z elementu grupy, który zawiera elementy menu skrótów i skojarz grupę z menu skrótów.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  W elemencie przycisków zdefiniuj poszczególnych poleceń, które będą wyświetlane w menu skrótów. Element przycisków powinien wyglądać następująco:  
  
    ```xml  
    <Buttons>  
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">  
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
            <Icon guid="guidImages" id="bmpPic1" />  
            <Strings>  
                <ButtonText>ShortcutMenu</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Red</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Yellow</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Blue</ButtonText>  
            </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
5.  W ShortcutMenuPackageGuids.cs Dodaj zestawu definicji polecenia identyfikatora GUID, menu skrótów i elementów menu.  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Są to takich samych identyfikatorów poleceń zdefiniowanych w sekcji symbole pliku ShortcutMenuPackage.vsct. Grupy kontekstu nie jest uwzględniony w tym miejscu ponieważ jest wymagane tylko w pliku vsct.  
  
## <a name="implementing-the-shortcut-menu"></a>Implementowanie Menu skrótów  
 W tej sekcji implementuje menu skrótów i jego poleceń.  
  
1.  W ShortcutMenu.cs okna narzędzia można pobrać usługi polecenia menu, ale nie formant, który go zawiera. Poniższe kroki pokazują, jak udostępnić usługi polecenia menu do kontrolki użytkownika.  
  
2.  W ShortcutMenu.cs, Dodaj następujące instrukcje using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Zastąp metodę Initialize() okna narzędzia, aby uzyskać usługi polecenia menu i Dodaj formant przekazywanie usługi polecenia menu do contructor:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  W Konstruktorze okna narzędzia ShortcutMenu usunąć wiersza, który dodaje formantu. Konstruktor powinien teraz wyglądać następująco:  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  W ShortcutMenuControl.xaml.cs Dodaj pole prywatne dla usługi polecenia menu i zmień kontrolkę konstruktora podjęcie usługi polecenia menu. Następnie użyj usługi polecenia menu, aby dodać polecenia w menu kontekstowym. Konstruktor ShortcutMenuControl powinna wyglądać podobnie do następującego kodu. Program obsługi poleceń będą zdefiniowane później.  
  
    ```csharp  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  W ShortcutMenuControl.xaml, Dodaj <xref:System.Windows.UIElement.MouseRightButtonDown> zdarzeń na najwyższym poziomie <xref:System.Windows.Controls.UserControl> elementu. Plik XAML powinna wyglądać następująco:  
  
    ```vb  
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            Background="{DynamicResource VsBrush.Window}"  
            Foreground="{DynamicResource VsBrush.WindowText}"  
            mc:Ignorable="d"  
            d:DesignHeight="300" d:DesignWidth="300"  
            Name="MyToolWindow"  
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">  
        <Grid>  
            <StackPanel Orientation="Vertical">  
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>  
            </StackPanel>  
        </Grid>  
    </UserControl>  
    ```  
  
7.  W ShortcutMenuControl.xaml.cs należy dodać szkielet obsługi zdarzeń.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Dodaj następujące instrukcje using do tego samego pliku:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. Implementowanie `MyToolWindowMouseRightButtonDown` zdarzeń w następujący sposób.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     Spowoduje to utworzenie <xref:System.ComponentModel.Design.CommandID> obiekt menu skrótów identyfikuje lokalizację kliknięcia myszą i otwarcie menu skrótów w tym miejscu przy użyciu <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> metody.  
  
10. Wdrożenie programu obsługi poleceń.  
  
    ```csharp  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     W takim przypadku tylko jedna metoda obsługi zdarzeń dla wszystkich elementów menu, określając <xref:System.ComponentModel.Design.CommandID> i odpowiednio Ustawianie koloru tła. Jeśli elementy menu ma niepowiązanych poleceń, czy utworzono obsługi zdarzenia osobne dla każdego polecenia.  
  
## <a name="testing-the-tool-window-features"></a>Testowanie funkcji okna narzędzi  
  
1.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.  
  
2.  W eksperymentalnym wystąpieniu kliknij **widoku / inne okna**, a następnie kliknij przycisk **ShortcutMenu**. W ten sposób powinien być wyświetlany okna narzędzia.  
  
3.  Kliknij prawym przyciskiem myszy w treści okna narzędzia. Menu skrótów, które zawiera listę kolorów powinien być wyświetlany.  
  
4.  Kliknij kolor menu skrótów. Należy zmienić kolor tła okna narzędzia do wybranego koloru.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Korzystanie z usług i dostarczanie ich](../extensibility/using-and-providing-services.md)