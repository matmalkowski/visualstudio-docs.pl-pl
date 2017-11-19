---
title: Tworzenie stron opcje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: "62"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 68a3afc0a83d4dba7b7cd46b2b1eba23695a2848
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-options-page"></a>Tworzenie stron opcje
W tym przewodniku tworzy prosta strona narzędzia/Opcje, która używa siatki właściwości do badania i ustaw właściwości.  
  
 Aby zapisać te właściwości, aby i przywrócić je z pliku ustawień, wykonaj następujące czynności, a następnie zobacz [tworzenia kategorii ustawienia](../extensibility/creating-a-settings-category.md).  
  
 MPF oferuje dwie klasy ułatwiające tworzenie strony opcji narzędzi <xref:Microsoft.VisualStudio.Shell.Package> klasy i <xref:Microsoft.VisualStudio.Shell.DialogPage> klasy. Należy utworzyć pakiet VSPackage zapewnienie kontener dla tych stron przez tworzenie podklas klas pakietu. Wyprowadzanie z klas elementu DialogPage do tworzenia każdej strony opcji narzędzi.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tools-options-grid-page"></a>Tworzenie strony siatki opcji narzędzi  
 W tej sekcji utworzysz prosty siatki właściwości opcji narzędzi. Ta siatka służy do wyświetlania i zmieniania wartości właściwości.  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Do tworzenia projektu VSIX i dodać pakiet VSPackage  
  
1.  Każde rozszerzenie programu Visual Studio rozpoczyna się od VSIX Projekt wdrożenia, który będzie zawierać zasoby rozszerzenia. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projektu o nazwie `MyToolsOptionsExtension`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2.  Dodaj pakiet VSPackage przez dodanie szablonu elementu pakiet programu Visual Studio o nazwie `MyToolsOptionsPackage`. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **okno dialogowe Dodaj nowy element**, przejdź do **elementów Visual C# / rozszerzalności** i wybierz **pakiet programu Visual Studio**. W **nazwa** u dołu okna dialogowego, Zmień nazwę pliku, aby `MyToolsOptionsPackage.cs`. Aby uzyskać więcej informacji na temat tworzenia pakiet VSPackage, zobacz [Tworzenie rozszerzenia z pakiet VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### <a name="to-create-the-tools-options-property-grid"></a>Aby utworzyć siatki właściwości opcji narzędzi  
  
1.  Otwórz plik MyToolsOptionsPackage w edytorze kodu.  
  
2.  Dodaj następującą instrukcję using.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  Deklarowanie klasy OptionPageGrid i pochodzi ona z <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Zastosuj <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do klasy pakiet VSPackage można przypisać do klasy opcje kategorii i nazwy strony opcje dla OptionPageGrid. Wynik powinien wyglądać następująco:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Dodaj `OptionInteger` właściwości `OptionPageGrid` klasy.  
  
    -   Zastosuj <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> można przypisać do właściwości kategorii siatki właściwości.  
  
    -   Zastosuj <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> można przypisać do właściwości name.  
  
    -   Zastosuj <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> można przypisać do właściwości Opis.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
  
        [Category("My Category")]  
        [DisplayName("My Integer Option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  Domyślna implementacja <xref:Microsoft.VisualStudio.Shell.DialogPage> obsługuje właściwości, która ma odpowiednie konwertery lub struktury lub tablic, które można rozszerzyć do właściwości, które mają odpowiednie konwertery. Aby uzyskać listę konwerterów, zobacz <xref:System.ComponentModel> przestrzeni nazw.  
  
6.  Skompiluj projekt i Rozpocznij debugowanie.  
  
7.  W eksperymentalne wystąpienie programu Visual Studio na **narzędzia** kliknij menu **opcje**.  
  
     W okienku po lewej stronie powinna zostać wyświetlona **Moje kategorii**. (Opcje kategorie są wymienione w kolejności alfabetycznej, powinien pojawiać się o połowie listę w dół.) Otwórz **Moje kategorii** , a następnie kliknij przycisk **Moja strona siatki**. Opcje siatki zostanie wyświetlony w okienku po prawej stronie. Kategoria właściwości jest **Moje opcje**, i nazwa właściwości jest **Moje opcja całkowitą**. Opis właściwości **Moje opcja całkowitą**, pojawi się w dolnej części okienka. Zmień wartość ze swojej wartości początkowej 256 do innego elementu. Kliknij przycisk **OK**, a następnie ponownie otwórz **Moja strona siatki**. Widać, że nowa wartość będzie się utrzymywał.  
  
     Strony opcji jest również dostępny za pośrednictwem szybkiego uruchamiania programu Visual Studio. W oknie Szybkie uruchamianie w prawym górnym rogu IDE wpisz **Moje kategorii** i będzie wyświetlany **Moje kategorii -> Moja strona siatki** wyświetlane na liście rozwijanej.  
  
## <a name="creating-a-tools-options-custom-page"></a>Tworzenie niestandardowego narzędzia Opcje strony  
 W tej sekcji utworzysz strony Opcje narzędzi z niestandardowego interfejsu użytkownika. Ta strona służy do wyświetlania i zmieniania wartości właściwości.  
  
1.  Otwórz plik MyToolsOptionsPackage w edytorze kodu.  
  
2.  Dodaj następującą instrukcję using.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Dodaj `OptionPageCustom` klasy tuż przed `OptionPageGrid` klasy. Pochodzi od nowa klasa `DialogPage`.  
  
    ```csharp  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
4.  Dodaj atrybut GUID. Dodaj właściwość właściwości OptionString:  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
5.  Zastosuj drugiej <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do klasy pakiet VSPackage. Ten atrybut przypisuje klasy opcje kategorii i nazwy strony opcji.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    [ProvideOptionPage(typeof(OptionPageCustom),  
        "My Category", "My Custom Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
6.  Dodaj nową **kontrolki użytkownika** o nazwie MyUserControl do projektu.  
  
7.  Dodaj **pole tekstowe** formantu do kontrolki użytkownika.  
  
     W **właściwości** okna, na pasku narzędzi kliknij **zdarzenia** przycisk, a następnie kliknij dwukrotnie **pozostaw** zdarzeń. W kodzie MyUserControl.cs pojawi się nowy program obsługi zdarzeń.  
  
8.  Dodaj publiczny `OptionsPage` pola `Initialize` metodę do klasy formantu i aktualizacji programu obsługi zdarzeń, aby ustawić opcję wartości zawartości pola tekstowego:  
  
    ```csharp  
    public partial class MyUserControl : UserControl  
    {  
        public MyUserControl()  
        {  
            InitializeComponent();  
        }  
  
        internal OptionPageCustom optionsPage;  
  
        public void Initialize()  
        {  
            textBox1.Text = optionsPage.OptionString;  
        }  
  
        private void textBox1_Leave(object sender, EventArgs e)  
        {  
            optionsPage.OptionString = textBox1.Text;  
        }  
    }  
    ```  
  
     `optionsPage` Pole zawiera odwołanie do elementu nadrzędnego `OptionPageCustom` wystąpienia. `Initialize` Metoda Wyświetla `OptionString` w **pole tekstowe**. Program obsługi zdarzeń zapisuje bieżącą wartość **pole tekstowe** do `OptionString` po skupić się pozostawia **pole tekstowe**.  
  
9. W pliku kodu pakietu, Dodaj zastąpienie `OptionPageCustom.Window` właściwości do tworzenia, zainicjować i zwrócić wystąpienia klasy OptionPageCustom `MyUserControl`. Klasa powinna wyglądać następująco:  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
  
        protected override IWin32Window Window  
        {  
            get  
            {  
                MyUserControl page = new MyUserControl();  
                page.optionsPage = this;  
                page.Initialize();  
                return page;  
            }  
        }  
    }  
    ```  
  
10. Tworzenie i uruchamianie projektu.  
  
11. W eksperymentalnym wystąpieniu kliknij **narzędzia / Opcje**.  
  
12. Znajdź **Moje kategorii** , a następnie **Moje niestandardowe strony**.  
  
13. Zmień wartość **właściwości OptionString**. Kliknij przycisk **OK**, a następnie ponownie otwórz **Moje strony niestandardowego**. Widać, że utrwalił nową wartość.  
  
## <a name="accessing-options"></a>Dostęp do opcji  
 W tej sekcji można uzyskać wartość opcji od pakiet VSPackage, który obsługuje skojarzonej strony opcji narzędzi. Tę samą metodę można uzyskać wartości dowolnej właściwości publicznej.  
  
1.  W pliku kodu pakietu, Dodaj właściwości publicznej o nazwie **OptionInteger** do **MyToolsOptionsPackage** klasy.  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Ten kod wywołuje <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> do utworzenia lub pobrać `OptionPageGrid` wystąpienia. `OptionPageGrid`wywołania <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> załadować jego opcji, które są właściwości publiczne.  
  
2.  Teraz Dodaj szablon elementu polecenia niestandardowych o nazwie **MyToolsOptionsCommand** do wyświetlania wartości. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **polecenia niestandardowych**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby **MyToolsOptionsCommand.cs**.  
  
3.  W pliku MyToolsOptionsCommand, Zastąp treści polecenia `ShowMessageBox` metody z następujących czynności:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Skompiluj projekt i Rozpocznij debugowanie.  
  
5.  W eksperymentalnym wystąpieniu na **narzędzia** menu, kliknij przycisk **MyToolsOptionsCommand wywołania**.  
  
     Okno komunikatu Wyświetla bieżącą wartość `OptionInteger`.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje i opcje strony](../extensibility/internals/options-and-options-pages.md)