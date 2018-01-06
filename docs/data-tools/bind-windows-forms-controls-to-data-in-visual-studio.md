---
title: "Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 7ade7aa6e103a8637d26b10029faabc434ce3a83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio
Aby wyświetlić dane użytkownikom aplikacji, wiązanie danych do formularzy systemu Windows. Aby utworzyć takie formanty powiązane z danymi, można przeciągnij elementy z **źródeł danych** okna na Projektant formularzy systemu Windows w programie Visual Studio.
  
![Źródło danych operacji przeciągania](../data-tools/media/raddata-data-source-drag-operation.png "operacji przeciągania raddata źródła danych")

Przed przeciągnij elementy, można ustawić typ kontroli, którą chcesz utworzyć powiązania. W zależności od tego, czy wybrano tabeli siebie lub poszczególnych kolumn są wyświetlane różne wartości.  Można również ustawić wartości niestandardowych. Dla tabeli "Szczegóły" oznacza, że każda kolumna jest związany z formantem oddzielne.  

![Powiązać źródła danych z formantu DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata powiązanego źródła danych do formantu DataGridView")  
  
## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource i kontrolki BindingNavigator
<xref:System.Windows.Forms.BindingSource> Składnika służy dwóch celów. Po pierwsze zapewnia warstwę abstrakcji podczas powiązywanie kontrolek z danymi. Formanty formularza jest powiązana z <xref:System.Windows.Forms.BindingSource> składnika zamiast bezpośrednio ze źródłem danych. Po drugie go zarządzanie kolekcją obiektów. Dodawanie typów do <xref:System.Windows.Forms.BindingSource> tworzy listę tego typu.  
  
Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.BindingSource> składników, zobacz:  
  
-   [BindingSource, składnik](/dotnet/framework/winforms/controls/bindingsource-component)  
  
-   [BindingSource, składnik — omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
-   [BindingSource, składnik — architektura](/dotnet/framework/winforms/controls/bindingsource-component-architecture)  
  
[Formantu BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) udostępnia interfejs użytkownika do przechodzenia między dane wyświetlane przez aplikację systemu Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Powiązanie z danymi w formancie DataGridView  
Aby uzyskać [formantu DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), cała tabela jest powiązana do pojedynczego formantu. Podczas przeciągania DataGridView w formularzu narzędzia paska nawigacji rekordów (<xref:System.Windows.Forms.BindingNavigator>) jest również dostępny. A [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane na pasku składnika. Na poniższej ilustracji obiekt TableAdapterManager również zostanie dodany, ponieważ tabela Klienci ma relację wobec tabeli zamówienia. Te zmienne są wszystkie zadeklarowane w automatycznie wygenerowany kod jako prywatne elementy członkowskie klasy formularza. Automatycznie wygenerowany kod dla formantu DataGridView wypełnianie znajduje się w obsłudze zdarzeń form_load. Kod zapisywania danych do aktualizacji bazy danych znajduje się w programu obsługi zdarzeń Zapisz BindingNavigator. Można przenieść lub modyfikować ten kod w razie potrzeby.  
  
![Element GridView o BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView z właściwością BindingNavigator")  
  
Można dostosować zachowanie formantu DataGridView i parametrze BindingNavigator, klikając tagów inteligentnych w prawym górnym rogu każdej:  
  
![DataGridView i powiązanie Nawigator tagów inteligentnych](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView i powiązanie Nawigator tagów inteligentnych")  
  
Jeśli formanty aplikacji wymaga nie są dostępne za pośrednictwem **źródeł danych** okna, można dodawać formanty. Aby uzyskać więcej informacji, zobacz [dodawanie formantów niestandardowych do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
Możesz także przeciągnąć elementy z **źródeł danych** okna na formanty już w formularzu można powiązać z danymi formantu. Formant, który jest już powiązany z danymi ma dane resetowania powiązania z elementem ostatnio przeciągnięto go. Aby identyfikator był prawidłowy miejsc docelowych, formanty muszą być umożliwiająca wyświetlanie podstawowy typ danych elementu przeciągane na niego z **źródeł danych** okna. Na przykład nie jest prawidłową przeciągnij elementu, który ma typ danych <xref:System.DateTime> na <xref:System.Windows.Forms.CheckBox>, ponieważ <xref:System.Windows.Forms.CheckBox> nie jest zdolny do wyświetlania daty.  
  
## <a name="bind-to-data-in-individual-controls"></a>Powiązanie z danymi w pojedynczych formantów  
Gdy "Szczegóły" można powiązać źródła danych, każdej kolumny w zestawie danych jest powiązany z oddzielnych formantu.  
  
![Źródło danych należy powiązać szczegóły](../data-tools/media/raddata-bind-data-source-to-details.png "raddata powiązanego źródła danych, aby uzyskać więcej informacji")  
  
> [!IMPORTANT]
> Należy pamiętać, że na poprzedniej ilustracji, przeciągnij z właściwości zamówień tabeli Klienci nie z tabeli zamówienia. Przez powiązanie dla właściwości Customer.Orders, wprowadzone w formancie DataGridView polecenia nawigacji są natychmiast odzwierciedlone w formantach szczegóły. Przypadku przeciągania z tabeli zamówienia formanty będą nadal powiązane z zestawem danych, ale nie ich może nie zostać zsynchronizowany z formantu DataGridView.  
  
Na poniższej ilustracji przedstawiono domyślne formanty powiązane z danymi, które są dodawane do formularza po właściwości zamówień w tabeli Klienci jest powiązany z "Szczegóły" w **źródeł danych** okna.  
  
![Powiązana tabela zamówień szczegóły](../data-tools/media/raddata-orders-table-bound-to-details.png "powiązana tabela zamówień raddata szczegóły")  
  
Należy pamiętać, że każdy formant ma tagów inteligentnych. Ten tag umożliwia dostosowania, które dotyczą tylko tego formantu.
  
## <a name="see-also"></a>Zobacz także
[Powiązywanie kontrolek z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
[Powiązanie danych w formularzach systemu Windows (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)