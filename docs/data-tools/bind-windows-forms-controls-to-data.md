---
redirect_url: /visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio
ms.openlocfilehash: 5ba8ada294275a99aab27ff9c249d6c3d8e17da3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
Tytuł: "formanty formularzy systemu Windows powiązanego z danymi | Ms.custom Microsoft Docs":" "ms.date: ms.reviewer"2016-11-04":" "ms.suite:" "ms.tgt_pltfrm:" "ms.topic:"artykuł"helpviewer_keywords: 
  - "Wyświetlanie danych, formanty formularzy systemu Windows"
  - "Formularze systemu Windows, wyświetlanie danych"
  - "źródeł danych, wyświetlanie"
  - ms.assetid "dane [formularze systemu Windows] wyświetlanie": 0163a34a-38cb-40b9-8f38-3058a90caf21 caps.latest.revision: 28 Autor: ms.author "gewarren": "gewarren" Menedżer: ghogen ms.technology: "narzędzia vs danych"
---
# <a name="bind-windows-forms-controls-to-data"></a>Powiązywanie formantów formularzy systemu Windows z danymi
Źródła danych można powiązać z formantów, przeciągając obiekty z **źródeł danych** okna na formularzu systemu Windows lub na istniejącej kontrolce na formularzu. Przed przeciągnij elementy, można ustawić typ kontroli, którą chcesz utworzyć powiązania. W zależności od tego, czy wybrano tabeli siebie lub poszczególnych kolumn są wyświetlane różne wartości.  Można również ustawić wartości niestandardowych. Dla tabeli "Szczegóły" oznacza, że każda kolumna jest związany z formantem oddzielne.  

![Powiązać źródła danych z formantu DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata powiązanego źródła danych do formantu DataGridView")  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Powiązanie z danymi w formancie DataGridView  
Dla formantu DataGridView cała tabela jest powiązana do pojedynczego formantu. Podczas przeciągania DataGridView w formularzu narzędzia paska nawigacji rekordów (<xref:System.Windows.Forms.BindingNavigator>) jest również dostępny. A [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane na pasku składnika. Na poniższej ilustracji obiekt TableAdapterManager również zostanie dodany, ponieważ tabela Klienci ma relację wobec tabeli zamówienia. Te zmienne są wszystkie zadeklarowane w automatycznie wygenerowany kod jako prywatne elementy członkowskie klasy formularza. Automatycznie wygenerowany kod dla formantu DataGridView wypełnianie znajduje się w obsłudze zdarzeń form_load. Kod zapisywania danych do aktualizacji bazy danych znajduje się w programu obsługi zdarzeń Zapisz BindingNavigator. Można przenieść lub modyfikować ten kod w razie potrzeby.  
  
 ![Element GridView o BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView z właściwością BindingNavigator")  
  
 Można dostosować zachowanie formantu DataGridView i parametrze BindingNavigator, klikając tagów inteligentnych w prawym górnym rogu każdej:  
  
 ![DataGridView i powiązanie Nawigator tagów inteligentnych](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView i powiązanie Nawigator tagów inteligentnych")  
  
 Jeśli formanty aplikacji wymaga nie są dostępne za pośrednictwem **źródeł danych** okna, można dodawać formanty. Aby uzyskać więcej informacji, zobacz [dodawanie formantów niestandardowych do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Możesz także przeciągnąć elementy z **źródeł danych** okna na formanty już w formularzu można powiązać z danymi formantu. Formant, który jest już powiązany z danymi ma dane resetowania powiązania z elementem ostatnio przeciągnięto go. Aby identyfikator był prawidłowy miejsc docelowych, formanty muszą być umożliwiająca wyświetlanie podstawowy typ danych elementu przeciągane na niego z **źródeł danych** okna. Na przykład nie jest prawidłową przeciągnij elementu, który ma typ danych <xref:System.DateTime> na <xref:System.Windows.Forms.CheckBox>, ponieważ <xref:System.Windows.Forms.CheckBox> nie jest zdolny do wyświetlania daty.  
  
## <a name="bind-to--data-in-individual-controls"></a>Powiązanie z danymi w pojedynczych formantów  
 Gdy "Szczegóły" można powiązać źródła danych, każdej kolumny w zestawie danych jest powiązany z oddzielnych formantu.  
  
 ![Źródło danych należy powiązać szczegóły](../data-tools/media/raddata-bind-data-source-to-details.png "raddata powiązanego źródła danych, aby uzyskać więcej informacji")  
  
> [!IMPORTANT]
>  Należy pamiętać, że na poprzedniej ilustracji, przeciągnij z właściwości zamówień tabeli Klienci nie z tabeli zamówienia. Przez powiązanie dla właściwości Customer.Orders, wprowadzone w formancie DataGridView polecenia nawigacji są natychmiast odzwierciedlone w formantach szczegóły. Przypadku przeciągania z tabeli zamówienia formanty będą nadal powiązane z zestawem danych, ale nie ich może nie zostać zsynchronizowany z formantu DataGridView.  
  
 Na poniższej ilustracji przedstawiono domyślne formanty powiązane z danymi, które są dodawane do formularza po właściwości zamówień w tabeli Klienci jest powiązany z "Szczegóły" w **źródeł danych** okna.  
  
 ![Powiązana tabela zamówień szczegóły](../data-tools/media/raddata-orders-table-bound-to-details.png "powiązana tabela zamówień raddata szczegóły")  
  
 Należy pamiętać, że każdy formant ma tagów inteligentnych. Ten tag umożliwia dostosowania, które dotyczą tylko tego formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)