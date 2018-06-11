---
title: 'Wskazówki: Aktualizowanie formantów na Wstążce w czasie wykonywania'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b2d9f8a585b6a9353c9e64cf03b0876e5324a539
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258804"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-runtime"></a>Wskazówki: Aktualizowanie formantów na Wstążce w czasie wykonywania
  W tym przewodniku przedstawiono sposób użycia model obiektu Wstążka zaktualizować formantów na Wstążce po załadowaniu wstążki do aplikacji pakietu Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Przykład pobiera dane z przykładowej bazy danych Northwind aby wypełnić pole kombi i menu programu Microsoft Office Outlook. Elementy, które należy wybrać w tych kontrolek automatycznie wypełnić pola, takie jak **do** i **podmiotu** w wiadomości e-mail.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Utwórz nowy projekt dodatku VSTO dla programu Outlook.  
  
-   Projektowanie niestandardową grupę wstążki.  
  
-   Dodaj niestandardową grupę do wbudowanej karty.  
  
-   Aktualizowanie formantów na Wstążce w czasie wykonywania.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Outlook  
  
## <a name="create-a-new-outlook-vsto-add-in-project"></a>Utwórz nowy projekt dodatku VSTO dla programu Outlook  
 Najpierw utwórz projektów dodatku VSTO dla programu Outlook.  
  
### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO dla programu Outlook  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], tworzenie projektów dodatku VSTO dla programu Outlook o nazwie **Ribbon_Update_At_Runtime**.  
  
2.  W **nowy projekt** okno dialogowe, wybierz opcję **Utwórz katalog rozwiązania**.  
  
3.  Zapisz projekt w katalogu projektu.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="design-a-custom-ribbon-group"></a>Projektowanie niestandardową grupę wstążki  
 Wstążki w tym przykładzie będą wyświetlane, gdy użytkownik Redaguj nową wiadomość e-mail. Aby utworzyć niestandardową grupę na Wstążce, najpierw Dodaj element wstążki do projektu, a następnie projektowania grupy w Projektancie wstążki. Ta grupa niestandardowych pomoże generują komunikaty kolejną wiadomość e-mail do klientów przez ściąganie nazwy i kolejność historii z bazy danych.  
  
### <a name="to-design-a-custom-group"></a>Projekt grupy niestandardowej  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **wstążki (projektanta wizualnego)**.  
  
3.  Zmień nazwę nowego wstążki do **CustomerRibbon**, a następnie kliknij przycisk **Dodaj**.  
  
     *CustomerRibbon.cs* lub *CustomerRibbon.vb* plik zostanie otwarty w Projektancie Wstążki i wyświetla kartę domyślne i grupy.  
  
4.  Kliknij przycisk projektanta wstążki, aby go wybrać.  
  
5.  W **właściwości** okna, kliknij strzałkę listy rozwijanej obok pola **RibbonType** właściwości, a następnie kliknij przycisk **Microsoft.Outlook.Mail.Compose**.  
  
     Dzięki temu na Wstążce, aby są wyświetlane, gdy użytkownik Redaguj nową wiadomość e-mail w programie Outlook.  
  
6.  W Projektancie Wstążki kliknij **grupa1** aby go wybrać.  
  
7.  W **właściwości** ustaw **etykiety** do **zakupy klienta**.  
  
8.  Z **formantów wstążki pakietu Office** karcie **przybornika**, przeciągnij **ComboBox** na **zakupy klienta** grupy.  
  
9. Kliknij przycisk **ComboBox1** aby go wybrać.  
  
10. W **właściwości** ustaw **etykiety** do **klientów**.  
  
11. Z **formantów wstążki pakietu Office** karcie **przybornika**, przeciągnij **Menu** na **zakupy klienta** grupy.  
  
12. W **właściwości** ustaw **etykiety** do **produktu zakupionych**.  
  
13. Ustaw **dynamiczne** do **true**.  
  
     Dzięki temu można dodawać i usuwać formanty menu w czasie wykonywania, po załadowaniu wstążki do aplikacji pakietu Office.  
  
## <a name="add-the-custom-group-to-a-built-in-tab"></a>Dodaj niestandardową grupę do wbudowanej karty  
 Tabulator wbudowana jest kartę, która jest już na wstążce programu Outlook Eksploratora lub Inspektora. W tej procedurze zostanie dodaj niestandardową grupę do wbudowanej karty, a następnie określić położenie niestandardowe grupy na karcie.  
  
### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Aby dodać niestandardową grupę do wbudowanej karty  
  
1.  Kliknij przycisk **TabAddins (wbudowane)** kartę, aby go wybrać.  
  
2.  W **właściwości** okna, rozwiń węzeł **ControlId** właściwości, a następnie ustawić **OfficeId** do **TabNewMailMessage**.  
  
     Spowoduje to dodanie **zakupy klienta** grupy **wiadomości** karty wstążki, która jest wyświetlana w nową wiadomość e-mail.  
  
3.  Kliknij przycisk **zakupy klienta** grupy, aby go wybrać.  
  
4.  W **właściwości** okna, rozwiń węzeł **pozycji** właściwości, kliknij strzałkę listy rozwijanej obok pola **PositionType** właściwości, a następnie kliknij przycisk  **BeforeOfficeId**.  
  
5.  Ustaw **OfficeId** właściwości **GroupClipboard**.  
  
     To umieszcza **zakupy klienta** grupy przed **Schowka** grupy **wiadomości** kartę.  
  
## <a name="create-the-data-source"></a>Utwórz źródło danych  
 Użyj **źródeł danych** okno, aby dodać typizowanego zestaw danych do projektu.  
  
### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.  
  
     Spowoduje to uruchomienie **Kreator konfiguracji źródła danych**.  
  
2.  Wybierz **bazy danych**, a następnie kliknij przycisk **dalej**.  
  
3.  Wybierz **Dataset**, a następnie kliknij przycisk **dalej**.  
  
4.  Wybierz połączenie danych z bazie danych programu Microsoft SQL Server Compact 4.0 Northwind lub Dodaj nowe połączenie za pomocą **nowe połączenie** przycisku.  
  
5.  Po połączenie zostało wybrane lub utworzyć, kliknij przycisk **dalej**.  
  
6.  Kliknij przycisk **dalej** Aby zapisać parametry połączenia.  
  
7.  Na **wybierz obiekty bazy danych użytkownika** rozwiń pozycję **tabel**.  
  
8.  Zaznacz pole wyboru obok każdego z następujących tabel:  
  
    1.  **Klienci**  
  
    2.  **Szczegóły zlecenia**  
  
    3.  **Zlecenia**  
  
    4.  **Produkty**  
  
9. Kliknij przycisk **Zakończ**.  
  
## <a name="update-controls-in-the-custom-group-at-runtime"></a>Zaktualizuj Kontrolki niestandardowe grupy w czasie wykonywania  
 Model obiektu Wstążka umożliwia wykonywanie następujących zadań:  
  
-   Dodaj nazwy klienta do **klientów** pola kombi.  
  
-   Dodaj formanty menu i przycisku do **zakupionych produktów** sprzedanych menu, które reprezentują zamówienia i produkty.  
  
-   Wypełnij do, tematu i treści pól nowe wiadomości e-mail przy użyciu danych z **klientów** pole kombi i **zakupionych produktów** menu.  
  
### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Aby zaktualizować formantów w niestandardowej grupie za pomocą modelu obiektów wstążki  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** wybierz opcję **System.Data.Linq** zestawu, a następnie kliknij przycisk **OK**.  
  
     Ten zestaw zawiera klasy dla przy użyciu język Language-Integrated zapytania (LINQ). LINQ użyje do wypełnienia Kontrolki niestandardowe grupy z danymi z bazy danych Northwind.  
  
3.  W **Eksploratora rozwiązań**, kliknij przycisk **CustomerRibbon.cs** lub **CustomerRibbon.vb** aby go wybrać.  
  
4.  Na **widoku** menu, kliknij przycisk **kod**.  
  
     Plik wstążki kodu zostanie otwarty w edytorze kodu.  
  
5.  Dodaj następujące instrukcje na początku pliku kodu wstążki. Instrukcje te zapewniają łatwy dostęp do programu LINQ w przestrzeni nazw i z przestrzenią nazw podstawowy zestaw międzyoperacyjny programu Outlook (PIA).  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]  
  
6.  Dodaj następujący kod wewnątrz `CustomerRibbon` klasy. Ten kod deklaruje tabeli danych i adaptery tabel, które będą używane do przechowywania informacji z klienta, zamówienia, szczegółów zamówienia i produktu tabele bazy danych Northwind.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]  
  
7.  Dodaj następujący blok kodu do `CustomerRibbon` klasy. Ten kod dodaje trzy metody pomocnicze, które Tworzenie formantów na Wstążce w czasie wykonywania.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]  
  
8.  Zastąp `CustomerRibbon_Load` metoda obsługi zdarzeń z następującym kodem. Ten kod używa zapytania LINQ do wykonywania następujących zadań:  
  
    -   Wypełnij **klientów** pole kombi za pomocą identyfikator i nazwa 20 klientów w bazie danych Northwind.  
  
    -   Wywołania `PopulateSalesOrderInfo` metody pomocnika. Ta metoda aktualizacji **ProductsPurchased** menu o numerach porządkowych sprzedaży, które odnoszą się do aktualnie zaznaczonego klienta.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]  
  
9. Dodaj następujący kod do `CustomerRibbon` klasy. Ten kod używa zapytań LINQ do wykonywania następujących zadań:  
  
    -   Dodaje do podmenu **ProductsPurchased** menu dla każdego zamówienia sprzedaży dotyczące wybranego klienta.  
  
    -   Dodaje przyciski do każdego podmenu produktów związanych z zamówienia sprzedaży.  
  
    -   Dodaje obsługę zdarzeń do każdego przycisku.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]  
  
10. W **Eksploratora rozwiązań**, kliknij dwukrotnie plik kodu wstążki.  
  
     Otwiera projektanta wstążki.  
  
11. Projektant wstążki, kliknij dwukrotnie **klientów** pola kombi.  
  
     Plik kodu wstążki zostanie otwarty w edytorze kodu i `ComboBox1_TextChanged` pojawi się program obsługi zdarzeń.  
  
12. Zastąp `ComboBox1_TextChanged` obsługi zdarzeń z następującym kodem. Kod będzie wykonywał następujące zadania:  
  
    -   Wywołania `PopulateSalesOrderInfo` metody pomocnika. Ta metoda aktualizacji **zakupionych produktów** menu z zamówień sprzedaży, które dotyczą wybranego odbiorcy.  
  
    -   Wywołania `PopulateMailItem` metody pomocniczej i przebiegów w bieżącym tekst, który jest nazwa wybranego klienta. Ta metoda powoduje wypełnienie do, tematu i treści pól nowe wiadomości e-mail.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]  
  
13. Dodaj następujące `Click` program obsługi zdarzeń do `CustomerRibbon` klasy. Ten kod dodaje nazwę zaznaczonych produktów do pola treści nowe wiadomości e-mail.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]  
  
14. Dodaj następujący kod do `CustomerRibbon` klasy. Kod będzie wykonywał następujące zadania:  
  
    -   Wypełnia wiersz na nowe wiadomości e-mail przy użyciu adresu e-mail aktualnie zaznaczonego klienta.  
  
    -   Dodaje tekst do pól temat i treść nowe wiadomości e-mail.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]  
  
## <a name="test-the-controls-in-the-custom-group"></a>Testowanie Kontrolki niestandardowe grupy  
 Po otwarciu nowego formularza poczty programu Outlook niestandardową grupę o nazwie **zakupy klienta** pojawia się na **wiadomości** karty wstążki.  
  
 Aby utworzyć komunikat kolejną wiadomość e-mail klienta, wybierz klienta, a następnie wybierz produktów zakupionych przez klienta. Formanty w **zakupy klienta** grupy są aktualizowane podczas pracy z danymi z bazy danych Northwind.  
  
### <a name="to-test-the-controls-in-the-custom-group"></a>Aby przetestować Kontrolki niestandardowe grupy  
  
1.  Naciśnij klawisz **F5** do uruchomienia projektu.  
  
     Uruchamia program Outlook.  
  
2.  W programie Outlook na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **wiadomość E-mail**.  
  
     Są wykonywane następujące akcje:  
  
    -   Zostanie wyświetlone nowe okno Inspektora wiadomości poczty.  
  
    -   Na **komunikat** karty wstążki, **zakupy klienta** grupy jest umieszczany przed **Schowka** grupy.  
  
    -   **Klientów** pole kombi grupy został zaktualizowany o nazw klientów w bazie danych Northwind.  
  
3.  Na **komunikat** karty wstążki w **zakupy klienta** grupy, wybierz klienta z **klientów** pola kombi.  
  
     Są wykonywane następujące akcje:  
  
    -   **Zakupionych produktów** menu jest aktualizowana w celu wyświetlenia każdego zamówienia sprzedaży dla wybranego odbiorcy.  
  
    -   Każdy podmenu zamówienie jest aktualizowana w celu wyświetlenia produktów zakupionych w podanej kolejności.  
  
    -   Adres e-mail wybranego klienta zostanie dodany do **do** wiersza wiadomości e-mail, tematu i treści wiadomości e-mail są wypełniane przy użyciu tekstu.  
  
4.  Kliknij przycisk **zakupy produktów** menu wskaż w dowolnej kolejności sprzedaży, a następnie kliknij produktu z zamówienia sprzedaży.  
  
     Nazwa produktu jest dodawana do treści wiadomości e-mail.  
  
## <a name="next-steps"></a>Następne kroki  
 Można poznać więcej informacji na temat sposobu dostosowywania interfejsu użytkownika pakietu Office z tych tematów:  
  
-   Dodaj kontekstowa interfejsu użytkownika do dostosowania dowolnym poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).  
  
-   Rozszerzenie standardowych lub niestandardowych formularzy programu Microsoft Office Outlook. Aby uzyskać więcej informacji, zobacz [wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
-   Dodawanie niestandardowego okienka zadań do programu Outlook. Aby uzyskać więcej informacji, zobacz [niestandardowego okienka zadań](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Zapytanie o języku zintegrowanym (LINQ)](/dotnet/csharp/linq/index)   
 [Porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md)   
 [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Porady: zmiana położenia zakładki na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Porady: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)   
 [Porady: dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Porady: eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Porady: dodatek Pokaż błędy interfejsu użytkownika](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  