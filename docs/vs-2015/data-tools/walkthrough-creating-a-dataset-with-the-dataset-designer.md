---
title: 'Wskazówki: Tworzenie zestawu danych za pomocą Projektanta obiektów Dataset | Dokumentacja firmy Microsoft'
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
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7c17a93a5d250ce620c37a2a0a89472bf760750b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684893"
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Wskazówki: tworzenie zestawu danych za pomocą narzędzia Projektant obiektów Dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku zostanie utworzony zestaw danych przy użyciu **Projektanta obiektów Dataset**. Spowoduje przejście przez proces tworzenia nowego projektu i dodawanie nowej **DataSet** elementu do niego. Nauczysz się, w jaki sposób tworzyć tabele na podstawie tabel w bazie danych bez używania kreatora.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie nowego **aplikacji Windows** projektu.  
  
-   Dodawanie pustego **DataSet** do projektu.  
  
-   Tworzenie i konfigurowanie źródła danych w aplikacji, tworząc zestaw danych o **Projektanta obiektów Dataset**.  
  
-   Tworzenie połączenia z bazą danych Northwind w **Eksploratora serwera**.  
  
-   Tworzenie tabel z elementami TableAdapter w zestawie danych na podstawie tabel istniejących w bazie danych.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu, należy:  
  
-   Dostęp do przykładowej bazy danych Northwind (wersja programu SQL Server lub Access). Aby uzyskać więcej informacji, zobacz [porady: Instalowanie przykładowych baz danych](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application-project"></a>Tworzenie nowego projektu aplikacji systemu Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Aby utworzyć nowy projekt aplikacji Windows  
  
1.  Z **pliku** menu, Utwórz nowy projekt.  
  
2.  Wybierz język programowania w **typów projektów** okienka.  
  
3.  Kliknij przycisk **aplikacji Windows** w **szablony** okienka.  
  
4.  Nadaj projektowi nazwę `DatasetDesignerWalkthrough`, a następnie kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Spowoduje to dodanie projektu **Eksploratora rozwiązań** i pojawi się nowy formularz w projektancie.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Dodawanie nowego zestawu danych do aplikacji  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Aby dodać nowy zestaw danych do projektu  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
     **Dodaj nowy element** pojawi się okno dialogowe.  
  
2.  W **szablony** pole **Dodaj nowy element** okno dialogowe, kliknij przycisk **zestawu danych**.  
  
3.  Nazwij zestaw danych `NorthwindDataset`, a następnie kliknij przycisk **Dodaj**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Spowoduje to dodanie pliku o nazwie **NorthwindDataset.xsd** do projektu, a następnie otwórz go w **Projektanta obiektów Dataset**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Tworzenie połączenia danych w Eksploratorze serwera  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Aby utworzyć połączenie z bazą danych Northwind  
  
1.  Na **widoku** menu, kliknij przycisk **Eksploratora serwera**.  
  
2.  W **Eksploratora serwera**, kliknij przycisk **Połącz z bazą danych** przycisku.  
  
3.  Utwórz połączenie z przykładową bazą danych Northwind.  
  
    > [!NOTE]
    >  W tym przewodniku połączenie można utworzyć z wersją bazy danych Northwind przeznaczoną dla programu SQL Server lub Access.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Tworzenie tabel w zestawie danych  
 W tym rozdziale wyjaśniono, jak dodawać tabele do zestawu danych.  
  
#### <a name="to-create-the-customers-table"></a>Aby utworzyć tabelę Customers  
  
1.  Rozwiń połączenie danych utworzone w **Eksploratora serwera**, a następnie rozwiń węzeł **tabel** węzła.  
  
2.  Przeciągnij **klientów** tabeli **Eksploratora serwera** na **Projektanta obiektów Dataset**.  
  
     A **klientów** tabelę danych i **CustomersTableAdapter** są dodawane do zestawu danych.  
  
#### <a name="to-create-the-orders-table"></a>Aby utworzyć tabelę Orders  
  
-   Przeciągnij **zamówienia** tabeli **Eksploratora serwera** na **Projektanta obiektów Dataset**.  
  
     **Zamówienia** tabeli danych **OrdersTableAdapter**oraz relacje danych między **klientów** i **zamówienia** tabele są dodawane do zestaw danych.  
  
#### <a name="to-create-the-orderdetails-table"></a>Aby utworzyć tabelę OrderDetails  
  
-   Przeciągnij **Orderdetails** tabeli **Eksploratora serwera** na **Projektanta obiektów Dataset**.  
  
     **Orderdetails** tabeli danych **Orderdetailstableadapter**oraz relacje danych między **zamówienia** i **Orderdetails** tabel zostaną dodane do zestawu danych.  
  
## <a name="next-steps"></a>Następne kroki  
  
### <a name="to-add-functionality-to-your-application"></a>Aby dodać funkcje do aplikacji  
  
-   Zapisz zestaw danych.  
  
-   Zaznacz elementy w **źródeł danych** okna i przeciągnij je na formularzu. Aby uzyskać więcej informacji, zobacz [formanty powiązania formularzy Windows do danych w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Dodaj więcej zapytań do elementów TableAdapter. Aby uzyskać więcej informacji, zobacz [porady: tworzenie zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Dodaj logikę walidacji do zdarzeń <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> tabel danych w zestawie danych. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)