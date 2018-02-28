---
title: "Omówienie modelu obiektu Wstążka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: bda61cd7ca0e169a4f62fbc0c33b24e3c4ec0048
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="ribbon-object-model-overview"></a>Model obiektu Wstążka ― Omówienie
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Udostępnia silnie typizowany obiekt modelu, który służy do pobierania i ustawiania właściwości formantów wstążki w czasie wykonywania. Na przykład możesz można dynamicznie wypełnianie formantów menu lub pokazać lub ukryć kontrolki kontekstowej. Na Wstążce, ale tylko w przypadku, przed załadowaniem wstążki według aplikacji pakietu Office, można dodać kart, grup i kontrolek. Aby uzyskać informacje, zobacz [ustawienie właściwości że stają się tylko do odczytu](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Ten model obiektu Wstążka składa się głównie z [klasy wstążki](#RibbonClass), [zdarzenia wstążki](#RibbonEvents), i [klasy formantów wstążki](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a>Klasa wstążki  
 Po dodaniu nowego **wstążki (projektanta wizualnego)** elementu do projektu programu Visual Studio dodaje **wstążki** klasy do projektu. **Wstążki** klasa dziedziczy <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> klasy.  
  
 Ta klasa jest wyświetlany jako częściowe klasy, która jest dzielone na Wstążce pliku kodu i pliku kodu projektanta wstążki.  
  
##  <a name="RibbonEvents"></a>Zdarzenia wstążki  
 **Wstążki** klasa zawiera trzy następujące zdarzenia:  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Wywoływane, gdy dostosowywania wstążki ładowania aplikacji pakietu Office. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> Program obsługi zdarzeń jest automatycznie dodawany do pliku kodu wstążki. Użyj tej obsługi zdarzeń do uruchomienia kodu niestandardowego, po załadowaniu wstążki.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Umożliwia utworzenie pamięci podręcznej obrazów w dostosowywania wstążki po załadowaniu wstążki. Możesz uzyskać są bardziej wydajne nieznaczne podczas pisania kodu do pamięci podręcznej obrazów wstążki w tej obsłudze zdarzeń. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Uruchamiany po zamknięciu wystąpienia wstążki.|  
  
##  <a name="RibbonControlClasses"></a>Formanty Wstążki  
 <xref:Microsoft.Office.Tools.Ribbon> Przestrzeń nazw zawiera typ dla każdego formantu, który pojawi się w **formantów wstążki pakietu Office** grupy **przybornika**.  
  
 W poniższej tabeli przedstawiono typ dla każdego `Ribbon` formantu. Aby uzyskać opis każdego formantu, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
|Nazwa formantu|Nazwa klasy|  
|------------------|----------------|  
|**Pole**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Przycisk**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**Grupa przycisków**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**Lista rozwijana**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**Pole edycji**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Galerii**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Grupy**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Etykieta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**Przycisk podziału**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Karta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 <xref:Microsoft.Office.Tools.Ribbon> Przestrzeni nazw używa prefiksu "Wstążki" dla tych typów, aby uniknąć kolizji nazw z nazwami klas kontroli w <xref:System.Windows.Forms> przestrzeni nazw.  
  
 Po dodaniu formantu do projektanta wstążki projektanta wstążki deklaruje klasy dla tego formantu jako pole w pliku kodu projektanta wstążki.  
  
### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Typowe zadania za pomocą właściwości formantów wstążki  
 Każdy `Ribbon` formant zawiera właściwości, których można używać do wykonywania różnych zadań, takich jak przypisywanie etykietę do formantu, lub wyświetlanie i ukrywanie formantów.  
  
 W niektórych przypadkach właściwości stają się tylko do odczytu po załadowaniu Wstążki lub formant został dodany do menu dynamiczne. Aby uzyskać więcej informacji, zobacz [ustawiając właściwości tego Become tylko do odczytu](#SettingReadOnlyProperties).  
  
 W poniższej tabeli opisano niektóre z zadań, które można wykonywać za pomocą `Ribbon` właściwości formantu.  
  
|Dla tego zadania:|wykonaj następujące czynności:|  
|--------------------|--------------|  
|Ukrycie lub pokazanie formantu.|Użyj właściwości Visible.|  
|Włącza lub wyłącza formant.|Użyj właściwości Enabled.|  
|Ustaw rozmiar formantu.|Użyj właściwości ControlSize.|  
|Pobierz obraz wyświetlany w formancie.|Użyj właściwości obrazu.|  
|Zmienianie etykiety formantu.|Użyj właściwości etykiety.|  
|Dodawanie danych do formantu.|Użyj właściwości tagu.|  
|Pobierz elementy w <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>, lub<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>formant.|Użyj właściwości elementów.|  
|Dodaj elementy do <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, lub <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> formantu.|Użyj właściwości elementów.|  
|Dodawanie formantów do <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Użyj właściwości elementów.<br /><br /> Do dodawania formantów do <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> po załadowaniu wstążki do aplikacji pakietu Office, musisz ustawić <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> właściwości **true** przed załadowaniem wstążki do aplikacji pakietu Office. Aby uzyskać informacje, zobacz [ustawienie właściwości że stają się tylko do odczytu](#SettingReadOnlyProperties).|  
|Pobierz zaznaczonego elementu <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, lub <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Użyj właściwości SelectedItem. Aby uzyskać <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> właściwości.|  
|Pobierz grupy <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> właściwości.|  
|Określ liczbę wierszy i kolumn, które są widoczne w <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> i <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> właściwości.|  
  
##  <a name="SettingReadOnlyProperties"></a>Ustawianie właściwości, które stają się tylko do odczytu  
 Niektóre właściwości można ustawić tylko przed ładuje wstążki. Istnieją trzy miejsca ustawić te właściwości:  
  
-   W programie Visual Studio **właściwości** okna.  
  
-   W Konstruktorze **wstążki** klasy.  
  
-   W metodzie CreateRibbonExtensibilityObject `ThisAddin`, `ThisWorkbook`, lub `ThisDocument` klasy projektu.  
  
 Menu dynamiczne Podaj niektóre wyjątki. Można tworzyć nowe formanty, ustawiania ich właściwości i dodać je do menu dynamiczne w czasie wykonywania, nawet po załadowaniu wstążki, która zawiera menu.  
  
 W dowolnym momencie można ustawić właściwości formantów, które dodajesz do menu dynamiczne.  
  
 Aby uzyskać więcej informacji, zobacz [właściwości tego Become tylko do odczytu](#ReadOnlyProperties).  
  
### <a name="setting-properties-in-the-constructor-of-the-ribbon"></a>Ustawianie właściwości w Konstruktorze wstążki  
 Można ustawić właściwości `Ribbon` kontroli w Konstruktorze **wstążki** klasy. Ten kod musi występować po wywołaniu `InitializeComponent` metody. W następującym przykładzie dodano nowy przycisk do grupy, jeśli bieżąca godzina jest 17:00 czasu pacyficznego (UTC-8) lub nowszym.  
  
 Dodaj następujący kod.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]  
  
 W środowisku Visual C# projektów, które w przypadku uaktualniania z programu Visual Studio 2008 konstruktora pojawia się w pliku kodu wstążki.  
  
 Projekty Visual Basic lub Visual C# projektów, które zostały utworzone w [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], konstruktora pojawia się w pliku kodu projektanta wstążki. Ten plik ma nazwę *YourRibbonItem*. Designer.cs narzędzie lub *YourRibbonItem*. Designer.VB. Aby wyświetlić ten plik w projektach Visual Basic, należy najpierw kliknąć **Pokaż wszystkie pliki** przycisk w Eksploratorze rozwiązań.  
  
### <a name="setting-properties-in-the-createribbonextensibilityobject-method"></a>Ustawianie właściwości w metodzie CreateRibbonExtensibilityObject  
 Można ustawić właściwości `Ribbon` kontrolowania, kiedy należy zastąpić metodę CreateRibbonExtensibilityObject w `ThisAddin`, `ThisWorkbook`, lub `ThisDocument` klasy projektu. Aby uzyskać więcej informacji na temat metody CreateRibbonExtensibilityObject, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
 Poniższy przykład przedstawia właściwości wstążki w metodzie CreateRibbonExtensibilityObject `ThisWorkbook` klasy projektu skoroszyt programu Excel.  
  
 Dodaj następujący kod.  
  
 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]  
  
###  <a name="ReadOnlyProperties"></a>Właściwości, które stają się tylko do odczytu  
 W poniższej tabeli przedstawiono właściwości, które można ustawić tylko przed ładuje wstążki.  
  
> [!NOTE]  
>  W dowolnym momencie można ustawić właściwości formantów w menu dynamiczne. Ta tabela nie ma zastosowania w takim przypadku.  
  
|Właściwość|Klasa formantów wstążki|  
|--------------|--------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Właściwość ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Właściwości ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dynamiczne**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Globalne**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Grupy**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**Nazwa_obrazu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Element MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Nazwa**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Stanowisko**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Liczba wierszy**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Karty**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Tytuł**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### <a name="setting-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Ustawianie właściwości taśmy, które są wyświetlane w programie Outlook inspektorzy  
 Nowe wystąpienie klasy wstążki jest tworzone za każdym razem, użytkownik otwiera inspektora, w której znajduje się wstążki. Jednak można ustawić właściwości wymienione w powyższej tabeli wyłącznie przed utworzeniem pierwszego wystąpienia wstążki. Po pierwszym wystąpieniu jest tworzony, te właściwości stać się tylko do odczytu, ponieważ pierwsze wystąpienie definiuje plik XML, który korzysta z programu Outlook można załadować na Wstążce.  
  
 Jeśli masz logikę warunkową, który ustawia żadnej z tych właściwości na inną wartość, gdy tworzone są inne wystąpienia wstążki, ten kod nie odniesie żadnego skutku.  
  
> [!NOTE]  
>  Upewnij się, że **nazwa** właściwość ma wartość dla każdego dodawanego do wstążki Outlook formantu. Jeśli formant zostanie dodany do programu Outlook wstążki w czasie wykonywania, należy ustawić tę właściwość w kodzie. Jeśli dodasz formantu do Wstążki programu Outlook w czasie projektowania, automatycznie jest ustawiona właściwość Name.  
  
## <a name="ribbon-control-events"></a>Zdarzenia formantów wstążki  
 Każda klasa formant zawiera co najmniej jednego zdarzenia. W poniższej tabeli opisano te zdarzenia.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|Kliknij|Występuje, gdy formant zostanie kliknięty.|  
|TextChanged|Występuje, gdy tekst pola edycji lub pola kombi zostanie zmieniona.|  
|ItemsLoading|Występuje, gdy kolekcji elementów formantu jest wymagane przez pakiet Office. Office buforuje kolekcji elementów, dopóki kod zmiany właściwości formantu, lub należy wywołać <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> metody.|  
|ButtonClick|Występuje, gdy przycisk w <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> lub <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> zostanie kliknięty.|  
|SelectionChanged|Występuje, gdy zaznaczenie w <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> lub <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> zmiany.|  
|DialogLauncherClick|Występuje po kliknięciu ikony uruchamiania okna dialogowego, w prawym dolnym rogu grupy.|  
  
 Programy obsługi zdarzeń dla tych zdarzeń ma dwa parametry opisane poniżej.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*nadawca*|<xref:System.Object> Reprezentujący formant, który wywołał zdarzenie.|  
|*e*|A <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> zawierający <xref:Microsoft.Office.Core.IRibbonControl>. Umożliwia dostęp do dowolnej właściwości, która nie jest dostępna w modelu obiektu Wstążka udostępniane przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Wskazówki: Aktualizowanie formantów na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Porady: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)   
 [Porady: dodawanie formantów do widoku Zakulisowego](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Porady: eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Instrukcje: Pokazywanie błędów dodatków interfejsu użytkownika](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  