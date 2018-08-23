---
title: 'Wskazówki: Łączenie z danymi w pliku lokalnej bazy danych (Windows Forms) | Dokumentacja firmy Microsoft'
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
- databases, connecting to
- local data, SQL Express
- SQL Express, walkthroughs
- SQL Express, connecting
- data [Visual Studio], local
- data [Visual Studio], connecting to SQL Express
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 9b2d17c5ed86e37d3c674ef9238702cd8557a90f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42689028"
---
# <a name="walkthrough-connecting-to-data-in-a-local-database-file-windows-forms"></a>Wskazówki: łączenie z danymi w pliku lokalnej bazy danych (formularze systemu Windows)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz szybko i łatwo wyświetlać dane z lokalnego pliku bazy danych w swojej aplikacji, tworząc zestaw danych, a następnie dodając powiązane z danymi formanty do swojej aplikacji. W tym instruktażu będą wyświetlane dane z pliku lokalnej bazy danych, który został utworzony, wykonując kroki opisane w [utworzyć bazę danych SQL przy użyciu projektanta](../data-tools/create-a-sql-database-by-using-a-designer.md). Po utworzeniu projektu Windows Forms będziesz łączyć się z bazą danych i określać, że dane z tabeli Customers są wyświetlane w siatce danych na formularzu przeznaczonym do aplikacji.  
  
 Kiedy tworzysz bazę danych w Visual Studio 2013, używany jest silnik SQL Server Express LocalDB w celu uzyskiwania dostępu do pliku bazy danych (mdf) w SQL Server 2012. We wcześniejszych wersjach programu Visual Studio do uzyskiwania dostępu do pliku bazy danych (mdf) jest używany aparat SQL Server Express. Zobacz [dane lokalne — Przegląd](../data-tools/local-data-overview.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
 Ten instruktaż zawiera następujące zagadnienia:  
  
-   [Tworzenie i konfigurowanie zestawu danych](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [Dodawanie formantów powiązanych z danymi](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Do przeprowadzenia tego instruktażu, potrzebny jest dostęp do bazy danych SampleDatabase.mdf, którą tworzysz przez ukończenie [utworzyć bazę danych SQL przy użyciu projektanta](../data-tools/create-a-sql-database-by-using-a-designer.md).  
  
##  <a name="BKMK_CreateDataset"></a> Tworzenie i konfigurowanie zestawu danych  
  
#### <a name="to-create-and-configure-a-dataset"></a>Aby utworzyć i skonfigurować zestaw danych  
  
1.  Utwórz projekt Windows Forms i nadaj mu nazwę **nazwę ConnectLocalData**.  
  
     Zobacz [aplikacje klienckie](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
2.  Jeśli **źródeł danych** nie wyświetli się okno, wybierz klawisze Shift-Alt-D lub na pasku menu wybierz **widoku**, **Windows inne**, **Pokaż źródła danych**.  
  
3.  W **źródeł danych** oknie Wybierz **Dodaj nowe źródło danych** łącza.  
  
     W **Kreatora konfiguracji źródła danych**, wybierz **dalej** przycisk dwa razy, aby zaakceptować ustawienia domyślne.  
  
4.  Na **wybierz połączenie danych** wybierz **nowe połączenie** przycisku.  
  
     **Wybierz źródło danych** pojawi się okno dialogowe.  
  
5.  W **źródła danych** wybierz **plik bazy danych programu Microsoft SQL Server**, a następnie wybierz **Kontynuuj** przycisku.  
  
     **Dodaj połączenie** pojawi się okno dialogowe.  
  
6.  W **nazwa pliku bazy danych** Określ plik, który został utworzony przez zakończenie [utworzyć bazę danych SQL przy użyciu projektanta](../data-tools/create-a-sql-database-by-using-a-designer.md), lub wybierz **Przeglądaj** przycisk, a następnie zlokalizuj Ten plik.  
  
     Domyślnie plik znajduje się w użytkowników\\*Twojekonto*\Documents\Visual Studio *wersji*\Projects\SampleDatabaseWalkthrough\SampleDatabaseWalkthrough.  
  
7.  W obszarze **Zaloguj się na serwerze**, zaakceptuj wartości domyślne, wybierz pozycję **OK** przycisk, a następnie wybierz **dalej** przycisku.  
  
    > [!NOTE]
    >  Kiedy łączysz się z lokalnym plikiem bazy danych, możesz utworzyć kopię bazy danych w swoim projekcie lub połączyć się z plikiem bazy danych w jego bieżącej lokalizacji. Zobacz [porady: Zarządzanie plikami danych lokalnych w projekcie](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
8.  W oknie dialogowym wybierz **tak** można skopiować plik bazy danych do projektu.  
  
9. Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz **dalej** przycisku.  
  
10. Na **wybierz obiekty bazy danych** rozwiń **tabel** węzła, wybierz opcję **klientów** i **zamówienia** pola wyboru, a następnie Wybierz **Zakończ** przycisku.  
  
     **SampleDatabaseDataSet** zostanie dodany do projektu, a **klientów** i **zamówienia** tabele są wyświetlane w **źródeł danych** okna.  
  
##  <a name="BKMK_AddCtrls"></a> Dodawanie formantów powiązanych z danymi  
  
#### <a name="to-add-data-bound-controls"></a>Aby dodać formanty powiązane z danymi  
  
1.  Przenieś główny **klientów** węzła z **źródeł danych** okna na **Form1**.  
  
     A <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w formularzu. A [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.  
  
2.  Aby uruchomić aplikację i wyświetlić dane, które dodano w poprzednim poradniku, wybierz klawisz F5.  
  
3.  Wybierz żółtą ikonę (![przycisk Dodaj w formularzu Windows](../data-tools/media/addrecord.png "AddRecord")), a następnie dodać rekord klienta i następnie zapisz zmiany, wybierając ikonę dyskietki (![przycisku Zapisz w formularzu Windows](../data-tools/media/saveinwf.png "SaveInWF")).  
  
4.  Usuń rekord, który właśnie utworzyłeś wybierając go, a następnie wybierając czerwoną ikonę usuwania (![przycisk Usuń w formularzu Windows](../data-tools/media/deleterecord.png "DeleteRecord")).  
  
## <a name="next-steps"></a>Następne kroki  
 Można tworzyć lub modyfikować obiekty w zestawie danych, jeżeli otworzysz źródło danych w [tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md). Możesz również dodać logikę walidacji do <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> wydarzenia tabel danych w zestawie danych. Zobacz [sprawdzanie poprawności danych w zestawach danych](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dane lokalne — Przegląd](../data-tools/local-data-overview.md)   
 [Porady: Zarządzanie plikami danych lokalnych w projekcie](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)