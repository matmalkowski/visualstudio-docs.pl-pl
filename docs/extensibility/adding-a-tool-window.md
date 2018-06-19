---
title: Dodawanie okna narzędzia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db06bebd700fa229685d6b79ffcfb014ef301994
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107884"
---
# <a name="adding-a-tool-window"></a>Dodawanie okna narzędzia
W tym przewodniku Dowiedz się jak utworzyć okna narzędzia i zintegrować ją z programu Visual Studio w następujący sposób:  
  
-   Dodawanie formantu do okna narzędzia.  
  
-   Dodaj pasek narzędzi do okna narzędzia.  
  
-   Dodaj polecenie do paska narzędzi.  
  
-   Wykonuje polecenia.  
  
-   Ustaw położenie domyślne okna narzędzia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tool-window"></a>Utworzenie okna narzędzia  
  
1.  Tworzenie projektu o nazwie **FirstToolWin** przy użyciu szablonu VSIX, a następnie dodaj niestandardowe narzędzie szablon elementu okna o nazwie **FirstToolWindow**.  
  
    > [!NOTE]
    >  Aby uzyskać więcej informacji o tworzeniu rozszerzenie z okna narzędzia, zobacz [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="add-a-control-to-the-tool-window"></a>Dodawanie formantu do okna narzędzi  
  
1.  Usuwanie domyślnej kontroli. Otwórz FirstToolWindowControl.xaml i Usuń **kliknij mnie!** przycisk.  
  
2.  W **przybornika**, rozwiń węzeł **wszystkich kontrolek WPF** sekcji i przeciągnij **elementu mediów** formant **FirstToolWindowControl** formularza. Wybierz kontrolkę, a następnie w **właściwości** okna, nazwa tego elementu **mediaElement1**.  
  
## <a name="add-a-toolbar-to-the-tool-window"></a>Dodaj pasek narzędzi do okna narzędzi  
 Dodając pasek narzędzi w następujący sposób, użytkownik gwarantuje, że jego gradienty i kolory są spójności z resztą środowiska IDE.  
  
1.  W **Eksploratora rozwiązań**, otwórz FirstToolWindowPackage.vsct. Pliku vsct definiuje elementów graficznego interfejsu użytkownika (GUI) w oknie narzędzia, za pomocą XML.  
  
2.  W `<Symbols>` sekcji, Znajdź `<GuidSymbol>` węzła których `name` atrybutu `guidFirstToolWindowPackageCmdSet`. Dodaj następujące dwa `<IDSymbol>` elementów do listy `<IDSymbol>` elementów w tym węźle do definiowania paska narzędzi i grupy paska narzędzi.  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  Po prostu powyżej `<Buttons>` sekcji, Utwórz `<Menus>` sekcji podobny to:  
  
    ```xml  
    <Menus>  
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">  
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
            <Strings>  
                <ButtonText>Tool Window Toolbar</ButtonText>  
                <CommandName>Tool Window Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Istnieje kilka różnych rodzajów menu. Tego menu jest paskiem narzędzi w oknie narzędzia zdefiniowane przez jego `type` atrybutu. `guid` i `id` ustawienia tworzą pełny identyfikator paska narzędzi. Zazwyczaj `<Parent>` menu jest grupy zawierającej. Jednak narzędzi jest zdefiniowany jako własnego elementu nadrzędnego. W związku z tym samym identyfikatorze służy do `<Menu>` i `<Parent>` elementy. `priority` Atrybut jest tylko "0".  
  
4.  Paski narzędzi przypominać menu na wiele sposobów. Na przykład tak samo, jak menu może mieć grup poleceń, paski narzędzi mogą także mieć grup. (W menu, grup polecenia są oddzielone poziome linie. Na paskach narzędzi grupy nie są rozdzielone visual separatorów.)  
  
     Dodaj `<Groups>` sekcję zawierającą `<Group>` elementu. To definiuje grupę, do których identyfikator zadeklarowany w `<Symbols>` sekcji. Dodaj `<Groups>` sekcji tuż po `<Menus>` sekcji.  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     Ustawiając nadrzędny identyfikator GUID i identyfikator GUID i identyfikator paska narzędzi, Dodaj grupę do paska narzędzi.  
  
## <a name="add-a-command-to-the-toolbar"></a>Dodaj polecenie do paska narzędzi  
 Dodaj polecenie do paska narzędzi, który jest wyświetlany jako przycisk.  
  
1.  W `<Symbols>` sekcji, Zadeklaruj następujące elementy IDSymbol zaraz po narzędzi i narzędzi deklaracje grupy.  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  Dodaj element przycisku wewnątrz `<Buttons>` sekcji. Ten element pojawi się na pasku narzędzi w oknie narzędzi z ikoną wyszukiwania (Lupa).  
  
    ```xml  
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">  
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <Strings>  
            <CommandName>cmdidWindowsMediaOpen</CommandName>  
            <ButtonText>Load File</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  Otwórz FirstToolWindowCommand.cs i dodaj następujące wiersze w klasie zaraz po istniejących pól.  
  
    ```csharp  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     W ten sposób udostępnia poleceniach w kodzie.  
  
## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Dodaj właściwość MediaPlayer do FirstToolWindowControl  
 Z obsługi zdarzeń dla formantów narzędzi kod musi mieć możliwość kontroli Media Player, który jest elementem podrzędnym klasy FirstToolWindowControl dostępu.  
  
 W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy FirstToolWindowControl.xaml, kliknij przycisk **kod widoku**i Dodaj następujący kod do klasy FirstToolWindowControl.  
  
```csharp  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## <a name="instantiate-the-tool-window-and-toolbar"></a>Utwórz wystąpienie okna narzędzia i paska narzędzi  
 Dodaj pasek narzędzi i polecenie menu, które wywołuje **Otwórz plik** okno dialogowe i odtwarzany wybrany plik multimedialny.  
  
1.  Otwórz FirstToolWindow.cs i dodaj następujące `using` instrukcje.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  Wewnątrz klasy FirstToolWindow Dodaj publiczny odwołanie do formantu FirstToolWindowControl.  
  
    ```csharp  
    public FirstToolWindowControl control;  
    ```  
  
3.  Na końcu konstruktora należy ustawić tę zmienną kontroli do nowo utworzonego formantu.  
  
    ```csharp  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  Uruchamianie narzędzi w konstruktorze.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  W tym momencie konstruktora FirstToolWindow powinien wyglądać następująco:  
  
    ```csharp  
    public FirstToolWindow() : base(null)  
    {  
        this.Caption = "FirstToolWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
        control = new FirstToolWindowControl();  
        base.Content = control;  
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
            FirstToolWindowCommand.ToolbarID);  
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    }  
    ```  
  
6.  Dodaj polecenie menu do paska narzędzi. W klasie FirstToolWindowCommand.cs, dodaj następującą instrukcję using  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
7.  W klasie FirstToolWindowCommand Dodaj następujący kod na końcu metody ShowToolWindow(). Polecenie ButtonHandler będą realizowane w następnej sekcji.  
  
    ```csharp  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
#### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Do wykonania polecenia menu okna narzędzi  
  
1.  W klasie FirstToolWindowCommand dodanie metody ButtonHandler, która wywołuje **Otwórz plik** okna dialogowego. Po wybraniu pliku odtwarzania pliku multimedialnego.  
  
2.  W klasie FirstToolWindowCommand Dodaj odwołanie prywatnych do okna FirstToolWindow, który jest tworzony w metodzie FindToolWindow().  
  
    ```csharp  
    private FirstToolWindow window;  
    ```  
  
3.  Zmień metodę ShowToolWindow() można ustawić okna zdefiniowanych powyżej (tak, aby program obsługi poleceń ButtonHandler można uzyskać dostępu do formantu okna. W tym miejscu jest pełną metodą ShowToolWindow().  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
                            throw new NotSupportedException("Cannot create tool window");  
        }  
  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
         var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),  
            FirstToolWindowCommand.cmdidWindowsMediaOpen);  
        var menuItem = new MenuCommand(new EventHandler(  
            ButtonHandler), toolbarbtnCmdID);  
        mcs.AddCommand(menuItem);  
    }  
    ```  
  
4.  Dodaj metodę ButtonHandler. Tworzy OpenFileDialog dla użytkownika określić plik, aby odtworzyć, i następnie odtworzenie wybranego pliku.  
  
    ```csharp  
    private void ButtonHandler(object sender, EventArgs arguments)  
    {  
        OpenFileDialog openFileDialog = new OpenFileDialog();  
        DialogResult result = openFileDialog.ShowDialog();  
        if (result == DialogResult.OK)  
        {  
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);  
        }  
    }  
    ```  
  
## <a name="set-the-default-position-for-the-tool-window"></a>Ustaw położenie domyślne okna narzędzi  
 Następnie należy określić domyślną lokalizację w IDE dla okna narzędzia. Informacje o oknie narzędzia konfiguracji są w pliku FirstToolWindowPackage.cs.  
  
1.  W FirstToolWindowPackage.cs, Znajdź <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atrybutu `FirstToolWindowPackage` klasy, która przekazuje do konstruktora typu FirstToolWindow. Aby określić domyślne położenie, należy dodać większej liczby parametrów do konstruktora poniższy przykład.  
  
    ```csharp  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     Pierwszy parametr o nazwie jest `Style` i jego wartość wynosi `Tabbed`, która oznacza, że okno będzie na karcie istniejącego okna. Pozycję dokowania jest określona przez `Window` parametru, n-tym przypadku identyfikator GUID **Eksploratora rozwiązań**.  
  
    > [!NOTE]
    >  Aby uzyskać więcej informacji na temat typów systemu windows w środowisku IDE, zobacz <xref:EnvDTE.vsWindowType>.  
  
## <a name="testing-the-tool-window"></a>Testowanie okna narzędzi  
  
1.  Naciśnij klawisz F5, aby otworzyć nowe wystąpienie programu Visual Studio eksperymentalne kompilacji.  
  
2.  Na **widoku** menu wskaż **inne okna** , a następnie kliknij przycisk **pierwszy okna narzędzia**.  
  
     Należy otworzyć okno narzędzia media player, w tym samym miejscu **Eksploratora rozwiązań**. Jeśli nadal wyświetlany w tym samym miejscu wcześniej, należy zresetować układ okna (**okna / zresetować układ okna**).  
  
3.  Kliknij przycisk (ma ikonę wyszukiwania) w oknie narzędzia. Wybierz obsługiwany plik dźwiękowy lub wideo, na przykład C:\windows\media\chimes.wav, naciśnij klawisz **Otwórz**.  
  
     Usłyszeć dźwięk brzęczyka.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)