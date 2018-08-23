---
title: 'Wskazówki: Wyświetlanie danych w formularzu Windows | Dokumentacja firmy Microsoft'
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
- Windows applications, displaying data
- data binding, Windows Forms
- data [Visual Studio], displaying on Windows Forms
- forms, displaying data
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3decf0da6dd6d16c0128fdaeedf2fcd0cea94871
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680357"
---
# <a name="walkthrough-displaying-data-on-a-windows-form"></a>Wskazówki: wyświetlanie danych na formularzach systemu Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jednym z najbardziej typowych scenariuszy w tworzeniu aplikacji jest do wyświetlania danych w formularzu w aplikacji Windows. Można wyświetlić dane w formularzu przez przeciąganie elementów z [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) na formularz. Ten poradnik tworzy prosty formularz, który wyświetla dane z pojedynczej tabeli w kilku pojedynczych formantów. W tym przykładzie użyto `Customers` tabeli w bazie danych Northwind.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie nowego **aplikacji Windows** projektu.  
  
-   Tworzenie i konfigurowanie zestawu danych za pomocą [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Wybieranie formantu do utworzenia w formularzu podczas przeciągania elementów z **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Tworzenie kontrolki powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu, należy:  
  
-   Dostęp do przykładowej bazy danych Northwind. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie przykładowych baz danych](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-windows-application"></a>Tworzenie aplikacji Windows  
 Pierwszym krokiem jest utworzenie **aplikacji Windows** projektu.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Aby utworzyć nowy projekt aplikacji Windows  
  
1.  Z **pliku** menu, Utwórz nowy projekt.  
  
2.  Nadaj projektowi nazwę `DisplayingDataonaWindowsForm`.  
  
3.  Wybierz **aplikacji Windows** i kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **DisplayingDataonaWindowsForm** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="creating-the-data-source"></a>Tworzenie źródła danych  
 Spowoduje to utworzenie źródła danych przy użyciu **Kreatora konfiguracji źródła danych** na podstawie `Customers` tabeli w bazie danych Northwind. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje na temat konfigurowania przykładowej bazy danych Northwind, zobacz [porady: Instalowanie przykładowych baz danych](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.  
  
3.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.  
  
4.  Na **wybierz połączenie danych** wykonaj strony, jedną z następujących czynności:  
  
    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
         —lub—  
  
    -   Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okno dialogowe...  
  
5.  Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.  
  
6.  Kliknij przycisk **dalej** na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** strony.  
  
7.  Rozwiń **tabel** węzeł **wybierz obiekty bazy danych** strony.  
  
8.  Wybierz **klientów** tabeli, a następnie kliknij przycisk **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu i **klientów** tabela zostanie wyświetlona w **źródeł danych** okna.  
  
## <a name="setting-the-controls-to-be-created"></a>Określa, który ma zostać utworzony  
 W tym przewodniku dane będą znajdować się w **szczegóły** układu, w którym dane są wyświetlane w poszczególnych formantów. (Alternatywnym podejściem jest domyślnie **siatki** układu, w którym dane są wyświetlane w <xref:System.Windows.Forms.DataGridView> kontroli.)  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Aby ustawić upuszczany typ elementów w oknie źródeł danych  
  
1.  Rozwiń **klientów** w węźle **źródeł danych** okna.  
  
2.  Zmień upuszczany typ **klientów** do tabeli **szczegóły** , wybierając **szczegóły** z listy rozwijanej na **klientów** węzła. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Zmiana **CustomerID** kolumny upuszczany typ na etykietę, wybierając **etykiety** na liście kontrolek na **CustomerID** węzła.  
  
## <a name="creating-the-form"></a>Tworzenie formularza  
 Tworzenie formantów powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć formanty powiązane z danymi formularza  
  
-   Przeciągnij główny **klientów** węzła z **źródeł danych** okna na formularzu.  
  
     Formanty powiązane z danymi z etykietami opisowymi są wyświetlane w formularzu, oraz pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
  
#### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
-   Naciśnij F5.  
  
-   Przejdź rekordów przy użyciu <xref:System.Windows.Forms.BindingNavigator> kontroli.  
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza Windows powiązane z danymi. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:  
  
-   Dodawanie funkcji wyszukiwania do formularza. Aby uzyskać więcej informacji, zobacz [porady: dodawanie zapytań parametrycznych do aplikacji Windows Forms](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Dodawanie funkcji do wysyłania aktualizacji w bazie danych. Aby uzyskać więcej informacji, zobacz [wskazówki: zapisywanie danych do bazy danych (Single Table)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
-   Dodawanie `Orders` tabeli do zestawu danych, wybierając **Konfigurowanie zestawu danych za pomocą kreatora** z poziomu **źródeł danych** okna. Następnie można dodać formanty, które wyświetlają pokrewne dane, przeciągając **zamówienia** węzeł (poniżej jednej **faks** kolumny w **klientów** tabeli) na formularz. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie powiązanych danych w aplikacji Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)   
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)