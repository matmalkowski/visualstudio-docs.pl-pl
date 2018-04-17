---
title: Formanty zawartości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.DropDownListContentControl
- VST.Toolbox.RichTextContentControl
- VST.Toolbox.PlainTextContentControl
- VST.Toolbox.ComboBoxContentControl
- VST.Toolbox.CCBuildingBlockGalleryContentControl
- VST.Toolbox.DatePickerContentControl
- VST.Toolbox.PictureContentControl
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document building blocks [Office development in Visual Studio]
- restricted permissions [Office development in Visual Studio]
- ComboBoxContentControl class
- PictureContentControl class
- PlainTextContentControl class
- Office documents [Office development in Visual Studio], restricted permissions
- RichTextContentControl class
- content controls [Office development in Visual Studio]
- building block gallery [Office development in Visual Studio]
- controls [Office development in Visual Studio], content controls
- GroupContentControl class
- documents [Office development in Visual Studio], restricted permissions
- DropDownListContentControl class
- DatePickerContentControl class
- data binding [Office development in Visual Studio], content controls
- content controls [Office development in Visual Studio], about content controls
- custom XML parts, content controls
- templates [Office development in Visual Studio], content controls
- BuildingBlockGalleryContentControl class
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a1c56b7e48ce42699330e8eb40595d9cc761736e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="content-controls"></a>Formanty zawartości
  Formanty zawartości umożliwiają Ci dokumentów projektowych i szablony, które mają następujące funkcje:  
  
-   Interfejs użytkownika (UI), który jest kontrolowany danych wejściowych, np.  
  
-   Ograniczenia, które uniemożliwiają użytkownikom edytowanie sekcje chronionego dokumentu lub szablonu. Aby uzyskać więcej informacji, zobacz [ochrona części dokumentów za pomocą formantów zawartości](#Protection).  
  
-   Wiązanie danych do źródła danych. Aby uzyskać więcej informacji, zobacz [wiązanie danych z formantami zawartości](#DataBinding).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [wiązanie danych do programu Word 2007 zawartość kontrolki Using Visual Studio Tools for Office System (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## <a name="overview-of-content-controls"></a>Omówienie formantów zawartości  
 Formanty zawartości umożliwiają interfejsu użytkownika, który jest zoptymalizowany zarówno użytkownika wejściowych i drukowania. Po dodaniu formantu zawartości w dokumencie formantu jest identyfikowany przez obramowanie, tytuł i tymczasowego tekst, który można dołączyć instrukcje dla użytkownika. Obramowania i tytuł formantu nie ma w drukowanej wersji dokumentu.  
  
 Na przykład jeśli chcesz, aby użytkownik musi wprowadzić datę w sekcji dokumentu, można dodać zawartości formant wyboru daty do dokumentu. Po kliknięciu formantu, zostanie wyświetlony selektor standardowy format daty interfejsu użytkownika. Można również ustawić właściwości formantu, aby ustawić regionalnych kalendarza, która jest wyświetlana i określić format daty. Po wybraniu typu date formantu interfejsu użytkownika jest ukryty, a tylko data jest wyświetlana, jeśli użytkownik drukuje dokument.  
  
 Kontrola zawartości również należy wykonać następujące czynności:  
  
-   Uniemożliwić użytkownikom edytowanie lub usuwanie części dokumentu. Jest to przydatne, jeśli masz informacji w dokumencie lub szablonu, który użytkownicy powinni być w stanie odczytywać, ale nie edytować, lub jeśli chcesz, aby użytkownicy mogli edytować formantów zawartości, ale nie ich usuwać.  
  
-   Części dokumentu lub szablonu można powiązać z danymi. Formanty zawartości można powiązać pola bazy danych, zarządzanych obiektów w [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)], elementy XML, które są przechowywane w dokumencie i innych źródeł danych.  
  
 W projektach na poziomie dokumentu możesz dodać formantów zawartości do dokumentu w czasie projektowania lub w czasie wykonywania. W dodatku VSTO projekty można dodawanie formantów zawartości do otwartego dokumentu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
> [!NOTE]  
>  Formanty zawartości można użyć tylko w przypadku dokumentów, które są zapisane w formacie Open XML. Formanty zawartości nie można użyć w dokumentach, które są zapisane w formacie programu Word 97-2003 (doc).  
  
## <a name="types-of-content-controls"></a>Typy formantów  
 Brak dziewięć różne typy formantów zawartości, które można dodać do dokumentów. Większość formantów zawartości ma odpowiedniego typu w <xref:Microsoft.Office.Tools.Word> przestrzeni nazw. Można również użyć ogólnego <xref:Microsoft.Office.Tools.Word.ContentControl>, które można odpowiada żadnemu z dostępnych formantów zawartości. Aby uzyskać wskazówki, które pokazuje, jak używać każdego z dostępnych formantów zawartości, zobacz [wskazówki: Tworzenie szablonu przez przy użyciu zawartość formantów](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
### <a name="building-block-gallery"></a>Galeria bloków konstrukcyjnych  
 Galeria modułów konstrukcyjnych umożliwia użytkownikom wybór z listy *bloki konstrukcyjne dokumentu* do wstawienia do dokumentu. Bloku konstrukcyjnego dokumentu jest zawartość, który został utworzony w celu można użyć wielokrotnie, takich jak typowych stron tytułowych, sformatowanej tabeli lub nagłówek. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> typu. Aby uzyskać więcej informacji na temat bloki konstrukcyjne, zobacz [What's New dla deweloperów w programie Word 2007](http://msdn.microsoft.com/en-us/74aa6688-65b3-4167-997d-131f26ad8f84).  
  
### <a name="check-box"></a>Pole wyboru  
 Pole wyboru udostępnia interfejs użytkownika, który reprezentuje stan binarny: zaznaczone lub wyczyszczone.  
  
 W przeciwieństwie do innych typów zawartości kontrolki [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nie zawiera określonego typu, który reprezentuje kontrolkę pola wyboru zawartości. Innymi słowy nie ma typu CheckBoxContentControl. Jednakże, nadal można utworzyć formantu zawartości pola wyboru przez dodanie ogólnego <xref:Microsoft.Office.Tools.Word.ContentControl> do dokumentu programowo. Aby uzyskać więcej informacji, zobacz [zawartości formanty pól wyboru w projekty programu Word](#checkbox).  
  
### <a name="combo-box"></a>pole kombi  
 Pole kombi Wyświetla listę elementów, które użytkownicy mogą wybrać. W przeciwieństwie do listy rozwijanej pola kombi umożliwia użytkownikom dodawać własne elementy. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> typu.  
  
### <a name="date-picker"></a>Wybór daty  
 Wybór daty zawiera kalendarz interfejsu użytkownika dla wybranej daty. Kalendarza jest wyświetlany, gdy użytkownik kliknie strzałkę listy rozwijanej w formancie. Można użyć regionalnych kalendarzy i formaty inną datę. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> typu.  
  
### <a name="drop-down-list"></a>Lista rozwijana  
 Listy rozwijanej Wyświetla listę elementów, które użytkownicy mogą wybrać. W przeciwieństwie do pola kombi listy rozwijanej nie zezwala użytkownikom na dodawanie lub edytowanie elementów. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> typu.  
  
### <a name="group"></a>Grupa  
 Formant grupy definiuje obszar chronionego dokumentu, który użytkownicy nie można edytować ani usunąć. Formant grupa może zawierać żadnych elementów dokumentu, takich jak tekstu, tabel, grafiki i inne formanty zawartości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.GroupContentControl> typu.  
  
### <a name="picture"></a>Obraz  
 Formant obrazu wyświetla obraz. Można określić obrazu w czasie projektowania lub czas wykonywania, lub kliknięcie tego formantu, aby wybrać obraz do wstawienia w dokumencie. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.PictureContentControl> typu.  
  
### <a name="rich-text"></a>Tekst sformatowany  
 Zawiera formant tekstu sformatowanego tekstu lub innych elementów, takich jak tabele, obrazy lub inne formanty zawartości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.RichTextContentControl> typu.  
  
### <a name="plain-text"></a>Zwykły tekst  
 Tekst zawiera formant zwykłego tekstu. Formant zwykłego tekstu nie może zawierać innych elementów, takich jak tabele, obrazy lub inne formanty zawartości. Ponadto cały tekst w formancie zwykły tekst ma tego samego formatowania. Na przykład jeśli powoduje zastosowanie kursywy o jedno słowo w zdania w formancie zwykłego tekstu, jest kursywą cały tekst wewnątrz formantu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> typu.  
  
### <a name="generic-content-control"></a>Ogólny formantu zawartości  
 Jest ogólny formantu zawartości <xref:Microsoft.Office.Tools.Word.ContentControl> obiekt, który można odpowiada żadnemu z dostępnych typów formantów zawartości. Możesz zmienić <xref:Microsoft.Office.Tools.Word.ContentControl> obiektu zachowanie przy użyciu innego typu zawartości formantu <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> właściwości. Na przykład w przypadku utworzenia <xref:Microsoft.Office.Tools.Word.ContentControl> obiekt, aby kontrolować jako zwykły tekst reprezentuje, można zmienić w czasie wykonywania, aby zachowuje się jak pole kombi.  
  
 Można utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiektów tylko w czasie wykonywania, a nie w czasie projektowania. Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
## <a name="common-features-of-content-controls"></a>Wspólne funkcje formanty zawartości  
 Formanty zawartości najbardziej udostępnianie zestaw elementów członkowskich, które służy do wykonywania typowych zadań. W poniższej tabeli opisano niektóre z zadań, które można wykonywać przy użyciu tych elementów członkowskich.  
  
|Dla tego zadania:|wykonaj następujące czynności:|  
|--------------------|--------------|  
|Pobrać lub ustawić tekst, który jest wyświetlany w formancie.|Użyj **tekst** właściwości. **Uwaga:** <xref:Microsoft.Office.Tools.Word.PictureContentControl> i <xref:Microsoft.Office.Tools.Word.ContentControl> typy nie mają tej właściwości.|  
|GET lub set tymczasowego tekst, który jest wyświetlany w formancie, dopóki użytkownik edytuje formantu, formantu jest wypełniane przy użyciu danych z źródła danych lub zawartość formantu zostanie usunięta.|Użyj **PlaceholderText** właściwości. **Uwaga:** <xref:Microsoft.Office.Tools.Word.PictureContentControl> typ nie zawiera tej właściwości.|  
|GET lub set tytuł, który jest wyświetlany w obramowania formantu zawartości po kliknięciu przez użytkownika.|Użyj **tytuł** właściwości.|  
|Usuwanie formantu z dokumentu automatycznie po użytkownik edytuje formantu. (Tekst w formancie pozostaje w dokumencie).|Użyj **tymczasowego** właściwości.|  
|Uruchamianie kodu, gdy użytkownik kliknie przycisk w formancie zawartości lub gdy kursor zostanie przeniesiony do zawartości kontrolki programowo.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> zdarzeń formantu.|  
|Uruchamianie kodu, gdy użytkownik kliknie poza kontrolą zawartości lub gdy kursor zostanie przesunięty poza kontrolą zawartości programowo.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> zdarzeń formantu.|  
|Uruchomienia kodu po zawartości formant został dodany do dokumentu w wyniku Powtórz lub cofnąć operacji.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> zdarzeń formantu.|  
|Uruchom kod bezpośrednio przed zawartości formantu zostanie usunięty z dokumentu.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> zdarzeń formantu.|  
  
##  <a name="Protection"></a> Ochrona części dokumentów za pomocą formantów zawartości  
 W przypadku ochrony części dokumentu, można uniemożliwić użytkownikom zmienianie lub usuwanie zawartości w tej części dokumentu. Istnieje kilka sposobów części dokumentu można chronić za pomocą formantów zawartości.  
  
 Jeśli obszar, który chcesz chronić znajduje się wewnątrz formantu zawartości, można użyć właściwości zawartości formantu, aby uniemożliwić użytkownikom edytowanie lub usuwanie formantu:  
  
-   **LockContents** właściwości uniemożliwia użytkownikom edytowania zawartości.  
  
-   **LockContentControl** właściwości uniemożliwia użytkownikom usuwanie formantu.  
  
 Jeśli obszar, który chcesz chronić, nie jest wewnątrz formantu zawartości lub jeśli chcesz chronić obszar, który zawiera formanty zawartości i innych typów zawartości, możesz umieścić cały obszar <xref:Microsoft.Office.Tools.Word.GroupContentControl>. W przeciwieństwie do innych formantów zawartości <xref:Microsoft.Office.Tools.Word.GroupContentControl> zapewnia bez interfejsu użytkownika, który jest widoczny dla użytkownika. Jej jedynym celem jest określenie region, który użytkownicy nie mogą edytować.  
  
> [!NOTE]  
>  W przypadku utworzenia <xref:Microsoft.Office.Tools.Word.GroupContentControl> zawiera osadzony formantów zawartości, osadzonych formantów zawartości nie są automatycznie chronione. Należy użyć **LockContents** właściwości każdego osadzonego formantu, aby uniemożliwić użytkownikom edytowanie ich zawartość.  
  
 Aby uzyskać więcej informacji o sposobie używania formantów zawartości do ochrona części dokumentów, zobacz [porady: ochrona części dokumentów za pomocą formantów zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
##  <a name="DataBinding"></a> Wiązanie danych z formantami zawartości  
 Można wyświetlić dane w dokumentach przez powiązanie formantu zawartości ze źródłem danych. Po zaktualizowaniu źródła danych formantu zawartości odzwierciedla zmiany. Można również zapisać zmiany w źródle danych.  
  
 Formanty zawartości udostępniają następujące opcje powiązania danych:  
  
-   Formanty zawartości można powiązać z pola bazy danych lub obiekty zarządzane przy użyciu tego samego modelu powiązanie danych formularzy systemu Windows.  
  
-   Formanty zawartości można powiązać z elementów w części XML (o nazwie *niestandardowe elementy XML*) osadzone w dokumencie.  
  
 Omówienie danych powiązania kontrolki hosta w rozwiązaniach pakietu Office, zobacz [powiązania danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
### <a name="using-the-windows-forms-data-binding-model"></a>Wiązanie modelu danych przy użyciu systemu Windows formularzy  
 Formanty zawartości najbardziej obsługuje model wiązania proste danych, który używa formularzy systemu Windows. Proste powiązanie danych oznacza, że formant jest powiązany element danych, takich jak wartość w kolumnie tabeli danych. Aby uzyskać więcej informacji, zobacz [powiązania danych i formularze systemu Windows](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 W projektach na poziomie dokumentu, można powiązać danych z formantami zawartości przy użyciu **źródeł danych** okna w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji na temat dodawania formantów zawartości powiązane z danymi do dokumentów, zobacz [porady: wypełnić dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md) i [porady: wypełnić dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
 W poniższej tabeli wymieniono formantów zawartości, które można powiązać z każdym typem danych **źródeł danych** okna.  
  
|Typ danych|Formant zawartości domyślny|Inne formanty zawartości, które mogą zostać powiązane do tego typu danych|  
|---------------|-----------------------------|----------------------------------------------------------------|  
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> Tablica|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Brak|  
  
 W poziomie dokumentu i projektów dodatku VSTO można powiązać zawartości formantu ze źródłem danych programowo przy użyciu <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> właściwości formantu. Jeśli to zrobisz, podaj ciąg **tekst** do *propertyName* parametr <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody. **Tekst** właściwość jest właściwością domyślną danych powiązanie formantów zawartości.  
  
 Formanty zawartości obsługują także powiązanie dwukierunkowe danych, w którym zmiany w formancie zostały zaktualizowane w źródle danych. Aby uzyskać więcej informacji, zobacz [porady: aktualizowanie źródła danych danymi z kontrolką hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
> [!NOTE]  
>  Formanty zawartości nie obsługują złożone powiązanie danych. W przypadku powiązania <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> lub <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> ze źródłem danych przy użyciu modelu danych formularzy systemu Windows, użytkownicy będą widzieć tylko jedną wartość, po kliknięciu formantu. Jeśli chcesz powiązać tych kontrolek do zestawu wartości danych, które użytkownicy mogą wybierać z tych kontrolek można powiązać elementów z niestandardowym elementem XML.  
  
### <a name="binding-content-controls-to-custom-xml-parts"></a>Wiązanie formantów zawartości do niestandardowych części XML  
 Niektóre formanty zawartości można powiązać z elementy niestandardowe elementy XML, które są osadzone w dokumencie. Aby uzyskać więcej informacji na temat niestandardowe elementy XML, zobacz [niestandardowych części XML ― omówienie](../vsto/custom-xml-parts-overview.md).  
  
 Aby powiązać formant zawartości elementu w niestandardowym elementem XML, użyj **XMLMapping** właściwości formantu. Poniższy przykład kodu pokazuje, jak można powiązać <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> do `Price` elementu w obszarze `Product` węzła w niestandardowym elementem XML, który został już dodany do dokumentu.  
  
```vb  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")  
```  
  
```csharp  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);  
```  
  
 Aby uzyskać wskazówki, który demonstruje sposób powiązanie formantów zawartości do niestandardowych części XML bardziej szczegółowo, zobacz [wskazówki: wiązanie formantów zawartości do niestandardowych części XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
 Po powiązaniu formantu zawartości z niestandardowym elementem XML, powiązanie dwukierunkowe danych jest automatycznie włączone. Jeśli użytkownik edytuje tekst w formancie, odpowiednich elementów XML są automatycznie aktualizowane. Podobnie zmiana wartości elementów w niestandardowe elementy XML formantów zawartości, które są powiązane elementy XML będą wyświetlane nowe dane.  
  
 Możesz powiązać następujące typy formantów zawartości do niestandardowych części XML:  
  
-   <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PictureContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>  
  
### <a name="data-binding-events-for-content-controls"></a>Powiązanie danych zdarzeń dla formantów zawartości  
 Wszystkie formanty zawartości udostępniają zestaw zdarzeń, które może obsłużyć do wykonywania zadań związanych z danymi, takich jak sprawdzanie, czy tekst w formancie spełnia określone kryteria, przed zaktualizowaniem źródła danych. W poniższej tabeli wymieniono zdarzenia formantu zawartości związanych z wiązania z danymi.  
  
|Zadanie|Zdarzenie|  
|----------|-----------|  
|Uruchom kod bezpośrednio przed zamknięciem Word automatycznie aktualizuje tekst w formancie zawartości, który jest powiązany z niestandardowym elementem XML.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|  
|Uruchom kod bezpośrednio przed zamknięciem Word automatycznie aktualizuje dane w niestandardowym elementem XML, który jest powiązany z zawartości kontroli (po zmienia tekst w formancie zawartości).|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|  
|Uruchomić kod do sprawdzania poprawności zawartości formantu zgodnie z niestandardowych kryteriów.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|  
|Uruchomić kod po zawartości formantu zostały pomyślnie zatwierdzone.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|  
  
## <a name="limitations-of-content-controls"></a>Ograniczenia formantów zawartości  
 Korzystając z formantów zawartości w projektach pakietu Office, należy pamiętać o następujące ograniczenia.  
  
### <a name="behavior-differences-between-design-time-and-run-time"></a>Zachowanie różnice czasu projektowania i w czasie wykonywania  
 Wiele ograniczeń, które program Microsoft Office Word nakłada się na formanty zawartości w czasie wykonywania nie są wymuszane w czasie projektowania. Podczas projektowania interfejsu użytkownika rozwiązania poziomie dokumentu w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], należy zmodyfikować formantów zawartości tylko w sposób, w którym są obsługiwane w czasie wykonywania.  
  
 Jeśli zmodyfikujesz zawartości formantu w czasie projektowania w taki sposób, który nie obsługuje formantu w czasie wykonywania, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta nie będzie alertów o nieobsługiwanych zmian. Jednak podczas debugowania i uruchomić projekt lub Zapisz i ponownie otwórz projekt, Word spowoduje wyświetlenie błędu komunikat żądania uprawnienia i naprawić tego dokumentu. Podczas naprawy dokument programu Word usuwa wszystkie nieobsługiwane zawartości i formatowania w formancie.  
  
 Na przykład program Word nie uniemożliwiają dodawania tabeli do <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> w czasie projektowania. Jednak ponieważ <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> obiekty nie mogą zawierać tabel w czasie wykonywania, Word wyświetli komunikat o błędzie, po otwarciu dokumentu.  
  
 Należy również zauważyć, że wiele właściwości, które określają zachowanie formantów zawartości nie obowiązują w czasie projektowania. Na przykład jeśli ustawisz **LockContents** właściwości formantu zawartości do **True** w czasie projektowania, można nadal edytować tekst w formancie w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta. Ta właściwość tylko uniemożliwia użytkownikom edycji formantu w czasie wykonywania.  
  
### <a name="event-limitations"></a>Ograniczenia dotyczące zdarzeń  
 Formanty zawartości są dostępne zdarzenie jest wywoływane, gdy użytkownik zmieni tekst lub innych elementów w formancie. Na przykład, nie ma żadnego zdarzenia, które jest wywoływane, gdy użytkownik wybierze inny element w <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> lub <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>.  
  
 Aby ustalić, kiedy użytkownik edytuje zawartość formantu zawartości, można powiązać formant z niestandardowym elementem XML, a następnie obsługi <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> zdarzeń. To zdarzenie jest wywoływane, gdy użytkownik zmieni zawartość formantu, który jest powiązany z niestandardowym elementem XML. Aby uzyskać wskazówki, który demonstruje sposób powiązania formantu zawartości do niestandardowych części XML, zobacz [wskazówki: wiązanie formantów zawartości do niestandardowych części XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
###  <a name="checkbox"></a> Formanty zawartości pól wyboru w projekty programu Word  
 Word 2010 wprowadzono nowy typ zawartości formantu, który reprezentuje pole wyboru. Jednak [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nie ma odpowiedniego typu CheckBoxContentControl do użycia w projektach pakietu Office. Można utworzyć formantu zawartości pola wyboru w [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub projekt Word 2010, użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> metodę w celu utworzenia <xref:Microsoft.Office.Tools.Word.ContentControl> obiektu i przekazać <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> wartość metodę, aby określić formantu zawartości pola wyboru. W poniższym przykładzie pokazano, jak to zrobić.  
  
 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Porady: dodawanie formantów zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Wskazówki: Tworzenie szablonu za pomocą formantów zawartości](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
