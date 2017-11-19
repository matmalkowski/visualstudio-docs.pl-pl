---
title: Zapisywanie danych w bazie danych (wiele tabel) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: e6ed4bf0cb025feb2a4f52084857d9bdf5394770
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2017
---
# <a name="save-data-to-a-database-multiple-tables"></a>Zapisywanie danych w bazie danych (wiele tabel)
Jest jedną z najbardziej typowych scenariuszy w aplikacjach do wyświetlania danych formularza w aplikacji systemu Windows, edycję danych i wysyłać zaktualizowane dane w bazie danych. W tym przewodniku tworzy formularz, który wyświetla dane z powiązanych tabel i przedstawia sposób edytowania rekordów i zapisać zmiany w bazie danych. W tym przykładzie użyto `Customers` i `Orders` tabele w bazie danych Northwind.  
  
 Dane można zapisać w aplikacji w bazie danych, wywołując `Update` metody TableAdapter. Przeciągnięcie tabel z **źródeł danych** okna w formularzu kodu, które są wymagane w celu zapisywania danych zostanie automatycznie dodana. Dodatkowe tabele, które są dodawane do formularza wymaga ręcznego dodawania tego kodu. W tym przewodniku przedstawiono sposób dodawania kod, aby zapisać aktualizacje z więcej niż jednej tabeli.  
  
> [!NOTE]
>  Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych w pomocy w zależności od ustawienia active lub edition, którego używasz. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie nowego **aplikacji Windows Forms** projektu.  
  
-   Tworzenie i konfigurowanie źródła danych do aplikacji z [Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Określa elementy [Data Sources — okno](add-new-data-sources.md). Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Tworzenie formantów powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna na formularzu.  
  
-   Modyfikowanie kilka rekordów w każdej tabeli w zestawie danych.  
  
-   Modyfikowanie kodu do odesłania zaktualizowanych danych w zestawie danych do bazy danych.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.  
  
1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania wersjach programu SQL Server](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **magazynu danych i przetwarzania** obciążenia, lub jako poszczególnych składników.  
  
2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:  

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowej kwerendy...** .  

       Zostanie otwarte okno edytora zapytań.  

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.  

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.  

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.  
  
## <a name="create-the-windows-forms-application"></a>Tworzenie aplikacji formularzy systemu Windows  
 Pierwszym krokiem jest utworzenie **aplikacji Windows Forms**. Przypisanie nazwy do projektu jest opcjonalne w tym kroku, ale firma Microsoft będzie nadaj mu nazwę, ponieważ projekt będzie zapisać później.  
  
#### <a name="to-create-the-new-windows-forms-application-project"></a>Aby utworzyć nowy projekt aplikacji formularzy systemu Windows  
  
1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .  
  
2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.  

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.  

4. Nazwij projekt **UpdateMultipleTablesWalkthrough**, a następnie wybierz pozycję **OK**. 
  
     **UpdateMultipleTablesWalkthrough** projektu jest tworzony i dodawany do **Eksploratora rozwiązań**.  
  
## <a name="create-the-data-source"></a>Utwórz źródło danych  
 Spowoduje to utworzenie źródła danych z bazy danych Northwind przy użyciu **Kreator konfiguracji źródła danych**. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje dotyczące konfigurowania przykładowej bazy danych Northwind, zobacz [porady: Instalowanie przykładowe bazy danych](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Na **danych** menu, wybierz opcję **Pokaż źródeł danych**.  
  
2.  W **źródeł danych** wybierz**Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
3.  Na **wybierz typ źródła danych** ekranu wybierz **bazy danych**, a następnie wybierz **dalej**.  
  
4.  Na **wybierz połączenie danych** wykonaj ekranu, jedną z następujących czynności:  
  
    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
         —lub—  
  
    -   Wybierz **nowe połączenie** otworzyć **połączenia Dodawanie i modyfikowanie** okno dialogowe.  
  
5.  Jeśli baza danych wymaga hasła, wybierz opcję, aby obejmować dane poufne, a następnie wybierz **dalej**.  
  
6.  Na **zapisać parametry połączenia w pliku konfiguracji aplikacji**, wybierz pozycję **dalej**.  
  
7.  Na **wybierz obiekty bazy danych**ekranu, a następnie rozwiń **tabel** węzła.  
  
8.  Wybierz **klientów** i **zamówień** tabel, a następnie wybierz **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu, i tabele są wyświetlane **źródeł danych** okna.  
  
## <a name="set-the-controls-to-be-created"></a>Ustaw opcje do utworzenia  
 W ramach tego przewodnika, dane w `Customers` tabela znajduje się w **szczegóły** układu, w którym dane są wyświetlane w pojedynczych formantów. Dane z `Orders` tabela znajduje się w **siatki** układu, która jest wyświetlana w <xref:System.Windows.Forms.DataGridView> formantu.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Aby ustawić typ listy elementów w oknie źródeł danych  
  
1.  W **źródeł danych** okna, rozwiń węzeł **klientów** węzła.  
  
2.  Na **klientów** węzła, wybierz opcję **szczegóły** z listy sterowania, aby zmienić kontrolę nad **klientów** tabeli do pojedynczych formantów. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="create-the-data-bound-form"></a>Tworzenie formularza z danymi  
 Formanty powiązane z danymi można utworzyć, przeciągając elementy z **źródeł danych** okna na formularzu.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć formantów powiązanych z danymi  
  
1.  Przeciągnij głównym **klientów** węzła z **źródeł danych** okna na **Form1**.  
  
     Formanty powiązane z danymi z opisowe etykiety są wyświetlane w formularzu, wraz z paska narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania rekordów. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane na pasku składnika.  
  
2.  Przeciągnij pokrewny **zamówień** węzła z **źródeł danych** okna na **Form1**.  
  
    > [!NOTE]
    >  Pokrewny **zamówień** węzeł znajduje się poniżej **faksów** kolumny i jest elementem podrzędnym **klientów** węzła.  
  
     A <xref:System.Windows.Forms.DataGridView> kontroli i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania rekordy są wyświetlane w formularzu. `OrdersTableAdapter` i <xref:System.Windows.Forms.BindingSource> są wyświetlane na pasku składnika.  
  
## <a name="add-code-to-update-the-database"></a>Dodaj kod, aby zaktualizować bazę danych  
 Można zaktualizować bazy danych przez wywołanie metody `Update` metody **klientów** i **zamówień** TableAdapters. Domyślnie program obsługi zdarzeń dla **zapisać** przycisku<xref:System.Windows.Forms.BindingNavigator> jest dodawana do kodu formularza w celu wysyłania aktualizacji do bazy danych. Ta procedura modyfikuje kod, aby wysyłać aktualizacje w odpowiedniej kolejności. Eliminuje to możliwość wywoływanie błędy integralności referencyjnej. Kod implementuje również obsługa błędów przez zawijania wywołania aktualizacji w bloku try-catch. Można zmodyfikować kod do potrzeb aplikacji.  
  
> [!NOTE]
>  Dla uzyskania przejrzystości ten przewodnik nie używać transakcji. Jednak Jeśli aktualizujesz dwa lub więcej powiązanych tabel, obejmują całą logikę aktualizacji w obrębie transakcji. Transakcja jest procesem, który gwarantuje, że wszystkie powiązane zmiany w bazie danych są pomyślnie przed wszelkie zmiany zostaną zatwierdzone. Aby uzyskać więcej informacji, zobacz [transakcji i współbieżność](/dotnet/framework/data/adonet/transactions-and-concurrency).  
  
#### <a name="to-add-update-logic-to-the-application"></a>Aby dodać logikę aktualizacji do aplikacji  
  
1.  Wybierz **zapisać** znajdującego się na <xref:System.Windows.Forms.BindingNavigator>. Zostanie otwarty w edytorze kodu `bindingNavigatorSaveItem_Click` obsługi zdarzeń.  
  
2.  Zastąp kod w obsłudze zdarzeń, aby wywołać `Update` metody TableAdapters pokrewne. Poniższy kod tworzy pierwsze trzy tabele danych tymczasowych do przechowywania zaktualizowane informacje dla każdego <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added>, i <xref:System.Data.DataRowState.Modified>). Następnie aktualizacje są uruchamiane w odpowiedniej kolejności. Kod powinien wyglądać następująco:  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Wybierz **F5**.  
  
2.  Niektóre zmiany w danych jednego lub wielu rekordów w każdej tabeli.  
  
3.  Wybierz **zapisać** przycisku.  
  
4.  Sprawdź wartości w bazie danych, aby sprawdzić, czy zmiany zostały zapisane.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie danych w bazie danych](../data-tools/save-data-back-to-the-database.md)