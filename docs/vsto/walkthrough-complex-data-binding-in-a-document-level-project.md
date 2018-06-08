---
title: 'Wskazówki: Złożone powiązanie danych w projektach na poziomie dokumentu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b490eb1afbe8136932cfbe4caf0b1df33fbd3e4b
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845681"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Wskazówki: Złożone powiązanie danych w projektach na poziomie dokumentu
  W tym przewodniku przedstawiono podstawowe informacje o złożone powiązanie danych w projektach na poziomie dokumentu. Wiele komórek w arkuszu programu Microsoft Office Excel można powiązać pola w bazie danych Northwind programu SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie źródła danych do projektu skoroszyt.  
  
-   Dodawanie formantów powiązanych z danymi w arkuszu.  
  
-   Zapisywanie zmian danych w bazie danych.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Dostęp do serwera z przykładowej bazy danych Northwind programu SQL Server.  
  
-   Uprawnienia do odczytu i zapisu w bazie danych programu SQL Server.  
  
## <a name="create-a-new-project"></a>Tworzenie nowego projektu  
 Pierwszym krokiem jest tworzenie projektu skoroszyt programu Excel.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu skoroszyt programu Excel o nazwie **Moje złożone powiązanie danych**. W kreatorze Wybierz **Utwórz nowy dokument**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje złożone powiązanie danych** projektu do **Eksploratora rozwiązań**.  
  
## <a name="create-the-data-source"></a>Utwórz źródło danych  
 Użyj **źródeł danych** okno, aby dodać typizowanego zestaw danych do projektu.  
  
### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Jeśli **źródeł danych** okna nie jest widoczne, wyświetl ją, z menu, wybierając **widoku** > **inne okna**  >   **Źródła danych**.  
  
2.  Wybierz **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
3.  Wybierz **bazy danych** , a następnie kliknij przycisk **dalej**.  
  
4.  Wybierz połączenie danych z bazie danych programu SQL Server Northwind lub Dodaj nowe połączenie przy użyciu **nowe połączenie** przycisku.  
  
5.  Po połączenie zostało wybrane lub utworzyć, kliknij przycisk **dalej**.  
  
6.  Wyczyść opcję, aby zapisać połączenie, jeśli jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
7.  Rozwiń węzeł **tabel** w węźle **obiekty bazy danych** okna.  
  
8.  Zaznacz pole wyboru obok pozycji **pracowników** tabeli.  
  
9. Kliknij przycisk **Zakończ**.  
  
 Kreator dodaje **pracowników** do tabeli **źródeł danych** okna. Dodano również typizowanego zestaw danych do projektu, które są widoczne w **Eksploratora rozwiązań**.  
  
## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza  
 Arkusz wyświetli **pracowników** tabeli po otwarciu skoroszytu. Użytkownicy będą mogli dokonać zmian danych, a następnie zapisać te zmiany w bazie danych przez kliknięcie przycisku.  
  
 Aby powiązać automatycznie arkusz do tabeli, można dodać <xref:Microsoft.Office.Tools.Excel.ListObject> formantu do arkusza z **źródeł danych** okna. Aby dać użytkownikowi opcję, aby zapisać zmiany, należy dodać <xref:System.Windows.Forms.Button> kontrolować z **przybornika**.  
  
#### <a name="to-add-a-list-object"></a>Aby dodać obiekt listy  
  
1.  Sprawdź, czy **Moje złożonych Binding.xlsx danych** skoroszyt jest otwarty w projektancie programu Visual Studio z **Sheet1 —** wyświetlane.  
  
2.  Otwórz **źródeł danych** i zaznacz **pracowników** węzła.  
  
3.  Kliknij strzałkę listy rozwijanej, która jest wyświetlana.  
  
4.  Wybierz **ListObject** na liście rozwijanej.  
  
5.  Przeciągnij **pracowników** tabeli do komórki **A6**.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie `EmployeesListObject` jest tworzony w komórce **A6**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `EmployeesBindingSource`, karty tabeli, a <xref:System.Data.DataSet> wystąpienia są dodawane do projektu. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana <xref:System.Data.DataSet> wystąpienia.  
  
### <a name="to-add-a-button"></a>Aby dodać przycisk  
  
1.  Z **formanty standardowe** karcie **przybornika**, Dodaj <xref:System.Windows.Forms.Button> formant w komórce **A4** arkusza.  
  
 Następnym krokiem jest dodać tekst przycisku, gdy arkusz otworzy.  
  
## <a name="initialize-the-control"></a>Inicjowanie kontrolki  
 Dodawanie tekstu na przycisk w <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obsługi zdarzeń.  
  
### <a name="to-initialize-the-control"></a>Aby zainicjować kontrolki  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.vb** lub **Sheet1.cs**, a następnie kliknij przycisk **kod widoku** menu skrótów.  
  
2.  Dodaj następujący kod do `Sheet1_Startup` metodę, aby ustawić tekst b`utton`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]  
  
3.  Język C# tylko, Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Sheet1_Startup` metody.  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]  
  
 Teraz Dodaj kod obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń przycisku.  
  
## <a name="save-changes-to-the-database"></a>Zapisz zmiany w bazie danych  
 Wprowadzono zmiany danych istnieją tylko w lokalnej zestawu danych, dopóki jawnie są zapisywane w bazie danych.  
  
### <a name="to-save-changes-to-the-database"></a>Aby zapisać zmiany w bazie danych  
  
1.  Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `button`i Dodaj następujący kod, aby zatwierdzić wszystkie zmiany wprowadzone w zestawie danych w bazie danych.  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować skoroszytu, aby sprawdzić, czy dane są wyświetlane zgodnie z oczekiwaniami i że można manipulować danymi w obiekcie listy.  
  
### <a name="to-test-the-data-binding"></a>Aby przetestować tworzenie wiązania danych  
  
-   Naciśnij klawisz **F5**.  
  
     Sprawdź, czy po otwarciu skoroszytu listy obiekt jest wypełniany danych z **pracowników** tabeli.  
  
### <a name="to-modify-data"></a>Aby zmodyfikować danych  
  
1.  Kliknij komórkę **B7**, który powinien zawierać nazwę **Kowalski**.  
  
2.  Wpisz nazwę **Andersona**, a następnie naciśnij klawisz **Enter**.  
  
### <a name="to-modify-a-column-header"></a>Aby zmodyfikować nagłówek kolumny  
  
1.  Kliknij komórkę, która zawiera nagłówki kolumn **nazwisko**.  
  
2.  Typ **nazwisko**, tym odstęp między dwoma wyrazami, a następnie naciśnij klawisz **Enter**.  
  
### <a name="to-save-data"></a>W celu zapisywania danych  
  
1.  Kliknij przycisk **zapisać** w arkuszu.  
  
2.  Zakończ działanie programu Excel. Kliknij przycisk **nr** po wyświetleniu monitu, aby zapisać zmiany.  
  
3.  Naciśnij klawisz **F5** ponownie uruchomić projekt.  
  
     Obiekt listy jest wypełniany przy użyciu danych z **pracowników** tabeli.  
  
4.  Zwróć uwagę, że nazwy w komórce **B7** jest nadal **Anderson**, czyli danych zmiany wprowadzone, a następnie zapisywana w bazie danych. Nagłówek kolumny **nazwisko** został zmieniony do postaci oryginalnej bez spacji, ponieważ nagłówek kolumny nie jest powiązany z bazą danych i zmiany wprowadzone w arkuszu nie został zapisany.  
  
### <a name="to-add-new-rows"></a>Aby dodać nowe wiersze  
  
1.  Zaznacz komórkę wewnątrz obiektu listy.  
  
     Nowy wiersz, który znajduje się w dolnej części listy gwiazdką (**\***) w pierwszej komórki nowego wiersza.  
  
2.  Dodaj następujące informacje w pustym wierszu.  
  
    |Identyfikator pracownika|Nazwisko|Imię|Tytuł|  
    |----------------|--------------|---------------|-----------|  
    |10|Pawłowski|Marek|Menedżer sprzedaży|  
  
### <a name="to-delete-rows"></a>Aby usunąć wiersze  
  
-   Kliknij prawym przyciskiem myszy numer 16 (wiersz 16) po lewej stronie arkusza, a następnie kliknij przycisk **usunąć**.  
  
### <a name="to-sort-the-rows-in-the-list"></a>Sortowanie wierszy na liście  
  
1.  Zaznacz komórkę wewnątrz listy.  
  
     Wyświetlane przyciski strzałek w każdy nagłówek kolumny.  
  
2.  Kliknij przycisk strzałki w **nazwisko** nagłówka kolumny.  
  
3.  Kliknij przycisk **sortowania rosnąco**.  
  
     Wiersze są sortowane w kolejności alfabetycznej przez nazwiska.  
  
### <a name="to-filter-information"></a>Do filtrowania informacji  
  
1.  Zaznacz komórkę wewnątrz listy.  
  
2.  Kliknij przycisk strzałki w **tytuł** nagłówka kolumny.  
  
3.  Kliknij przycisk **przedstawiciel handlowy**.  
  
     Lista zawiera tylko tych wierszy, które mają **sprzedaży reprezentatywny** w **tytuł** kolumny.  
  
4.  Kliknij przycisk strzałki w **tytuł** ponownie nagłówek kolumny.  
  
5.  Kliknij przycisk **(wszystkie)**.  
  
     Filtrowanie zostaną usunięte i wszystkie wiersze są wyświetlane.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawy powiązania tabeli w bazie danych do listy obiektów. Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Pamięci podręcznej danych, dzięki czemu mogą być używane w trybie offline. Aby uzyskać więcej informacji, zobacz [porady: dane z pamięci podręcznej do użycia w trybie offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Wdrażanie rozwiązania. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
-   Tworzenie relacji wzorzec/szczegół między pola i tabeli. Aby uzyskać więcej informacji, zobacz [wskazówki: tworzenie relacji wzorzec szczegół za pomocą buforowanego zestawu danych](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)   
 [Wskazówki: Proste powiązanie danych w projektach na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  