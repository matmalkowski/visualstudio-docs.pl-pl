---
title: 'Wskazówki: Tworzenie relacji wzorzec szczegółów przy użyciu pamięci podręcznej zestawu danych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: abe0b766214c1906afcf443c23948c492a6bde90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-master-detail-relation-using-a-cached-dataset"></a>Wskazówki: Tworzenie relacji wzorzec szczegółów przy użyciu pamięci podręcznej zestawu danych
  W tym przewodniku pokazano tworzenie relacji wzorzec/szczegół w arkuszu i buforowanie danych, aby rozwiązania mogą być używane w trybie offline.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W tym przewodniku przedstawiono sposób:  
  
-   Dodawanie formantów do arkusza.  
  
-   Skonfigurowanie zestawu danych, które można buforować w arkuszu.  
  
-   Dodaj kod, aby włączyć przewijanie rekordów.  
  
-   Testowanie projektu.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Dostęp do przykładowej bazy danych Northwind programu SQL Server. Baza danych może być na komputerze dewelopera lub na serwerze.  
  
-   Uprawnienia do odczytu i zapisu w bazie danych programu SQL Server.  
  
## <a name="creating-a-new-project"></a>Tworzenie nowego projektu  
 W tym kroku utworzysz projektu skoroszyt programu Excel.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu skoroszyt programu Excel o nazwie **Moje główny-szczegółowy**, za pomocą Visual Basic lub C#. Upewnij się, że **Utwórz nowy dokument** jest zaznaczone. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio zostanie otwarty nowy skoroszyt programu Excel w Projektancie i dodaje **Moje główny-szczegółowy** projektu do **Eksploratora rozwiązań**.  
  
## <a name="creating-the-data-source"></a>Tworzenie źródła danych  
 Użyj **źródeł danych** okno, aby dodać typizowanego zestaw danych do projektu.  
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Jeśli **źródeł danych** okna nie jest widoczne, wyświetl ją, z menu, wybierając **widoku**, **inne okna**, **źródeł danych**.  
  
2.  Wybierz **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
3.  Wybierz **bazy danych** , a następnie kliknij przycisk **dalej**.  
  
4.  Wybierz połączenie danych z bazie danych programu SQL Server Northwind lub Dodaj nowe połączenie przy użyciu **nowe połączenie** przycisku.  
  
5.  Po wybraniu lub utworzenie połączenia, kliknij przycisk **dalej**.  
  
6.  Wyczyść opcję, aby zapisać połączenie, jeśli jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
7.  Rozwiń węzeł **tabel** w węźle **obiekty bazy danych** okna.  
  
8.  Wybierz **zamówień** tabeli i **szczegółów zamówienia** tabeli.  
  
9. Kliknij przycisk **Zakończ**.  
  
 Kreator dodaje dwie tabele, aby **źródeł danych** okna. Dodano również typizowanego zestaw danych do projektu, które są widoczne w **Eksploratora rozwiązań**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza  
 W tym kroku zostaną dodane do pierwszego arkusza nazwanego zakresu, obiekt listy i przyciskami. Najpierw dodaj nazwanego zakresu i obiekt listy z **źródeł danych** okna tak, aby automatycznie powiązanych ze źródłem danych. Następnie dodaj przycisków z **przybornika**.  
  
#### <a name="to-add-a-named-range-and-a-list-object"></a>Aby dodać nazwanego zakresu, a obiekt listy  
  
1.  Sprawdź, czy **Moje Detail.xlsx wzorca** skoroszyt jest otwarty w projektancie programu Visual Studio z **Sheet1 —** wyświetlane.  
  
2.  Otwórz **źródeł danych** okna i rozwiń **zamówień** węzła.  
  
3.  Wybierz **OrderID** kolumny, a następnie kliknij strzałkę listy rozwijanej, która jest wyświetlana.  
  
4.  Kliknij przycisk **NamedRange** w listy rozwijanej, a następnie przeciągnij **OrderID** kolumny do komórki **A2**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `OrderIDNamedRange` jest tworzony w komórce **A2**. W tym samym czasie <xref:System.Windows.Forms.BindingSource> o nazwie `OrdersBindingSource`, karty tabeli, a <xref:System.Data.DataSet> wystąpienia są dodawane do projektu. Kontrolka jest powiązana z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana <xref:System.Data.DataSet> wystąpienia.  
  
5.  Przewiń w dół poza kolumn, które są objęte **zamówień** tabeli. W dolnej części listy jest **szczegółów zamówienia** tabeli; tutaj jest ponieważ jest elementem podrzędnym **zamówień** tabeli. Wybierz tę opcję, **szczegółów zamówienia** tabeli nie jedną, która jest na tym samym poziomie jako **zamówień** tabeli, a następnie kliknij strzałkę listy rozwijanej, która jest wyświetlana.  
  
6.  Kliknij przycisk **ListObject** w listy rozwijanej, a następnie przeciągnij **SzczegółyZamówienia** tabeli do komórki **A6**.  
  
7.  A <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie **Order_DetailsListObject** jest tworzony w komórce **A6**i powiązane z <xref:System.Windows.Forms.BindingSource>.  
  
#### <a name="to-add-two-buttons"></a>Aby dodać dwóch przycisków  
  
1.  Z **formanty standardowe** karcie **przybornika**, Dodaj <xref:System.Windows.Forms.Button> formant w komórce **A3** arkusza.  
  
     Ta pozycja nosiła nazwę `Button1`.  
  
2.  Dodaj inny <xref:System.Windows.Forms.Button> formant w komórce **B3** arkusza.  
  
     Ta pozycja nosiła nazwę `Button2`.  
  
 Następnie oznacz zestaw danych w pamięci podręcznej w dokumencie.  
  
## <a name="caching-the-dataset"></a>Buforowanie zestawu danych  
 Oznacz zestaw danych można buforować w dokumencie dokonując zestawu danych publicznych i ustawienie **CacheInDocument** właściwości.  
  
#### <a name="to-cache-the-dataset"></a>Do pamięci podręcznej zestawu danych  
  
1.  Wybierz **NorthwindDataSet** na pasku składnika.  
  
2.  W **właściwości** Zmień **Modyfikatory** właściwości **publicznego**.  
  
     Zestawy danych muszą być publiczne, zanim buforowanie jest włączone.  
  
3.  Zmień **CacheInDocument** właściwości **True**.  
  
 Następnym krokiem jest dodanie tekstu do przycisków, a w języku C# Dodaj kod, aby Podłączanie obsługi zdarzeń.  
  
## <a name="initializing-the-controls"></a>Inicjowanie kontrolki  
 Należy ustawić tekst przycisku i dodać procedury obsługi zdarzeń podczas <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> zdarzeń.  
  
#### <a name="to-initialize-the-data-and-the-controls"></a>Aby zainicjować danych i formantów  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1.vb** lub **Sheet1.cs**, a następnie kliknij przycisk **kod widoku** menu skrótów.  
  
2.  Dodaj następujący kod do `Sheet1_Startup` metodę, aby ustawić tekst przycisków.  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  Dla C# tylko dodać obsługi zdarzeń dla przycisku kliknij zdarzenia `Sheet1_Startup` metody.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>Dodawanie kodu, aby włączyć przewijanie rekordów  
 Dodaj kod, aby <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń w każdym przycisku, aby przechodzić.  
  
#### <a name="to-scroll-through-the-records"></a>Do przewijania rekordów  
  
1.  Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button1`i Dodaj następujący kod, aby przechodzić wstecz:  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.Control.Click> zdarzenia `Button2`i Dodaj następujący kod, aby poprawić rekordy:  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować skoroszytu do upewnij się, że dane są wyświetlane zgodnie z oczekiwaniami oraz że rozwiązanie można użyć w trybie offline.  
  
#### <a name="to-test-the-data-caching"></a>Aby przetestować buforowanie danych  
  
1.  Naciśnij klawisz **F5**.  
  
2.  Sprawdź, czy nazwany zakres i obiekt listy są wypełnione danych ze źródła danych.  
  
3.  Przewiń niektóre rekordy za pomocą przycisków.  
  
4.  Zapisz skoroszyt, a następnie zamknij skoroszyt i Visual Studio.  
  
5.  Wyłączanie połączenia z bazą danych. Odłącz kabel sieciowy z komputera, jeśli baza danych znajduje się na serwerze lub zatrzymania usługi programu SQL Server, jeśli baza danych znajduje się na komputerze deweloperskim.  
  
6.  Otwórz program Excel, a następnie otwórz **Moje Detail.xlsx wzorca** z katalogu \bin (\My Master-Detail\bin w języku Visual Basic lub \My Master-Detail\bin\debug w języku C#).  
  
7.  Przewijanie rekordów, aby zobaczyć, czy arkusz działa normalnie, po rozłączeniu.  
  
8.  Połącz się ponownie z bazą danych. Ponownie podłączyć komputer sieci, jeśli baza danych znajduje się na serwerze lub uruchomić usługę serwera SQL, jeśli baza danych znajduje się na komputerze deweloperskim.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono podstawy tworzenie relacji wzorzec/szczegół danych w arkuszu i buforowania zestawu danych. Poniżej przedstawiono niektóre zadania, które mogą występować:  
  
-   Wdrażanie rozwiązania. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)   
 [Buforowanie danych](../vsto/caching-data.md)   
 [Przegląd obiektów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)  
  
  