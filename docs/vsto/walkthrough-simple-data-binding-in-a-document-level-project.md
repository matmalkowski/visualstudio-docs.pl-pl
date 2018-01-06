---
title: "Wskazówki: Proste powiązanie danych w projektach na poziomie dokumentu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
ms.assetid: 6b8fd638-af13-4ea1-b1c0-2763e2d8ae23
caps.latest.revision: "58"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 36053a8ef415e35f1244d0e379a49a46ea24f33d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Wskazówki: proste powiązanie danych w projektach na poziomie dokumentów
  W tym przewodniku przedstawiono podstawowe powiązanie danych w projektach na poziomie dokumentu. Jedno pole danych w bazie danych programu SQL Server jest powiązana z nazwanym zakresem w programie Microsoft Office Excel. Instruktaż także przedstawiono sposób dodawania kontrolek, które umożliwiają przewijać wszystkie rekordy w tabeli.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie źródła danych dla projektu programu Excel.  
  
-   Dodawanie formantów do arkusza.  
  
-   Przewijanie rekordów bazy danych.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)]lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Dostęp do serwera z przykładowej bazy danych Northwind programu SQL Server.  
  
-   Uprawnienia do odczytu i zapisu w bazie danych programu SQL Server.  
  
## <a name="creating-a-new-project"></a>Tworzenie nowego projektu  
 W tym kroku utworzysz projektu skoroszyt programu Excel.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu skoroszyt programu Excel o nazwie **Moje proste powiązanie danych**, za pomocą Visual Basic lub C#. Upewnij się, że **Utwórz nowy dokument** jest zaznaczone. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje proste powiązanie danych** projektu do **Eksploratora rozwiązań**.  
  
## <a name="creating-the-data-source"></a>Tworzenie źródła danych  
 Użyj **źródeł danych** okno, aby dodać typizowanego zestaw danych do projektu.  
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Jeśli **źródeł danych** okna nie jest widoczne, wyświetl ją, z menu, wybierając **widoku**, **inne okna**, **źródeł danych**.  
  
2.  Wybierz **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
3.  Wybierz **bazy danych** , a następnie kliknij przycisk **dalej**.  
  
4.  Wybierz połączenie danych z bazie danych programu SQL Server Northwind lub Dodaj nowe połączenie, używając **nowe połączenie** przycisku.  
  
5.  Po połączenie zostało wybrane lub utworzyć, kliknij przycisk **dalej**.  
  
6.  Wyczyść opcję, aby zapisać połączenie, jeśli jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
7.  Rozwiń węzeł **tabel** w węźle **obiekty bazy danych** okna.  
  
8.  Zaznacz pole wyboru obok pozycji **klientów** tabeli.  
  
9. Kliknij przycisk **Zakończ**.  
  
 Kreator dodaje **klientów** do tabeli **źródeł danych** okna. Dodano również typizowanego zestaw danych do projektu, które są widoczne w **Eksploratora rozwiązań**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza  
 W ramach tego przewodnika wymagane są dwa zakresy nazwane i czterech przycisków w pierwszym arkuszu. Najpierw dodaj dwa zakresy nazwane z **źródeł danych** okna tak, aby automatycznie powiązanych ze źródłem danych. Następnie dodaj przycisków z **przybornika**.  
  
#### <a name="to-add-two-named-ranges"></a>Aby dodać dwa zakresy nazwane  
  
1.  Sprawdź, czy **Moje proste Binding.xlsx danych** skoroszyt jest otwarty w projektancie programu Visual Studio z **Sheet1 —** wyświetlane.  
  
2.  Otwórz **źródeł danych** okna i rozwiń **klientów** węzła.  
  
3.  Wybierz **NazwaFirmy** kolumny, a następnie kliknij strzałkę listy rozwijanej, która jest wyświetlana.  
  
4.  Wybierz **NamedRange** w listy rozwijanej, a następnie przeciągnij **NazwaFirmy** kolumny do komórki **A1**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `companyNameNamedRange` jest tworzony w komórce **A1**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `customersBindingSource`, karty tabeli, a <xref:System.Data.DataSet> wystąpienia są dodawane do projektu. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana <xref:System.Data.DataSet> wystąpienia.  
  
5.  Wybierz **CustomerID** kolumny w **źródeł danych** okna, a następnie kliknij strzałkę listy rozwijanej, która jest wyświetlana.  
  
6.  Kliknij przycisk **NamedRange** w listy rozwijanej, a następnie przeciągnij **CustomerID** kolumny do komórki **B1**.  
  
7.  Inny <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `customerIDNamedRange` jest tworzony w komórce **B1**i powiązane z <xref:System.Windows.Forms.BindingSource>.  
  
#### <a name="to-add-four-buttons"></a>Aby dodać czterech przycisków  
  
1.  Z **formanty standardowe** karcie **przybornika**, Dodaj <xref:System.Windows.Forms.Button> formant w komórce **A3** arkusza.  
  
     Ta pozycja nosiła nazwę `Button1`.  
  
2.  Tak, że nazwy są pokazane, Dodaj trzy więcej przycisków do następujących komórek w następującej kolejności:  
  
    |Komórki|(Nazwa)|  
    |----------|--------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 Następnym krokiem jest dodanie tekstu do przycisków, a w języku C# dodać obsługę zdarzeń.  
  
## <a name="initializing-the-controls"></a>Inicjowanie kontrolki  
 Należy ustawić tekst przycisku i dodać procedury obsługi zdarzeń podczas <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> zdarzeń.  
  
#### <a name="to-initialize-the-controls"></a>Aby zainicjować kontrolki  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.vb** lub **Sheet1.cs**, a następnie kliknij przycisk **kod widoku** menu skrótów.  
  
2.  Dodaj następujący kod do `Sheet1_Startup` metodę, aby ustawić tekst dla przycisku.  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3.  Dla C# tylko dodać obsługi zdarzeń dla przycisku kliknij zdarzenia `Sheet1_Startup` metody.  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
 Teraz Dodaj kod obsługi <xref:System.Windows.Forms.Control.Click> zdarzenia przycisków, dzięki czemu użytkownik może przeglądać rekordy.  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>Dodawanie kodu, aby włączyć przewijanie rekordów  
 Dodaj kod, aby <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń w każdym przycisku, aby przechodzić.  
  
#### <a name="to-move-to-the-first-record"></a>Aby przejść do pierwszego rekordu  
  
1.  Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenie `Button1` przycisk i Dodaj następujący kod, aby przejść do pierwszego rekordu:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
#### <a name="to-move-to-the-previous-record"></a>Przejście do poprzedniego rekordu  
  
1.  Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenie `Button2` przycisk i Dodaj następujący kod, aby cofnąć pozycji o jeden:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
#### <a name="to-move-to-the-next-record"></a>Aby przejść do następnego rekordu  
  
1.  Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenie `Button3` przycisk i Dodaj następujący kod, aby przejść przez jedną pozycję:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
#### <a name="to-move-to-the-last-record"></a>Przejdź do ostatniego rekordu  
  
1.  Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenie `Button4` przycisk i Dodaj następujący kod, aby przejść do ostatniego rekordu:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować skoroszytu, aby upewnić się, można przeglądać rekordy w bazie danych.  
  
#### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
2.  Upewnij się, że pierwszy rekord jest wyświetlana w komórkach **A1** i **B1**.  
  
3.  Kliknij przycisk  **>**  (`Button3`) znajdujący się i sprawdzić, czy następnego rekordu jest wyświetlany w komórce **A1** i **B1**.  
  
4.  Klikaj inne przyciski przewijania, aby upewnić się, że rekord zmienia się zgodnie z oczekiwaniami.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawowe informacje dotyczące powiązania nazwanego zakresu pola w bazie danych. Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Pamięci podręcznej danych, dzięki czemu mogą być używane w trybie offline. Aby uzyskać więcej informacji, zobacz [porady: dane pamięci podręcznej do użycia w trybie Offline lub na serwerze](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Powiązać z komórek na wiele kolumn w tabeli, a nie jedno pole. Aby uzyskać więcej informacji, zobacz [wskazówki: złożone powiązanie danych w projektach na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Użyj <xref:System.Windows.Forms.BindingNavigator> sterowania do przewijania rekordów. Aby uzyskać więcej informacji, zobacz [porady: nawigowanie danych za pomocą BindingNavigator formularzy systemu Windows](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)   
 [Przewodnik: Złożone powiązanie danych w projektach na poziomie dokumentów](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  