---
title: Obsługiwanie wyjątku współbieżności
ms.date: 09/11/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b7895a15dcc7536ee29317a2c02546bf125a6b4a
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117202"
---
# <a name="handle-a-concurrency-exception"></a>Obsługiwanie wyjątku współbieżności
Wyjątków współbieżności (<xref:System.Data.DBConcurrencyException>) są wywoływane, gdy dwóch użytkowników próba zmiany tych samych danych w bazie danych, w tym samym czasie. W tym przewodniku tworzenia aplikacji systemu Windows, która ilustruje sposób catch <xref:System.Data.DBConcurrencyException>, odszukaj wiersz, który spowodował błąd i Dowiedz się strategię sposobu jego obsługa.

 W tym przewodniku przeprowadza użytkownika przez następujący proces:

1.  Utwórz nową **aplikacji Windows Forms** projektu.

2.  Utwórz nowy zestaw danych oparty na Northwind `Customers` tabeli.

3.  Tworzenie formularza z <xref:System.Windows.Forms.DataGridView> do wyświetlania danych.

4.  Wypełnianie zestawu danych danymi z `Customers` tabeli w bazie danych Northwind.

5.  Użyj **Pokaż dane tabeli** w narzędziu **Eksploratora serwera** dostępu `Customers` danych i zmiany rekord tabeli.

6.  Zmień ten sam rekord na inną wartość, zaktualizować dataset i próba zapisania zmian w bazie danych, co powoduje błąd współbieżności są zgłaszane.

7.  Błąd catch, wyświetlania różnych wersji rekordu, co pozwala na określanie, czy kontynuować i zaktualizować bazę danych lub Anuluj aktualizację.

## <a name="prerequisites"></a>Wymagania wstępne
W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.

1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [strony pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalator programu Visual Studio**. W **Instalator programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB w ramach **magazynu danych i przetwarzania** obciążenia, lub jako poszczególnych składników.

2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.

       Po pewnym czasie zakończeniu zapytania i utworzeniu bazy danych Northwind.

> [!NOTE]
>  Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych w pomocy w zależności od ustawienia active lub edition, którego używasz. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Twoje wskazówki rozpocząć się przez utworzenie nowej aplikacji formularzy systemu Windows.

#### <a name="to-create-a-new-windows-forms-application-project"></a>Aby utworzyć nowy projekt aplikacji Windows Forms

1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy** > **projektu**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop**.

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.

4. Nazwij projekt **ConcurrencyWalkthrough**, a następnie wybierz pozycję **OK**.

     **ConcurrencyWalkthrough** projektu jest tworzony i dodawany do **Eksploratora rozwiązań**, i nowy formularz zostanie otwarty w projektancie.

## <a name="create-the-northwind-dataset"></a>Tworzenie zestawu danych Northwind
 W tej sekcji utworzysz zestaw danych o nazwie `NorthwindDataSet`.

#### <a name="to-create-the-northwinddataset"></a>Aby utworzyć NorthwindDataSet

1.  Na **danych** menu, wybierz **źródła Dodawanie nowych danych**.

     [Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png) otwiera.

2.  Na **wybierz typ źródła danych** ekranu wybierz **bazy danych**.

3.  Wybierz połączenie z przykładową bazą danych Northwind z listy dostępnych połączeń. Jeśli połączenie nie jest dostępny na liście połączeń, wybierz **nowe połączenie**.

    > [!NOTE]
    >  Jeśli łączysz się z plikiem bazy danych lokalnych, wybierz **nr** po otrzymaniu monitu, jeśli jak chcesz dodać plik do projektu.

4.  Na **zapisać parametry połączenia w pliku konfiguracyjnym aplikacji** ekranu wybierz **dalej**.

5.  Rozwiń węzeł **tabel** a następnie wybierz węzeł `Customers` tabeli. Domyślna nazwa dla zestawu danych powinny być `NorthwindDataSet`.

6.  Wybierz **Zakończ** do dodania do projektu zestawu danych.

## <a name="create-a-data-bound-datagridview-control"></a>Tworzenie formantu DataGridView powiązanym z danymi
 W tej sekcji utworzysz <xref:System.Windows.Forms.DataGridView> przeciągając **klientów** elementu z **źródeł danych** okna na formularzu systemu Windows.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Aby utworzyć formantu DataGridView, który jest powiązany z tabeli klientów

1.  Na **danych** menu, wybierz **Pokaż źródeł danych** otworzyć **Data Sources — okno**.

2.  W **źródeł danych** okna, rozwiń węzeł **NorthwindDataSet** węzeł, a następnie wybierz **klientów** tabeli.

3.  Wybierz strzałkę w dół w węźle tabeli, a następnie wybierz **DataGridView** na liście rozwijanej.

4.  Przeciągnij tabeli na wolne miejsce formularza.

     A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `CustomersDataGridView` i <xref:System.Windows.Forms.BindingNavigator> o nazwie `CustomersBindingNavigator` są dodawane do formularza, który jest powiązany z <xref:System.Windows.Forms.BindingSource>. To z kolei powiązany z `Customers` w tabeli `NorthwindDataSet`.

## <a name="test-the-form"></a>Przetestuj formularz
 Teraz możesz przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami do tego punktu.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

1.  Wybierz **F5** do uruchomienia aplikacji.

     Formularz pojawia się z <xref:System.Windows.Forms.DataGridView> sterowania na nim wypełnionej danych z `Customers` tabeli.

2.  Na **debugowania** menu, wybierz opcję **Zatrzymaj debugowanie**.

## <a name="handle-concurrency-errors"></a>Obsługa błędów współbieżności
 Sposób obsługi błędów zależy od firmy zasady aplikacji. W ramach tego przewodnika używamy strategia jako przykład sposobu obsługi błąd współbieżności.

 Aplikacja przedstawia trzy wersje rekordu użytkownika:

-   Bieżący rekord w bazie danych

-   Oryginalny rekord, który jest ładowany do zestawu danych

-   Proponowane zmiany w zestawie danych

Użytkownik będzie mógł zastąpienia bazy danych z wersją proponowanych, lub Anuluj aktualizację i Odśwież zestaw danych przy użyciu nowych wartości z bazy danych.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Aby włączyć obsługę błędów współbieżności

1.  Utwórz program obsługi błędów niestandardowych.

2.  Wyświetl opcje dla użytkownika.

3.  Przetwarzanie odpowiedzi użytkownika.

4.  Wyślij ponownie aktualizację, lub zresetuj danych w zestawie danych.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Dodaj kod obsługi wyjątku współbieżności
 Podczas próby przeprowadzenia aktualizacji, a zgłoszony wyjątek, zazwyczaj chcesz zrobić coś z danych, które jest dostępne zgłoszono wyjątek.

 W tej sekcji możesz dodać kod, który próbuje zaktualizować bazę danych. Można również obsługiwać żadnego <xref:System.Data.DBConcurrencyException> który może zostać wywołane, a także inne wyjątki.

> [!NOTE]
>  `CreateMessage` i `ProcessDialogResults` metody są dodawane w dalszej części tego przewodnika.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Aby dodać obsługę błędów dla błąd współbieżności

1.  Dodaj następujący kod poniżej `Form1_Load` metody:

     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2.  Zastąp `CustomersBindingNavigatorSaveItem_Click` metodę do wywołania `UpdateDatabase` metody tak wygląda podobnie do następującej:

     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Wyświetl opcje do użytkownika
 Kod, który właśnie został napisany wywołania `CreateMessage` procedury, aby wyświetlić informacje o błędzie dla użytkownika. W ramach tego przewodnika można użyć okno komunikatu do wyświetlenia różnych wersji rekordu użytkownika. Dzięki temu użytkownikowi na wybranie, czy zastąpić rekordu zmiany lub anulować edycję. Gdy użytkownik wybierze opcję (kliknie przycisk) w oknie komunikatu, odpowiedź jest przekazywana do `ProcessDialogResult` metody.

##### <a name="to-create-the-message-to-display-to-the-user"></a>Aby utworzyć komunikat do wyświetlenia dla użytkownika

-   Utwórz wiadomość, dodając następujący kod, aby **edytora kodu**. Wprowadź poniżej kod `UpdateDatabase` metody.

     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Przetwarzanie odpowiedzi użytkownika
 Należy również kod w celu przetworzenia odpowiedzi użytkownika do pola wiadomości. Aby zastąpić bieżący rekord w bazie danych proponowanej zmiany lub Porzuć lokalne zmiany i Odśwież tabelę danych z rekordu, który jest obecnie w bazie danych są następujące opcje. Jeśli użytkownik zdecyduje się **tak**, <xref:System.Data.DataTable.Merge%2A> metoda jest wywoływana z *preserveChanges* argument wartość `true`. Powoduje to, że próba aktualizacji był udany, ponieważ oryginalna wersja rekordu zgodna z rekord w bazie danych.

##### <a name="to-process-the-user-input-from-the-message-box"></a>Do przetworzenia użytkownika dane wejściowe z pola wiadomości

-   Dodaj następujący kod poniżej kod, który został dodany w poprzedniej sekcji.

     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Przetestuj formularz
 Teraz możesz przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami. Aby symulować Naruszenie współbieżności, możesz zmienić po wypełnieniu NorthwindDataSet w bazie danych.

#### <a name="to-test-the-form"></a>Aby przetestować formularz

1.  Wybierz **F5** do uruchomienia aplikacji.

2.  Gdy zostanie wyświetlony formularz, usługa będzie działać i przejdź do środowiska IDE programu Visual Studio.

3.  Na **widoku** menu, wybierz **Eksploratora serwera**.

4.  W **Eksploratora serwera**, rozwiń węzeł połączenia aplikacji przy użyciu, a następnie rozwiń **tabel** węzła.

5.  Kliknij prawym przyciskiem myszy **klientów** tabeli, a następnie wybierz **Pokaż dane tabeli**.

6.  W pierwszym rekordzie (`ALFKI`) Zmień `ContactName` do `Maria Anders2`.

    > [!NOTE]
    >  Przejdź do innego wiersza, aby zatwierdzić zmiany.

7.  Przełącz się do `ConcurrencyWalkthrough`do uruchamiania formularza.

8.  W pierwszym rekordzie na formularzu (`ALFKI`), zmienić`ContactName` do `Maria Anders1`.

9. Wybierz **zapisać** przycisku.

     Błąd współbieżności i pojawi się okno komunikatu.

10. Wybieranie **nr** anuluje aktualizacji i aktualizuje zestaw danych z wartościami, które są obecnie w bazie danych. Wybieranie **tak** zapisuje proponowanej wartości w bazie danych.

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)