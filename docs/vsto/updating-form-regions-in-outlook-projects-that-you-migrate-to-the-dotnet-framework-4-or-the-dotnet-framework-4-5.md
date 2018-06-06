---
title: Aktualizowanie regionów formularzy w projektach programu Outlook, których można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97778716ad5be8e110c022048a3d04f4c980f839
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767978"
---
# <a name="update-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualizowanie regionów formularzy w projektach programu Outlook, których można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5
  Zmiana platformy docelowej projektu dodatku VSTO dla programu Outlook z regionu formularza do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy wprowadzić kilka zmian kodu regionu generowanym formularzu i kodu, który tworzy niektórych klas regionu formularza w czasie wykonywania.  
  
## <a name="update-the-generated-form-region-code"></a>Zaktualizuj kod regionu generowanym formularzu  
 Jeśli platforma docelowa projektu jest zmieniana na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy zmienić kod regionu generowanym formularzu. Wprowadzone zmiany są różne dla regionów formularzy, które zaprojektowane w Visual Studio i formularza regionach, które są importowane z programu Outlook. Aby uzyskać więcej informacji na temat różnic między tymi typami regionów formularzy, zobacz [regionów formularzy Outlook utwórz](../vsto/creating-outlook-form-regions.md).  
  
### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Aby zaktualizować wygenerowany kod dla regionów formularzy zaprojektowanych w programie Visual Studio  
  
1.  Otwórz plik CodeBehind regionu formularza w edytorze kodu. Ten plik ma nazwę *YourFormRegion*. Designer.cs narzędzie lub *YourFormRegion*. Designer.VB. Aby wyświetlić ten plik w projektach Visual Basic, kliknij przycisk **Pokaż wszystkie pliki** przycisk **Eksploratora rozwiązań**.  
  
2.  Zmodyfikuj deklaracja klasy regionu formularza tak, aby dziedziczy <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> zamiast `Microsoft.Office.Tools.Outlook.FormRegionControl`.  
  
3.  Zmodyfikuj konstruktora klasy regionu formularza, jak pokazano w poniższych przykładach kodu.  
  
     Poniższy przykład kodu pokazuje konstruktora klasy regionu formularza w projekcie, którego element docelowy .NET Framework 3.5.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
     Poniższy przykład kodu pokazuje konstruktora klasy regionu formularza w projekcie którego element docelowy [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
        Me.InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.InitializeComponent();  
    }  
    ```  
  
4.  Modyfikowanie podpis `InitializeManifest` metody, jak pokazano poniżej. Upewnij się, że nie należy modyfikować kod w metodzie; Ten kod reprezentuje ustawienia regionu formularza, które stosowane w projektancie. W projektach Visual C#, należy rozwinąć obszaru o nazwie `Form Region Designer generated code` wyświetlić tę metodę.  
  
     Poniższy przykład kodu pokazuje podpis `InitializeManifest` metody w projekcie, przeznaczonego dla programu .NET Framework 3.5.  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
     Poniższy przykład kodu pokazuje podpis `InitializeManifest` w projekcie, którego celem metody [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,   
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)  
  
        ' Do not change code in this method.  
    End Sub  
    ```  
  
    ```csharp  
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,   
        Microsoft.Office.Tools.Outlook.Factory factory)  
    {  
        // Do not change code in this method.  
    }  
    ```  
  
5.  Dodaj nowy element regionów formularzy programu Outlook do projektu. Otwórz plik CodeBehind dla nowego regionu formularza, odszukaj *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` klasy w pliku i skopiuj te klasy do Schowka.  
  
6.  Usuń nowego regionu formularza, dodane do projektu.  
  
7.  W pliku CodeBehind aktualizowanego działa w projekcie retargeted regionu formularza, Znajdź *YourOriginalFormRegion* `Factory` i `WindowFormRegionCollection` klas i zastąp je z kodem, które zostały skopiowane z nowe regionu formularza.  
  
8.  W *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` klasy, wyszukaj wszystkie odwołania do *YourNewFormRegion* klasy i zmienić każde odwołanie do  *YourOriginalFormRegion* zamiast klasy. Na przykład, jeśli aktualizowanie regionów formularzy nosi nazwę `SalesDataFormRegion` i nosi nazwę nowego regionu formularza utworzonego w kroku 5 `FormRegion1`, zmień wszystkich odwołań `FormRegion1` do `SalesDataFormRegion`.  
  
#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Aby zaktualizować wygenerowany kod dla regionu formularza, które są importowane z programu Outlook  
  
1.  Otwórz plik CodeBehind regionu formularza w edytorze kodu. Ten plik ma nazwę *YourFormRegion*. Designer.cs narzędzie lub *YourFormRegion*. Designer.VB. Aby wyświetlić ten plik w projektach Visual Basic, kliknij przycisk **Pokaż wszystkie pliki** przycisk **Eksploratora rozwiązań**.  
  
2.  Zmodyfikuj deklaracja klasy regionu formularza tak, aby dziedziczy <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> zamiast `Microsoft.Office.Tools.Outlook.ImportedFormRegion`.  
  
3.  Zmodyfikuj konstruktora klasy regionu formularza, jak pokazano w poniższych przykładach kodu.  
  
     Poniższy przykład kodu pokazuje konstruktora klasy regionu formularza w projekcie, którego element docelowy .NET Framework 3.5.  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
     Poniższy przykład kodu pokazuje podpisu konstruktora klasy regionu formularza w projekcie którego element docelowy [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
    ```vb  
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)  
        MyBase.New(Globals.Factory, formRegion)  
    End Sub  
    ```  
  
    ```csharp  
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)  
        : base(Globals.Factory, formRegion)  
    {  
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);  
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);  
    }  
    ```  
  
4.  Dla każdego wiersza kodu w `InitializeControls` metodę, która inicjuje kontrolkę w klasie regionu formularza, należy zmodyfikować kod, jak pokazano poniżej.  
  
     Poniższy przykład kodu pokazuje, jak zainicjować formantu w projekcie którego element docelowy .NET Framework 3.5. W tym kodzie `GetFormRegionControl` metoda ma parametr typu, który określa typ formantu, który jest zwracany.  
  
    ```vb  
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")  
    ```  
  
    ```csharp  
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");  
    ```  
  
     Poniższy przykładowy kod przedstawia sposób zainicjować formantu w projekcie, którego element docelowy [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. W tym kodzie <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> metoda nie ma parametru typu. Należy rzutować wartości zwracanej typu formantu, który jest inicjowania.  
  
    ```vb  
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)  
    ```  
  
    ```csharp  
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");  
    ```  
  
5.  Dodaj nowy element regionów formularzy programu Outlook do projektu. Otwórz plik CodeBehind dla nowego regionu formularza, odszukaj *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` klasy w pliku i skopiuj te klasy do Schowka.  
  
6.  Usuń nowego regionu formularza, dodane do projektu.  
  
7.  W pliku CodeBehind aktualizowanego działa w projekcie retargeted regionu formularza, Znajdź *YourOriginalFormRegion* `Factory` i `WindowFormRegionCollection` klas i zastąp je z kodem, które zostały skopiowane z nowe regionu formularza.  
  
8.  W *YourNewFormRegion* `Factory` i `WindowFormRegionCollection` klasy, wyszukaj wszystkie odwołania do *YourNewFormRegion* klasy i zmienić każde odwołanie do  *YourOriginalFormRegion* zamiast klasy. Na przykład, jeśli aktualizowanie regionów formularzy nosi nazwę `SalesDataFormRegion` i nosi nazwę nowego regionu formularza utworzonego w kroku 5 `FormRegion1`, zmień wszystkich odwołań `FormRegion1` do `SalesDataFormRegion`.  
  
## <a name="instantiate-form-region-classes"></a>Utworzenie wystąpienia klasy regionu formularza  
 Należy zmodyfikować każdy kod dynamicznie tworzy niektórych klas regionu formularza. W projektach przeznaczonych dla programu .NET Framework 3.5, można utworzyć wystąpienie klasy regionu formularza takie jak `Microsoft.Office.Tools.Outlook.FormRegionManifest` bezpośrednio. W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, te klasy są interfejsy, które nie można utworzyć wystąpienia bezpośrednio.  
  
 Jeśli platforma docelowa projektu jest zmieniana na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, trzeba utworzyć wystąpienie interfejsy przy użyciu metod, które są udostępniane przez `Globals.Factory` właściwości. Aby uzyskać więcej informacji na temat `Globals.Factory` właściwości, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 W poniższej tabeli przedstawiono typy regionu formularza i metody służące do tworzenia wystąpienia typu projektów przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym.  
  
|Typ|Metoda fabryki do użycia|  
|----------|---------------------------|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|  
  
## <a name="see-also"></a>Zobacz także  
 [Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)  
  