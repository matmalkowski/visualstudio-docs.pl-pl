---
title: 'Wskazówki: Tworzenie TableAdapter z wieloma zapytaniami | Dokumentacja firmy Microsoft'
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
- TableAdapter queries, creating
- data [Visual Studio], TableAdapters
- TableAdapters, creating
- data [Visual Studio], walkthroughs
- queries [Visual Studio], TableAdapters
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e48750cf876f561b25802fd20b1e270215a1b605
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683946"
---
# <a name="walkthrough-creating-a-tableadapter-with-multiple-queries"></a>Wskazówki: tworzenie TableAdapter z wieloma zapytaniami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu utworzysz TableAdapter w zestawie danych za pomocą [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). Przewodnik przeprowadzi Cię przez proces tworzenia drugiego zapytania w [TableAdapter](../data-tools/tableadapter-overview.md) przy użyciu [edytowanie TableAdapters](../data-tools/editing-tableadapters.md) w ramach [Projektanta obiektów Dataset](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie nowego **aplikacji Windows** projektu.  
  
-   Tworzenie i konfigurowanie źródła danych w aplikacji, tworząc zestaw danych o **Kreatora konfiguracji źródła danych**.  
  
-   Otwieranie nowego zestawu danych w **Projektanta obiektów Dataset**.  
  
-   Dodawanie zapytań do TableAdapter za pomocą **Kreatora konfiguracji zapytania TableAdapter**.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu, należy:  
  
-   Dostęp do przykładowej bazy danych Northwind (wersja programu SQL Server lub Access). Aby uzyskać więcej informacji, zobacz [porady: Instalowanie przykładowych baz danych](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application"></a>Tworzenie nowej aplikacji Windows  
 Pierwszym krokiem jest utworzenie aplikacji Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Aby utworzyć nowy projekt aplikacji Windows  
  
1.  W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], z **pliku** menu, Utwórz nowy projekt.  
  
2.  Wybierz język programowania w **typów projektów** okienka.  
  
3.  Kliknij przycisk **aplikacji Windows** w **szablony** okienka.  
  
4.  Nadaj projektowi nazwę `TableAdapterQueriesWalkthrough`, a następnie kliknij przycisk **OK**.  
  
     Program Visual Studio dodaje projekt do **Eksploratora rozwiązań** i wyświetla nowy formularz w projektancie.  
  
## <a name="creating-a-database-data-source-with-a-tableadapter"></a>Tworzenie źródła danych bazy danych za pomocą TableAdapter  
 Spowoduje to utworzenie źródła danych przy użyciu **Kreatora konfiguracji źródła danych** na podstawie `Customers` tabeli w bazie danych Northwind. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje na temat konfigurowania przykładowej bazy danych Northwind, zobacz [porady: Instalowanie przykładowych baz danych](../data-tools/how-to-install-sample-databases.md).  
  
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
  
8.  Wybierz **klientów** tabeli, a następnie kliknij przycisk **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu i **klientów** tabela zostanie wyświetlona w **źródeł danych** okna.  
  
## <a name="opening-the-dataset-in-the-dataset-designer"></a>Otwieranie zestawów danych w Projektancie obiektów Dataset  
  
#### <a name="to-open-the-dataset-in-the-dataset-designer"></a>Aby otworzyć zestaw danych w Projektancie obiektów Dataset  
  
1.  Kliknij prawym przyciskiem myszy **NorthwindDataset** w **źródeł danych** okna.  
  
2.  W menu skrótów wybierz **Edycja zestawu danych za pomocą projektanta**.  
  
     Zostanie otwarty obiekt NorthwindDataset w **Projektanta obiektów Dataset**.  
  
## <a name="adding-a-second-query-to-the-customerstableadapter"></a>Dodawane drugiego zapytania do CustomersTableAdapter  
 Kreator utworzył zestaw danych o **klientów** tabelę danych i **CustomersTableAdapter**. Tej części instruktażu dodawane jest drugie zapytanie, aby **CustomersTableAdapter**.  
  
#### <a name="to-add-a-query-to-the-customerstableadapter"></a>Aby dodać zapytanie do CustomersTableAdapter  
  
1.  Przeciągnij **zapytania** z **zestawu danych** karcie **przybornika** na **klientów** tabeli.  
  
     [Edytowanie TableAdapters](../data-tools/editing-tableadapters.md) zostanie otwarty.  
  
2.  Wybierz **użyj instrukcji SQL**, a następnie kliknij przycisk **dalej**.  
  
3.  Wybierz **SELECT, która zwraca wiersze**, a następnie kliknij przycisk **dalej**.  
  
4.  Dodaj klauzulę WHERE do zapytania, tak aby wyglądało:  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Jeśli używasz wersji dostępu do bazy danych Northwind, należy zastąpić @City parametr znakiem zapytania. (`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`)  
  
5.  Na **Wybierz metody do generowania** strony, nazwij **wypełnienia DataTable** metoda `FillByCity`.  
  
    > [!NOTE]
    >  Metoda **róć tabelę DataTable** nie jest używany w tym przewodniku, więc możesz wyczyścić pole wyboru lub pozostawić nazwę domyślną.  
  
6.  Kliknij przycisk **dalej** i Zakończ działanie kreatora.  
  
     **FillByCity** zapytania jest dodawany do **CustomersTableAdapter**.  
  
## <a name="adding-code-to-execute-the-additional-query-on-the-form"></a>Dodawanie kodu do wykonania dodatkowego zapytania na formularzu  
  
#### <a name="to-execute-the-query"></a>Aby wykonać zapytanie  
  
1.  Wybierz **Form1** w **Eksploratora rozwiązań**i kliknij przycisk **Projektant widoków**.  
  
2.  Przeciągnij **klientów** węzła z **źródeł danych** okna **Form1**.  
  
3.  Zmień na widok kodu wybierając **kodu** z **widoku** menu.  
  
4.  Zastąp kod w `Form1_Load` programu obsługi zdarzeń przy użyciu następujących do uruchomienia `FillByCity` zapytania.  
  
     [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
     [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
## <a name="running-the-application"></a>Uruchamianie aplikacji  
  
#### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
-   Naciśnij F5.  
  
-   Siatka jest wypełniana klientami z ustawieniem `City` wartość `Seattle`.  
  
## <a name="next-steps"></a>Następne kroki  
  
### <a name="to-add-functionality-to-your-application"></a>Aby dodać funkcje do aplikacji  
  
-   Dodaj <xref:System.Windows.Forms.TextBox> kontroli i <xref:System.Windows.Forms.Button> kontroli i przekaż wartość w polu tekstowym do zapytania. (`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`).  
  
-   Dodaj logikę walidacji do <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> wydarzenia tabel danych w zestawie danych. Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Zobacz też  
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)   
 [Tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [Porady: tworzenie zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)