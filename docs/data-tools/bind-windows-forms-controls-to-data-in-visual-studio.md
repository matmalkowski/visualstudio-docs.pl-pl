---
title: Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio
ms.date: 11/03/2017
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4652d8dd3e9be582bc15c4644711accc06fd283f
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845525"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio
Aby wyświetlić dane użytkownikom aplikacji, wiązanie danych do formularzy systemu Windows. Aby utworzyć takie formanty powiązane z danymi, przeciągnij elementy z **źródeł danych** okna na Projektant formularzy systemu Windows w programie Visual Studio.

![Operacja przeciągania źródła danych](../data-tools/media/raddata-data-source-drag-operation.png)

Przed przeciągnij elementy, można ustawić typ kontroli, którą chcesz utworzyć powiązania. W zależności od tego, czy wybrano tabeli siebie lub poszczególnych kolumn są wyświetlane różne wartości.  Można również ustawić wartości niestandardowych. W przypadku tabeli **szczegóły** oznacza, że każda kolumna jest związany z formantem oddzielne.

![Powiązać źródła danych z formantu DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Kontrolki BindingSource i BindingNavigator
<xref:System.Windows.Forms.BindingSource> Składnika służy dwóch celów. Po pierwsze zapewnia warstwę abstrakcji podczas powiązywanie kontrolek z danymi. Formanty formularza jest powiązana z <xref:System.Windows.Forms.BindingSource> składnika zamiast bezpośrednio ze źródłem danych. Po drugie go zarządzanie kolekcją obiektów. Dodawanie typów do <xref:System.Windows.Forms.BindingSource> tworzy listę tego typu.

Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.BindingSource> składników, zobacz:

-   [BindingSource — składnik](/dotnet/framework/winforms/controls/bindingsource-component)

-   [Informacje o składniku BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

-   [Architektura składnika BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[Formantu BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) udostępnia interfejs użytkownika do przechodzenia między dane wyświetlane przez aplikację systemu Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Powiązanie z danymi w formancie DataGridView
Aby uzyskać [formantu DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), cała tabela jest powiązana do pojedynczego formantu. Przeciągnięcie **DataGridView** do formularza, narzędzie paska nawigacji rekordów (<xref:System.Windows.Forms.BindingNavigator>) jest również dostępny. A [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane na pasku składnika. Na poniższej ilustracji [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) również zostanie dodany, ponieważ tabela Klienci ma relację wobec tabeli zamówienia. Te zmienne są wszystkie zadeklarowane w automatycznie wygenerowany kod jako prywatne elementy członkowskie klasy formularza. Automatycznie wygenerowany kod dla wypełnianie **DataGridView** znajduje się w `Form_Load` obsługi zdarzeń. Kod zapisywania danych do aktualizacji bazy danych znajduje się w `Save` programu obsługi zdarzeń dla **BindingNavigator**. Można przenieść lub modyfikować ten kod w razie potrzeby.

![Element GridView o BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Można dostosować zachowanie **DataGridView** i **BindingNavigator** , klikając tagów inteligentnych w prawym górnym rogu każdej:

![DataGridView i powiązanie Nawigator tagów inteligentnych](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Jeśli formanty aplikacji wymaga nie są dostępne za pośrednictwem **źródeł danych** okna, można dodawać formanty. Aby uzyskać więcej informacji, zobacz [dodawanie formantów niestandardowych do okna źródeł danych](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Możesz także przeciągnąć elementy z **źródeł danych** okna na formanty już w formularzu można powiązać z danymi formantu. Formant, który jest już powiązany z danymi ma dane resetowania powiązania z elementem ostatnio przeciągnięto go. Aby identyfikator był prawidłowy miejsc docelowych, formanty muszą być umożliwiająca wyświetlanie podstawowy typ danych elementu przeciągane na niego z **źródeł danych** okna. Na przykład nie jest prawidłową przeciągnij elementu, który ma typ danych <xref:System.DateTime> na <xref:System.Windows.Forms.CheckBox>, ponieważ <xref:System.Windows.Forms.CheckBox> nie jest zdolny do wyświetlania daty.

## <a name="bind-to-data-in-individual-controls"></a>Powiązanie z danymi w pojedynczych formantów
Po powiązaniu źródło danych do **szczegóły**, każda kolumna w zestawie danych jest powiązany z oddzielnych formantu.

![Powiązać źródła danych, aby uzyskać więcej informacji](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Należy pamiętać, że na poprzedniej ilustracji, przeciągnij z właściwości zamówień tabeli Klienci nie z tabeli zamówienia. Przez powiązanie do `Customer.Orders` właściwość nawigacji polecenia wprowadzone w **DataGridView** natychmiast odzwierciedlone w formantach szczegóły. Jeśli przeciągnięte z tabeli zamówienia, formanty będą nadal powiązane z zestawem danych, ale nie one może nie być zsynchronizowany z **DataGridView**.

Na poniższej ilustracji przedstawiono domyślne formantów powiązanych z danymi, które są dodawane do formularza po właściwości zamówień w tabeli Klienci jest powiązany z **szczegóły** w **źródeł danych** okna.

![Tabela zamówienia powiązane szczegóły](../data-tools/media/raddata-orders-table-bound-to-details.png)

Należy pamiętać, że każdy formant ma tagów inteligentnych. Ten tag umożliwia dostosowania, które dotyczą tylko tego formantu.

## <a name="see-also"></a>Zobacz także

- [Powiązywanie kontrolek z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Powiązanie danych w formularzach systemu Windows (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)