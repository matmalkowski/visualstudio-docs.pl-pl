---
title: Tworzenie tabel wyszukiwania w aplikacjach formularzy systemu Windows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: f27fdbe216b6ba2a738f6d9f45d746344d542b38
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Tworzenie tabel wyszukiwania w aplikacjach formularzy systemu Windows
Termin *tabeli odnośników* zawiera opis kontrolek, które są powiązane z dwóch powiązanych tabel danych. Te kontrolki wyszukiwania odnośników pokazują dane z pierwszej tabeli w oparciu o wartości wybrane w drugiej tabeli.  
  
 Tabele wyszukiwania można utworzyć, przeciągając węzeł główny tabeli nadrzędnej (z [Data Sources — okno](add-new-data-sources.md)) na kontrolkę w formularzu, która jest już powiązany z kolumną w tabeli podrzędnych.  
  
 Na przykład rozważmy tabelę `Orders` w bazie danych sprzedaży. Każdy rekord w `Orders` tabela zawiera `CustomerID`, wskazujący, które złożone kolejności. `CustomerID` to klucz obcy wskazujący rekord klienta w tabeli `Customers`. W tym scenariuszu, należy rozwinąć `Orders` tabeli w **źródeł danych** okna i ustaw węzeł główny na **szczegóły**. Następnie ustaw `CustomerID` kolumnę <xref:System.Windows.Forms.ComboBox> (lub inny formant obsługującego powiązanie wyszukiwania) i przeciągnij `Orders` węzła do formularza. Na koniec, przeciągnij `Customers` węzła na kontrolkę, która jest powiązana z kolumną powiązanych — w takim przypadku <xref:System.Windows.Forms.ComboBox> powiązany `CustomerID` kolumny.  
  
## <a name="to-databind-a-lookup-control"></a>Aby powiązać z danymi kontrolkę wyszukiwania odnośników  
  
1.  Otwórz **źródeł danych** okna.  
  
    > [!NOTE]
    >  Tabele wyszukiwania wymaga dwóch tabel powiązanych lub obiekty są dostępne w **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](relationships-in-datasets.md).  
  
2.  Rozwiń węzły w **źródeł danych** okna tak, aby wyświetlić tabeli nadrzędnej i wszystkie jego kolumn i tabel podrzędnych i wszystkie jego kolumny.  
  
    > [!NOTE]
    >  Węzłem tabeli podrzędnej jest węzeł pokazywany jako rozwijany węzeł podrzędny tabeli nadrzędnej.  
  
3.  Zmień typ listy tabelą podrzędną dla **szczegóły** wybierając **szczegóły** z listy kontroli w węźle tabeli podrzędnej. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
4.  Znajdź węzeł, który łączy dwie tabele ( `CustomerID` węzła w poprzednim przykładzie). Zmień jego usuwania typów do <xref:System.Windows.Forms.ComboBox> wybierając **ComboBox** z listy kontroli.  
  
5.  Przeciągnij głównego podrzędnym tabeli z **źródeł danych** okna na formularzu.  
  
     W formularzu pojawią się kontrolki powiązane z danymi (z etykietami opisowymi) oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>). A [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane na pasku składnika.  
  
6.  Teraz przeciągnij węzeł nadrzędny głównego tabeli z **źródeł danych** okna bezpośrednio na formant wyszukiwania ( <xref:System.Windows.Forms.ComboBox>).  
  
     Powiązania wyszukiwania odnośników są teraz ustanowione. W poniższej tabeli opisano konkretne właściwości skonfigurowane w kontrolce.  
  
    |Właściwość|Wyjaśnienie ustawienia|  
    |--------------|----------------------------|  
    |**Źródło danych**|Jako wartość tej właściwości program Visual Studio ustawia element <xref:System.Windows.Forms.BindingSource> utworzony dla tabeli przeciągniętej na kontrolkę (w przeciwieństwie do elementu <xref:System.Windows.Forms.BindingSource> utworzonego podczas tworzenia kontrolki).<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na element <xref:System.Windows.Forms.BindingSource> tabeli zawierającej kolumnę, która ma być wyświetlana.|  
    |**DisplayMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę po kluczu podstawowym zawierającą dane będące ciągiem tekstowym w tabeli, która została przeciągnięta na kontrolkę.<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na nazwę kolumny, która ma być wyświetlana.|  
    |**ValueMember**|Jako wartość tej właściwości program Visual Studio ustawia pierwszą kolumnę należącą do klucza podstawowego, a jeśli klucz nie został zdefiniowany, pierwszą kolumnę tabeli.<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na klucz podstawowy w tabeli zawierającej kolumnę, która ma być wyświetlana.|  
    |**SelectedValue**|Visual Studio ustawia tę właściwość do oryginalnego kolumny z **źródeł danych** okna.<br /><br /> Jeśli trzeba dokonać korekty, zmień wartość na kolumnę klucza obcego w pokrewnej tabeli.|  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)