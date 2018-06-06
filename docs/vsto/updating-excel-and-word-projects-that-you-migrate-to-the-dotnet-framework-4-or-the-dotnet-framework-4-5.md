---
title: Aktualizacja programu Excel i Word projektów, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5
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
ms.openlocfilehash: 38734366f5b7d19ef0780c8ef998efb19e50a46f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767533"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualizacja programu Excel i Word projektów, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5
  Jeśli masz projektu programu Excel lub Word, która używa dowolnej z następujących funkcji, należy zmodyfikować kod zmiana platformy docelowej na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy:  
  
-   [GetVstoObject i HasVstoObject metody](#GetVstoObject)  
  
-   [Wygenerowane klasy w projektach na poziomie dokumentu](#generatedclasses)  
  
-   [Formanty formularzy systemu Windows w dokumentach](#winforms)  
  
-   [Zdarzenia formantów zawartości programu Word](#ccevents)  
  
-   [Klasy OLEObject i OLEControl](#ole)  
  
-   [Właściwość Controls.Item(Object)](#itemproperty)  
  
-   [Kolekcje, które pochodzą z CollectionBase](#collections)  
  
 Należy również usunąć `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` i odwołuje się do `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` klasy z projekty programu Excel, które są przekierować do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym. Program Visual Studio nie powoduje usunięcia tego atrybutu lub odwołania do klasy dla Ciebie.  
  
## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Usuń atrybut ExcelLocale1033 z projekty programu Excel  
 `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` Został usunięty z programu Visual Studio 2010 Tools dla pakietu Office runtime, służący do rozwiązania, które odnoszą się do części [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym. Środowisko uruchomieniowe języka wspólnego (CLR) w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i później zawsze przekazuje ustawień regionalnych 1033 Identyfikatora modelu obiektów programu Excel, a nie będzie można użyć tego atrybutu Aby wyłączyć to zachowanie. Aby uzyskać więcej informacji, zobacz [globalizacja i lokalizacja rozwiązania programu Excel](../vsto/globalization-and-localization-of-excel-solutions.md).  
  
### <a name="to-remove-the-excellocale1033attribute"></a>Aby usunąć ExcelLocale1033Attribute  
  
1.  Otwórz projekt w programie Visual Studio Otwórz **Eksploratora rozwiązań**.  
  
2.  W obszarze **właściwości** węzeł (C#) lub **mój projekt** węzeł (Visual Basic), kliknij dwukrotnie plik kodu AssemblyInfo, aby otworzyć go w edytorze kodu.  
  
    > [!NOTE]  
    >  W projektach Visual Basic, należy kliknąć opcję **Pokaż wszystkie pliki** przycisk **Eksploratora rozwiązań** do znajduje się w pliku kodu AssemblyInfo.  
  
3.  Zlokalizuj `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` i usuń go z pliku lub go komentarz.  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Usuń odwołanie do klasy ExcelLocal1033Proxy  
 Projekty, które zostały utworzone przy użyciu programu Microsoft Visual Studio 2005 Tools dla pakietu Microsoft Office System wystąpienia programu Excel <xref:Microsoft.Office.Interop.Excel.Application> obiektu przy użyciu `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` klasy. Ta klasa została usunięta z części Visual Studio 2010 Tools dla pakietu Office runtime, który został użyty do rozwiązania kierowanych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym. W związku z tym należy usunąć lub w komentarz wiersz kodu, który odwołuje się do tej klasy.  
  
### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Aby usunąć odwołania do klasy ExcelLocal1033Proxy  
  
1.  Otwórz projekt w programie Visual Studio, a następnie otwórz **Eksploratora rozwiązań**.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów *ThisAddin.cs* (dla C#) lub *ThisAddin.vb* (w języku Visual Basic), a następnie wybierz pozycję **kod widoku**.  
  
3.  W edytorze kodu w `VSTO generated code` regionu, usuń lub komentarz następujący wiersz kodu.  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a> Zaktualizuj kod, który używa metody GetVstoObject i HasVstoObject  
 W projektach przeznaczonych dla programu .NET Framework 3.5 `GetVstoObject` lub `HasVstoObject` metody są dostępne jako metody rozszerzenia na jednym z następujących obiektów macierzystych w projekcie: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, lub <xref:Microsoft.Office.Interop.Excel.ListObject>. Po wywołaniu metody, nie trzeba przekazać parametr. Poniższy przykład kodu pokazuje, jak użyć tej metody GetVstoObject w dodatku VSTO programu Word, przeznaczonego dla programu .NET Framework 3.5.  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument =   
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy zmodyfikować swój kod, aby dostęp do tych metod w jednym z następujących sposobów:  
  
-   Możesz mogą nadal uzyskiwać dostęp do tych metod jako metody rozszerzenia <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, lub <xref:Microsoft.Office.Interop.Excel.ListObject> obiektów. Jednak teraz musi przekazać obiektu zwróconego przez `Globals.Factory` właściwości do tych metod.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
    ```  
  
-   Alternatywnie dostęp do tych metod dla obiektu, który jest zwracany przez `Globals.Factory` właściwości. Gdy uzyskujesz dostęp do tych metod w ten sposób, trzeba przekazać obiekt natywny, który ma zostać rozszerzony do metody.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
    ```  
  
 Aby uzyskać więcej informacji, zobacz [dokumentów rozszerzania programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
##  <a name="generatedclasses"></a> Zaktualizuj kod, który używa wystąpienia wygenerowanych klas w projektach na poziomie dokumentu  
 W przypadku projektów na poziomie dokumentu przeznaczonych dla programu .NET Framework 3.5, wygenerowane klasy w projektach pochodzi od następujące klasy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, typów w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wymienionych powyżej są interfejsy, zamiast klasy. Wygenerowanej klasy w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później pochodzi od następujące nowe klasy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
 Jeśli kod w projekcie odwołuje się do wystąpienia jednego z wygenerowane klasy jako klasy podstawowej, która dziedziczy, należy zmodyfikować kod.  
  
 Na przykład w projekcie skoroszytu programu Excel, przeznaczonego dla programu .NET Framework 3.5, może być metodę pomocnika, którą wykonuje dodatkowych czynności w wystąpieniach wygenerowany `Sheet` *n* klas w projekcie.  
  
```vb  
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)  
    ' Do something to the worksheet object.  
End Sub  
```  
  
```csharp  
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)  
{  
    // Do something to the worksheet object.  
}  
```  
  
 Jeśli przekierowanie projektu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, należy jedną z następujących zmian w kodzie:  
  
-   Zmodyfikować każdy kod wywołujący `DoSomethingToSheet` można przekazać <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> właściwość <xref:Microsoft.Office.Tools.Excel.WorksheetBase> obiektu w projekcie. Ta właściwość zwraca <xref:Microsoft.Office.Tools.Excel.Worksheet> obiektu.  
  
    ```vb  
    DoSomethingToSheet(Globals.Sheet1.Base)  
    ```  
  
    ```csharp  
    DoSomethingToSheet(Globals.Sheet1.Base);  
    ```  
  
-   Modyfikowanie `DoSomethingToSheet` parametru metody oczekiwać <xref:Microsoft.Office.Tools.Excel.WorksheetBase> zamiast tego obiektu.  
  
    ```vb  
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)  
        ' Do something to the worksheet object.  
    End Sub  
    ```  
  
    ```csharp  
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)  
    {  
        // Do something to the worksheet object.  
    }  
    ```  
  
##  <a name="winforms"></a> Zaktualizuj kod, który używa formanty formularzy systemu Windows w dokumentach  
 Należy dodać **przy użyciu** (C#) lub **importów** — instrukcja (Visual Basic) dla <xref:Microsoft.Office.Tools.Excel> lub <xref:Microsoft.Office.Tools.Word> przestrzeni nazw na początku każdego pliku kodu, który używa właściwości kontrolki, aby dodawać formularzy systemu Windows formanty w dokumencie lub arkusz programowo.  
  
 W projektach przeznaczonych dla platformy .NET Framework 3.5, Dodaj formanty formularzy systemu Windows metody (takie jak `AddButton` metody) są zdefiniowane w <xref:Microsoft.Office.Tools.Excel.ControlCollection> i <xref:Microsoft.Office.Tools.Word.ControlCollection> klasy.  
  
 W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te metody są metody rozszerzenia, które są dostępne dla właściwości formantów. Aby korzystać z tych metod rozszerzenia, musi mieć pliku kodu, w którym możesz użyć metod **przy użyciu** lub **importów** instrukcji dla <xref:Microsoft.Office.Tools.Excel> lub <xref:Microsoft.Office.Tools.Word> przestrzeni nazw. Ta instrukcja jest generowany automatycznie w nowych projektach, które odnoszą się do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym. Jednak ta instrukcja nie jest automatycznie dodawane w projektach przeznaczonych .NET Framework 3.5, gdy Przekieruj projektu należy go dodać.  
  
 Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="ccevents"></a> Zaktualizuj kod obsługujący zdarzenia formantów zawartości programu Word  
 W projektach przeznaczonych dla programu .NET Framework 3.5, zdarzenia Word formanty zawartości są obsługiwane przez ogólnego <xref:System.EventHandler%601> delegowanie. W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te zdarzenia są obsługiwane przez inne obiekty delegowane.  
  
 W poniższej tabeli wymieniono zdarzenia formantu zawartości programu Word i obiektów delegowanych, które są skojarzone z nimi w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym.  
  
|Zdarzenie|Delegat do użycia w [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i nowszym projektów|  
|-----------|---------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a> Zaktualizuj kod, który korzysta z klas OLEObject i OLEControl  
 W projektach przeznaczonych dla programu .NET Framework 3.5, można dodać kontrolki niestandardowe (takie jak kontrolki użytkownika formularzy systemu Windows) w dokumencie lub arkusz za pomocą `Microsoft.Office.Tools.Excel.OLEObject` i `Microsoft.Office.Tools.Word.OLEControl` klasy.  
  
 W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te klasy zostały zastąpione przez <xref:Microsoft.Office.Tools.Excel.ControlSite> i <xref:Microsoft.Office.Tools.Word.ControlSite> interfejsów. Należy zmodyfikować kod, który odwołuje się do `Microsoft.Office.Tools.Excel.OLEObject` i `Microsoft.Office.Tools.Word.OLEControl` do zamiast odwoływania się do <xref:Microsoft.Office.Tools.Excel.ControlSite> i <xref:Microsoft.Office.Tools.Word.ControlSite>. Inne niż nowe nazwy tych kontrolek zachowują się tak samo jak w projektach przeznaczonych dla programu .NET Framework 3.5.  
  
 Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="itemproperty"></a> Zaktualizuj kod, który używa właściwości Controls.Item(Object)  
 W projektach przeznaczonych dla programu .NET Framework 3.5, można użyć właściwości Item(Object) Microsoft.Office.Tools.Word.Document.Controls lub `Microsoft.Office.Tools.Excel.Worksheet.Controls` kolekcję, aby określić, czy dokument lub arkusz określonego formantu.  
  
 W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, właściwość Item(Object) został usunięty z tych kolekcji. Aby ustalić, czy dokument lub arkusz zawiera określonego formantu, należy użyć metody Contains(System.Object) <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> lub <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> kolekcji zamiast tego.  
  
 Aby uzyskać więcej informacji na temat kolekcji formantów dokumentów i arkuszy, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="collections"></a> Zaktualizuj kod, który używa kolekcje, które pochodzą z CollectionBase  
 W projektach przeznaczonych dla programu .NET Framework 3.5, kolekcji kilka typów w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pochodzi od <xref:System.Collections.CollectionBase> klas, takich jak `Microsoft.Office.Tools.SmartTagCollection`, `Microsoft.Office.Tools.Excel.ControlCollection`, i `Microsoft.Office.Tools.Word.ControlCollection`.  
  
 W projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, te typy kolekcji są teraz interfejsów, które nie pochodzą z <xref:System.Collections.CollectionBase>. Niektóre elementy nie są już dostępne dla tych typów kolekcji, takie jak <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>, i <xref:System.Collections.CollectionBase.InnerList%2A>.  
  
## <a name="see-also"></a>Zobacz także  
 [Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Formanty zawartości](../vsto/content-controls.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  