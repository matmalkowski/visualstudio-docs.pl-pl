---
title: "Aktualizowanie dostosowań Wstążki w projektach pakietu Office, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
ms.assetid: 3b7c8ad4-a616-4b42-9d62-9658fdefe6a3
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d2c7dfef925ff61255e57315a3980fa6a145c235
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualizowanie dostosowań wstążki w projektach związanych z pakietem Office przenoszonych do oprogramowania .NET Framework w wersji 4 lub 4.5
  Jeśli projekt zawiera dostosowania wstążki, który został utworzony przy użyciu **wstążki (projektanta wizualnego)** elementu projektu, należy wprowadzić następujące zmiany w kodzie projektu zmiana platformy docelowej na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później.  
  
-   Zmodyfikuj wygenerowanego kodu wstążki.  
  
-   Modyfikowanie kodu, który tworzy formantów wstążki w czasie wykonywania, obsługuje zdarzenia Wstążki lub programowo Ustawia położenie składnika wstążki.  
  
## <a name="updating-the-generated-ribbon-code"></a>Aktualizowanie kodu wygenerowanego wstążki  
 Jeśli platforma docelowa projektu jest zmieniana na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy zmienić wygenerowany kod dla elementu wstążki, wykonując następujące czynności. Pliki kodu, który należy zaktualizować zależą od język programowania i sposobu tworzenia projektu:  
  
-   Projekty Visual Basic lub Visual C# projektów, które zostały utworzone w jednym [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] lub [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] wykonaj wszystkie kroki przedstawione w pliku CodeBehind wstążki (*YourRibbonItem*. Designer.cs narzędzie lub *YourRibbonItem*. Designer.VB). Aby wyświetlić plik CodeBehind w projektach Visual Basic, kliknij przycisk **Pokaż wszystkie pliki** przycisk **Eksploratora rozwiązań**.  
  
-   W projektach Visual C#, które są tworzone w programie Visual Studio 2008, a następnie uaktualnienia do [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], wykonać pierwsze dwa kroki w pliku kodu wstążki (*YourRibbonItem*.cs lub *YourRibbonItem*.vb), a Wykonaj pozostałe kroki w pliku związanym z kodem wstążki.  
  
#### <a name="to-change-the-generated-ribbon-code"></a>Aby zmienić wygenerowanego kodu wstążki  
  
1.  Zmodyfikuj deklaracja klasy wstążki, tak aby dziedziczy <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> zamiast Microsoft.Office.Tools.Ribbon.OfficeRibbon.  
  
2.  Zmodyfikuj konstruktora klasy wstążki, jak pokazano poniżej. Jeśli dodano własne kodu do konstruktora, nie należy zmieniać swój kod. W projektach Visual Basic zmodyfikuj konstruktora bez parametrów. Ignoruj innego konstruktora.  
  
     Poniższy przykład kodu pokazuje domyślnego konstruktora klasy wstążki w projekcie, którego element docelowy .NET Framework 3.5.  
  
    ```vb  
    Public Sub New()  
        MyBase.New()  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
    {  
        InitializeComponent();  
    }  
    ```  
  
     Poniższy przykład kodu pokazuje domyślnego konstruktora klasy wstążki w projektach którego element docelowy [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym.  
  
    ```vb  
    Public Sub New()  
        MyBase.New(Globals.Factory.GetRibbonFactory())  
        InitializeComponent()  
    End Sub  
    ```  
  
    ```csharp  
    public Ribbon1()  
        : base(Globals.Factory.GetRibbonFactory())  
    {  
        InitializeComponent();  
    }  
    ```  
  
3.  W `InitializeComponent` metody zmodyfikować każdy kod, który konstruuje formantu wstążki, dzięki czemu kod zamiast niego użyto jednego z metody pomocnika <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiektu.  
  
    > [!NOTE]  
    >  W projektach Visual C#, należy rozwinąć obszaru o nazwie `Component Designer generated code` wyświetlić `InitializeComponent` metody.  
  
     Załóżmy na przykład, że plik zawiera następujący wiersz kodu, który tworzy <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> o nazwie `button1` w projekcie, przeznaczonego dla programu .NET Framework 3.5.  
  
    ```vb  
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();  
    ```  
  
     W projekcie, którego celem [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, zamiast tego należy użyć następującego kodu.  
  
    ```vb  
    Me.button1 = Me.Factory.CreateRibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = this.Factory.CreateRibbonButton();  
    ```  
  
     Aby zapoznać się z pełną listą metody pomocnicze dla formantów wstążki, zobacz [uruchamianiu formantów wstążki](#ribboncontrols).  
  
4.  Projekty Visual C#, zmodyfikuj każdym wierszu kodu w `InitializeComponent` metody, która używa <xref:System.EventHandler%601> pełnomocnika, aby zamiast tego użyj określonego delegata wstążki.  
  
     Załóżmy na przykład, że plik zawiera następujący wiersz kodu, który obsługuje <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> zdarzeń w projekcie, przeznaczonego dla programu .NET Framework 3.5.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
     W projekcie, którego celem [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, zamiast tego należy użyć następującego kodu.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
     Aby uzyskać pełną listę obiektów delegowanych wstążki, zobacz [obsługi zdarzeń wstążki](#ribbonevents).  
  
5.  Projekty Visual Basic, odszukaj `ThisRibbonCollection` klasy na końcu pliku. Deklaracja tej klasy należy zmodyfikować, tak aby nie będzie już dziedziczyć z Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection.  
  
##  <a name="ribboncontrols"></a>Tworzenie wystąpień formantów wstążki  
 Należy zmodyfikować każdy kod dynamicznie tworzy formantów wstążki. W projektach przeznaczonych programu .NET Framework 3.5, formantów wstążki są klasy, które można utworzyć wystąpienie bezpośrednio w niektórych scenariuszach. W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, tych kontrolek interfejsów, które nie można utworzyć wystąpienia bezpośrednio. Formanty należy utworzyć przy użyciu metod, które są udostępniane przez <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiektu.  
  
 Istnieją dwa sposoby <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiektu:  
  
-   Za pomocą właściwości fabryki klasy wstążki. Użyj podejścia z kodu w klasie wstążki.  
  
-   Przy użyciu metody Globals.Factory.GetRibbonFactory. Użyj podejścia do kodu spoza klasy wstążki. Aby uzyskać więcej informacji na temat klasy globalne, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> w klasie wstążki w projekcie, którego celem [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 W poniższej tabeli wymieniono formanty można tworzyć programowo i metodę używaną do tworzenia kontrolek w projektach przeznaczonych do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym.  
  
|Formant|RibbonFactory metodę używaną do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i nowszym projektów|  
|-------------|---------------------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|  
  
##  <a name="ribbonevents"></a>Obsługa zdarzeń wstążki  
 Należy zmodyfikować każdy kod obsługujący zdarzenia formantów wstążki. W projektach przeznaczonych dla programu .NET Framework 3.5, te zdarzenia są obsługiwane przez ogólnego <xref:System.EventHandler%601> delegowanie. W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te zdarzenia są teraz obsługiwane przez inne delegatów.  
  
 W poniższej tabeli wymieniono zdarzenia Wstążki i obiektów delegowanych, które są skojarzone z nimi w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym.  
  
|Zdarzenie|Delegat do użycia w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i nowszym projektów|  
|-----------|---------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>zdarzenia w klasie wygenerowanego wstążki|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|  
  
## <a name="setting-the-position-of-a-ribbon-component-programmatically"></a>Programowo ustawienie pozycji składnika wstążki  
 Należy zmodyfikować każdy kod ustawia położenie grup, karty lub formantów wstążki. W projektach przeznaczonych programu .NET Framework 3.5, służy AfterOfficeId i BeforeOfficeId metody statycznej klasy Microsoft.Office.Tools.Ribbon.RibbonPosition można przypisać właściwości Position grupy, karty lub formantu. W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy uruchomić przy użyciu tych metod <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> właściwości udostępniane przez <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiektu.  
  
 Istnieją dwa sposoby <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> obiektu:  
  
-   Za pomocą właściwości fabryki klasy wstążki. Użyj podejścia z kodu w klasie wstążki.  
  
-   Przy użyciu metody Globals.Factory.GetRibbonFactory. Użyj podejścia do kodu spoza klasy wstążki. Aby uzyskać więcej informacji na temat klasy globalne, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 Poniższy przykład kodu pokazuje sposób ustawiania właściwości Position karty w klasie wstążki w projektach, którego element docelowy .NET Framework 3.5.  
  
```vb  
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");  
```  
  
 W poniższym przykładzie kodu pokazano tego samego zadania w projekcie, którego celem jest [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
```vb  
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)  
  
  