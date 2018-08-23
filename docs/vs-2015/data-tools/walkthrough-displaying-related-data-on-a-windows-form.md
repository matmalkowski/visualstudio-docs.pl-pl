---
title: 'Wskazówki: Wyświetlanie powiązanych danych w formularzu Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- master-details lists, displaying on Windows Forms
- data [Visual Studio], master-details
- displaying tables, related data
- displaying table data
- displaying table information
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: be86fa89cd35ff55ed9e454c9453b4d2684f311d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42694263"
---
# <a name="walkthrough-displaying-related-data-on-a-windows-form"></a>Wskazówki: wyświetlanie powiązanych danych na formularzu systemu Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W wielu scenariuszach aplikacji chcesz pracować z danych, które pochodzą z więcej niż jednej tabeli i często danych z powiązanych tabel. Oznacza to, że chcesz pracować z relacją nadrzędny podrzędny. Na przykład można utworzyć formularz, gdzie wybierając rekord klienta Wyświetla zamówień tego klienta. Wyświetlania powiązanych rekordów w formularzu odbywa się przez ustawienie <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość elementu podrzędnego <xref:System.Windows.Forms.BindingSource> do elementu nadrzędnego <xref:System.Windows.Forms.BindingSource> (nie tabeli podrzędnej) i ustawienie <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwość elementu podrzędnego <xref:System.Windows.Forms.BindingSource> do relacji danych tabele nadrzędnymi i podrzędnymi, łączy ze sobą.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie **aplikacji Windows** projektu.  
  
-   Tworzenie i konfigurowanie zestawu danych w aplikacji na podstawie `Customers` i `Orders` tabele w bazie danych Northwind za pomocą [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Dodawanie formantów do wyświetlania danych z `Customers` tabeli.  
  
-   Dodawanie formantów do wyświetlania `Orders` na podstawie wybranej `Customer`.  
  
-   Testowanie aplikacji, wybieranie różnych klientów i weryfikowanie, czy dla zaznaczonego klienta wyświetlane są poprawne zamówienia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu, należy:  
  
-   Dostęp do przykładowej bazy danych Northwind. Aby skonfigurować przykładowych baz danych, zobacz [porady: Instalowanie przykładowych baz danych](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie **aplikacji Windows**.  
  
#### <a name="to-create-the-windows-application-project"></a>Aby utworzyć projekt aplikacji Windows  
  
1.  Z **pliku** menu, Utwórz nowy projekt.  
  
2.  Nadaj projektowi nazwę `RelatedDataWalkthrough`.  
  
3.  Wybierz **aplikacji Windows** i kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **RelatedDataWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="creating-the-data-source"></a>Tworzenie źródła danych  
 W tym kroku jest tworzony zestaw danych na podstawie `Customers` i `Orders` tabel w bazie danych Northwind.  
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.  
  
3.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.  
  
4.  Na **wybierz połączenie danych** wykonaj strony, jedną z następujących czynności:  
  
    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
         —lub—  
  
    -   Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okno dialogowe.  
  
5.  Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.  
  
6.  Kliknij przycisk **dalej** na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** strony.  
  
7.  Rozwiń **tabel** węzeł **wybierz obiekty bazy danych** strony.  
  
8.  Wybierz **klientów** i **zamówienia** tabel, a następnie kliknij **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu i **klientów** tabela zostanie wyświetlona w **źródeł danych** okna.  
  
## <a name="creating-controls-to-display-data-from-the-customers-table"></a>Tworzenie formantów do wyświetlania danych z tabeli Customers  
  
#### <a name="to-create-controls-to-display-the-customer-data-parent-records"></a>Aby utworzyć formanty do wyświetlania danych klientów (rekordów nadrzędnych)  
  
1.  W **źródeł danych** wybierz **klientów** tabeli, a następnie kliknij strzałkę listy rozwijanej.  
  
2.  Wybierz **szczegóły** z menu.  
  
3.  Przeciągnij główny **klientów** węzła z **źródeł danych** okna na początku **Form1**.  
  
     Formanty powiązane z danymi z etykietami opisowymi są wyświetlane w formularzu, oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.  
  
## <a name="creating-controls-to-display-data-from-the-orders-table"></a>Tworzenie formantów do wyświetlania danych z tabeli Orders  
 ![Okno źródeł danych, przedstawiający relacji](../data-tools/media/datasources2.gif "DataSources2")  
  
#### <a name="to-create-controls-to-display-the-orders-for-each-customer-child-records"></a>Aby utworzyć formant do wyświetlania zamówień dla każdego klienta (rekordy podrzędne)  
  
-   W **źródeł danych** okna, rozwiń węzeł **klientów** węzła i zaznacz ostatnią kolumnę **klientów** tabeli, która jest rozszerzalnym węzłem **zamówienia** węzeł i przeciągnij go do dołu **Form1**.  
  
     A <xref:System.Windows.Forms.DataGridView> zostanie dodany do formularza i nowe <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource`) i TableAdapter (`OrdersTableAdapter`) są dodawane do zasobnika składnika.  
  
    > [!NOTE]
    >  Otwórz [okno właściwości](../ide/reference/properties-window.md) i wybierz **OrdersBindingSource**. Sprawdzanie <xref:System.Windows.Forms.BindingSource.DataSource%2A> i <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości, aby zobaczyć, jak powiązanie jest skonfigurowane do wyświetlania powiązanych rekordów. <xref:System.Windows.Forms.BindingSource.DataSource%2A> Ustawiono `CustomersBindingSource` (tabeli nadrzędnej <xref:System.Windows.Forms.BindingSource>), a nie `Orders` tabeli. <xref:System.Windows.Forms.BindingSource.DataMember%2A> Właściwość jest ustawiona na `FK_Orders_Customers`, czyli nazwę <xref:System.Data.DataRelation> obiekt, który wiąże ze sobą tabele.  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Naciśnij klawisz F5, aby uruchomić aplikację.  
  
2.  Wybierz różnych klientów, za pomocą **CustomersBindingNavigator** Aby zweryfikować poprawne zamówienia są wyświetlane w <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu głównego/szczegółowego formularza. Jest ulepszeniem, których można dokonać w tym przewodniku:  
  
-   Filtrowanie `Customers` rekordów, dodając parametry do `Customers` tabeli. Aby to zrobić, wybierz dowolną kontrolkę, która wyświetla dane z `Customers` tabelę, kliknij tag inteligentny, a następnie wybierz **Dodaj zapytanie**. Wykonaj [kryteria Konstruktor — okno dialogowe Wyszukiwanie](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d). Aby uzyskać więcej informacji, zobacz [porady: dodawanie zapytań parametrycznych do aplikacji Windows Forms](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Okno źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)   
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)   
 [Porady: wyświetlanie powiązanych danych w Windows Forms aplikacji](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [BindingSource, składnik — omówienie](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)   
 [BindingNavigator, kontrolka — omówienie](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0)