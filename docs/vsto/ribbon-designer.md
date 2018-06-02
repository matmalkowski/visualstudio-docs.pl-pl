---
title: Projektant wstążki
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8cb8df33c89ce044572508918ba48edae2a6d75e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693347"
---
# <a name="ribbon-designer"></a>Projektant wstążki
  Projektant wstążki jest kanwy wizualnego projektu. Użyj projektanta wstążki, aby dodać niestandardowe karty, grup i kontroli do Wstążki aplikacji pakietu Microsoft Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Aby otworzyć projektanta wstążki, Dodaj **wstążki (projektanta wizualnego)** elementu do projektu. Następnie możesz użyć narzędzi do projektowania, do następujących zadań:  
  
-   [Projektowanie układu wstążki](#DesigningRibbonLayout)  
  
-   [Obsługa zdarzeń i ustaw właściwości formantu](#HandleEventsSetProperties)  
  
-   [Dodawanie formantów do widoku Backstage](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  Istnieje kilka zadań, których nie można osiągnąć za pomocą projektanta wstążki. Aby uzyskać więcej informacji na temat tych zadań i jak można je wykonać, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak I: Użyj projektanta wstążki, aby dostosować na Wstążce w programie Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Dodaj element wstążki (projektanta wizualnego) do projektu  
 Aby korzystać z projektanta wstążki, Dodaj nową **wstążki (projektanta wizualnego)** elementu do projektu. Aby uzyskać więcej informacji, zobacz [porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
 Po dodaniu nowego **wstążki (projektanta wizualnego)** elementu, Visual Studio automatycznie dodaje następujące pliki do projektu:  
  
-   Plik kodu wstążki. Ten plik ma nazwę, którą określisz dla **wstążki (projektanta wizualnego)** elementu **Dodaj nowy element** okno dialogowe. Dodaj kod obsługi zdarzenia wstążki do tego pliku.  
  
-   Projektant wstążki pliku kodu. Ten plik zawiera kod wygenerowany przez projektanta wstążki i nie należy bezpośrednio edytować.  
  
-   Plik zasobów. Ten plik zawiera wartości właściwości każdego formantu na Wstążce.  
  
 Jeśli masz już **wstążki (projektanta wizualnego)** elementu z innego projektu, można ponownie użyć go w bieżącym projekcie przy użyciu **Dodaj istniejący element** okno dialogowe.  
  
##  <a name="DesigningRibbonLayout"></a> Projektowanie wstążki  
 Istnieją trzy sposoby Otwórz projektanta wstążki:  
  
-   W **Eksploratora rozwiązań**, kliknij dwukrotnie plik kodu wstążki.  
  
-   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik kodu wstążki, a następnie kliknij przycisk **Widok projektanta**.  
  
-   W **Eksploratora rozwiązań**, wybierz plik kodu wstążki, a następnie kliknij przycisk **projektanta** na **widoku** menu.  
  
 Projektant wstążki zawiera domyślną kartę i grupy. Możesz usunąć domyślną kartę i grupy z projektanta wstążki. Aby usunąć domyślną grupę, kliknij prawym przyciskiem myszy **grupa1**, a następnie kliknij przycisk **usunąć**. Aby usunąć kartę domyślny, kliknij prawym przyciskiem myszy pusty obszar powierzchni projektu, a następnie kliknij **Usuń karty wstążki**.  
  
 Można również dodać niestandardowe karty, grupy i formanty do projektanta wstążki. Można znaleźć tych kontrolek w **przybornika**w **formantów wstążki pakietu Office** grupy. Istnieją trzy sposoby dodawania formantów z **formantów wstążki pakietu Office** grupy do projektanta wstążki:  
  
-   Przeciągnij formant do odpowiedniego obszaru na projektanta wstążki.  
  
-   Kliknij kontrolkę, a następnie kliknij odpowiedni obszar projektanta wstążki.  
  
-   Wybierz odpowiedni obszar w projektancie, a następnie kliknij dwukrotnie formantu w **przybornika**.  
  
### <a name="ribbon-design-workflow"></a>Przepływ pracy projektowania wstążki  
 Wykonaj następujące czynności, aby zaprojektować układ wstążki:  
  
1.  [Dodawanie kart niestandardowych do wstążki](#AddTabToRibbon).  
  
2.  [Aby dodać grupy do karty](#AddGroupsToTab).  
  
3.  [Dodawanie formantów do grup](#AddControlsToGroups).  
  
 Formanty można usunąć tylko w grupach; Nie można przeciągnąć formantu, bezpośrednio do karty lub do wstążki. Grupy można usunąć tylko na kartach. Nie można przeciągnąć grupę bezpośrednio do wstążki.  
  
 Rozmieszczanie formantów przeciągając je na prawidłowe pozycje. Można ustawić właściwości formantu przy użyciu **właściwości** okna.  
  
 Nie można przeciągnij formanty z jednej karty do innego na Wstążce. Jeśli chcesz przenieść formant do innej karty, należy użyć **Wytnij** polecenie, aby usunąć formant z jedną kartę, a następnie wklej kontrolki na inną kartę. Jeśli formant Wytnij i wklej go, program obsługi zdarzeń przestanie działać. Można ponownie połączyć program obsługi zdarzeń w **właściwości** okna. Aby uzyskać więcej informacji, zobacz [okna właściwości](/visualstudio/ide/reference/properties-window).  
  
###  <a name="AddTabToRibbon"></a> Dodaj niestandardowe karty do wstążki  
 Istnieją trzy sposoby dodawania niestandardowych kartę na Wstążce:  
  
-   Dodaj kartę z **przybornika**.  
  
-   Kliknij prawym przyciskiem myszy projektanta wstążki, a następnie kliknij przycisk **dodać karty wstążki**.  
  
-   Otwórz **edytora kolekcji kartę**, a następnie kliknij przycisk **Dodaj**.  
  
     Aby otworzyć **edytora kolekcji kartę**w **właściwości** wybierz **karty** właściwości, a następnie kliknij przycisk wielokropka ![ASP.NET Mobile Elipsy projektanta](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer").  
  
 Po dodaniu karty, można dodać grupy zawiera formanty.  
  
#### <a name="remove-custom-tabs-from-the-ribbon"></a>Usuń niestandardowe karty na Wstążce  
 Istnieją trzy sposoby usuwania kart niestandardowych na Wstążce:  
  
-   Kliknij prawym przyciskiem myszy projektanta, a następnie kliknij przycisk **Usuń karty wstążki**.  
  
-   W **polecenia** okienku **właściwości** okna, kliknij przycisk **Usuń karty wstążki**.  
  
-   Otwórz **edytora kolekcji kartę**, wybierz kartę, a następnie kliknij przycisk **Usuń**.  
  
#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Zmiana położenia zakładki na Wstążce  
 Można zmienić kolejność kart niestandardowych na Wstążce. Możesz również umieścić niestandardowe karty przed lub po wbudowanej karty na Wstążce. Aby uzyskać więcej informacji, zobacz [porady: zmiana położenia zakładki na wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Dostosowywanie wbudowanej karty na Wstążce  
 Tabulator wbudowana jest karta, która jest już na Wstążce aplikacji pakietu Microsoft Office. Na przykład **danych** karta jest wbudowanej karty w programie Excel.  
  
 Możesz dodać grup i kontroli do wbudowanej karty. Domyślnie niestandardową grupę pojawia się jako ostatni grupy na karcie wbudowanych, ale można go przenieść przed lub po wszelkich wbudowanej grupy na karcie.  
  
 Nie można usunąć wbudowanych grup.  
  
 Aby uzyskać więcej informacji o sposobie Dostosowywanie wbudowanej karty, zobacz [porady: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md).  
  
###  <a name="AddGroupsToTab"></a> Dodaj grupy, do karty  
 Grupy organizację formantów na Wstążce. Dodaj grupy na znaki tabulacji. Do grupy, należy dodać inne formanty.  
  
###  <a name="AddControlsToGroups"></a> Dodawanie formantów do grupy  
 Dodaj jeden lub kilka formantów do grupy. W poniższej tabeli opisano każdego formantu.  
  
|Formant|Opis|  
|-------------|-----------------|  
|**Box**|Kontener, który umożliwia organizowanie formantów w grupie. Można dodać żadnego formantu, do pola, z wyjątkiem separatora, grupy lub kartę. Pole może być pozioma lub pionowa.|  
|**Przycisk**|Przycisk, który rozpoczyna się akcja. Przycisk można dodać do grupy, Grupa przycisków, listy rozwijanej, Galeria, menu lub przycisku podziału.|  
|**Grupa przycisków**|Grupy, która zawiera jeden lub więcej przycisków, przycisków przełączania menu, przyciski podziału i galerii. Grupa przycisków można dodać do grupy lub menu.|  
|**CheckBox**|Pole jest zaznaczone lub wyczyszczone, aby włączyć lub wyłączyć opcję.|  
|**ComboBox**|Pole edycji z listą dołączony. Użytkownicy mogą albo wpisz lub wybierz wybranych przez nich. Pola są wyświetlane bieżące zaznaczenie. Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> właściwości do dodawania i usuwania elementów w czasie wykonywania przed lub po załadowaniu wstążki do aplikacji pakietu Office.|  
|**Lista rozwijana**|Lista elementów, które użytkownik może wybrać. Użytkownik nie wpisz nowy element na liście rozwijanej.<br /><br /> Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> właściwości, aby dodać elementy do listy. Można dodawać i usuwać elementy w czasie wykonywania.<br /><br /> Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> dodawanie przycisków do listy właściwości. Jednak nie można dodawać i usuwać przyciski w czasie wykonywania po załadowaniu wstążki do aplikacji pakietu Office.|  
|**Pole edycji**|Pole, w którym użytkownik może wpisać tekst.|  
|**Galeria**|Menu przedstawiający tablicą lub siatki visual opcji, z których użytkownicy mogą wybrać. Można kontrolować układ zaznaczeń w menu. Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> i <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> właściwości, aby określić liczbę wierszy i kolumn, które będzie wyświetlał elementy i przyciski galerii.|  
|**Etykieta**|Tekst, który służy do identyfikowania formantów na Wstążce.|  
|**Menu**|Listy rozwijanej, która może zawierać żadnego z następujących kontrolek:<br /><br /> -Przycisk<br />— Pole wyboru<br />-Galerii<br />-Menu<br />— Przycisk pokrętła<br />— Przełącznik<br />-Separatora<br /><br /> Aby dodać kontrolkę menu w Projektancie wstążki, kliknij strzałkę w dół w menu, aby ujawnić powierzchni projektowej menu. Można następnie przeciągnij formanty wstążki z **przybornika** na menu. Aby zorganizować formantów, przeciągnij je do odpowiednie pozycje.<br /><br /> Do dodawania formantów do <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> po załadowaniu wstążki do aplikacji pakietu Office, musisz ustawić <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> właściwości **true** przed załadowaniem wstążki. Aby dowiedzieć się, jak to zrobić, zobacz [model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md).|  
|**Separator**|Pasek alokowania używany do oddzielania elementów na liście. Po dodaniu do grupy, pasek jest pionowy. Po dodaniu do menu, paska jest poziomy.|  
|**Przycisk podziału**|Przycisk menu dołączony. Przycisk podziału może zawierać żadnego z następujących kontrolek:<br /><br /> -Przycisk<br />— Pole wyboru<br />-Galerii<br />-Menu<br />— Przycisk pokrętła<br />— Przełącznik<br />-Separatora<br /><br /> Podobnie jak menu przycisku podziału ma własną powierzchnię projektu. Jednak w przeciwieństwie do menu, możesz aktualizować tylko elementy przycisku podziału przed załadowaniem wstążki do aplikacji pakietu Office. Aby uzyskać informacje o sposobie aktualizowania elementów przycisku podziału, zobacz [model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md).|  
|**ToggleButton**|Przycisk wyświetlony naciśnięcie lub nie naciśnięto symbolu.|  
  
##  <a name="HandleEventsSetProperties"></a> Obsługa zdarzeń i ustawienie właściwości  
 Projektant wstążki umożliwia ustawienie właściwości formantu w czasie projektowania przy użyciu **właściwości** okna. Ponadto wstążki udostępnia silnie typizowany obiekt modelu, który służy do pobierania i ustawiania właściwości formantów wstążki w czasie wykonywania.  
  
 Możesz kliknąć dwukrotnie żadnego formantu na projektanta, aby otworzyć program obsługi zdarzeń dla zdarzenia domyślne formantu. Programy obsługi zdarzeń dla wszystkich zdarzeń kontrolowania można tworzyć przy użyciu **właściwości** okna.  
  
 Wstążka zdarzeń i właściwości, które znajdują się w <xref:Microsoft.Office.Tools.Ribbon> przestrzeni nazw. **Wstążki (projektanta wizualnego)** elementu automatycznie dodaje odwołania do tego zestawu w projekcie i wstawia odpowiednie **przy użyciu** lub **importów** instrukcji u góry Wstążka pliku kodu.  
  
 Aby informacji na temat obsługi zdarzeń Wstążki i ustawienie właściwości formantów wstążki w czasie wykonywania, zobacz [model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md).  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a> Dostosowywanie widoku Backstage  
 Projektant wstążki umożliwia dodawanie formantów do menu dostępnym po kliknięciu **pliku** kartę. W tym menu nosi nazwę widoku Backstage.  
  
 Nie możesz umieścić kontrolek przed lub po formantów wbudowanych za pomocą projektanta wstążki. Wbudowane funkcje sterowania jest już wyświetlany w widoku Backstage formantu. Jeśli chcesz umieścić kontrolek przed lub po formantów wbudowanych, należy użyć kodu XML wstążki. Aby uzyskać więcej informacji na temat **wstążki (XML)**, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md). Aby uzyskać więcej informacji dotyczących dostosowywania widoku Backstage, zobacz [wprowadzenie do pakietu Office 2010 Backstage widoku dla deweloperów](http://go.microsoft.com/fwlink/?LinkId=182189) i [dostosować widok pakietu Office 2010 Backstage dla deweloperów](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 Aby uzyskać informacje o sposobie dodawania formantów do widoku Backstage, zobacz [porady: dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
##  <a name="Accessibility"></a> Ułatwienia dostępu w Projektancie wstążki  
 Skróty klawiaturowe umożliwia przenoszenie formantów w Projektancie wstążki. Niektóre skróty klawiaturowe dotyczą wszystkich kontrolek, a niektóre dotyczą tylko formanty, które mają menu.  
  
 W poniższej tabeli przedstawiono skróty klawiaturowe, które są stosowane do wszystkich kontrolek.  
  
|Akcja|Skrót klawiaturowy|  
|------------|-----------------------|  
|Przesuń kontrolkę przed poprzednią kontrolkę na liście.|**CTRL**+**się**<br /><br /> **CTRL**+**lewej**|  
|Przesuń kontrolkę po następnej kontrolki na liście.|**CTRL**+**w dół**<br /><br /> **CTRL**+**prawej**|  
|Przeniesienie zaznaczenia do innego z tej samej grupy. Panelu listy rozwijanej przenoszeniu ich do kontrolki nadrzędnej i formantów w panelu listy rozwijanej.|**W górę**<br /><br /> **W dół**|  
|Przekazuj iterację wszystkie kontrolki.|**Karta**|  
|Iterowanie wstecznego przez wszystkie kontrolki.|**SHIFT**+**kartę**|  
|Usuń wybrany formant lub zbiór kontrolek.|**Usuwanie**|  
|Skopiuj wybrane formanty.|**CTRL**+**C**|  
|Wytnij wybrane formanty.|**CTRL**+**X**|  
|Wklej formanty ze Schowka.|**CTRL**+**V**|  
|Wybierz **przybornika**.|**CTRL**+**Alt**+**X**|  
|Wybierz składnik nadrzędny.|**ESC**|  
  
 Skróty klawiaturowe, które mają zastosowanie tylko do Microsoft Office Menu <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, i <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> przedstawiono w poniższej tabeli.  
  
|Akcja|Skrót klawiaturowy|  
|------------|-----------------------|  
|Wybierz formant nadrzędny jest otwarty panel listy rozwijanej, jeśli ma formantu wybranego na panelu listy rozwijanej.|**Po lewej**|  
|Zamknij panel listy rozwijanej, jeśli formant nadrzędny jest zaznaczone i jest otwarty panel listy rozwijanej.|**Po lewej**|  
|Otwórz panel listy rozwijanej.|**Prawo**|  
|Wybierz pierwszą kontrolkę w panelu listy rozwijanej, jeśli panel listy rozwijanej jest otwarty.|**Prawo**|  
|Zamknij panel listy rozwijanej.|**ESC**|  
  
## <a name="see-also"></a>Zobacz także  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [XML wstążki](../vsto/ribbon-xml.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Porady: eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  