---
title: 'Wskazówki: Projektowanie regionów formularzy programu Outlook | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 22d67ffe14b261911d220dfeb64a0204a6a16032
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-designing-an-outlook-form-region"></a>Wskazówki: projektowanie regionów formularzy programu Outlook
  Regiony formularzy niestandardowe rozszerzenie standardowych lub niestandardowych formularzy programu Microsoft Office Outlook. W tym przewodniku projektowania regionów formularzy niestandardowych wyświetlany jako nową stronę w oknie inspektora w elemencie kontaktu. Ten region formularza wyświetla mapy każdego adresu, który znajduje się kontaktu, wysyłając informacje o adresach do systemu Windows Live lokalnego wyszukiwania witryny internetowej. Aby uzyskać informacje na temat regionów formularzy, zobacz [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie nowego projektu dodatku VSTO dla programu Outlook.  
  
-   Dodawanie regionu formularza do projektu dodatku VSTO.  
  
-   Projektowanie układu regionu formularza.  
  
-   Dostosowywanie zachowania regionu formularza.  
  
-   Testowanie regionów formularzy programu Outlook.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] lub [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") wersję wideo tego tematu, zobacz [wideo sposobu: Projektowanie regionów formularzy programu Outlook](http://go.microsoft.com/fwlink/?LinkID=140824).  
  
## <a name="creating-a-new-outlook-vsto-add-in-project"></a>Tworzenie nowego programu Outlook VSTO dodatku projektu  
 Najpierw utworzyć podstawowego projektów dodatku VSTO.  
  
#### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO dla programu Outlook  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], tworzenie projektów dodatku VSTO dla programu Outlook o nazwie **MapItAddIn**.  
  
2.  W **nowy projekt** okno dialogowe, wybierz opcję **Utwórz katalog rozwiązania**.  
  
3.  Zapisz projekt do dowolnego katalogu.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="adding-a-form-region-to-the-outlook-vsto-add-in-project"></a>Dodawanie regionu formularza do programu Outlook VSTO dodatku projektu  
 Rozwiązanie dodatku VSTO dla programu Outlook może zawierać jeden lub więcej elementów regionu formularza programu Outlook. Dodaj element regionu formularza do projektu przy użyciu **nowych regionów formularzy programu Outlook** kreatora.  
  
#### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Aby dodać regionu formularza do projektu dodatku VSTO dla programu Outlook  
  
1.  W **Eksploratora rozwiązań**, wybierz pozycję **MapItAddIn** projektu.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **regionów formularzy programu Outlook**, nadaj nazwę plikowi **MapIt**, a następnie kliknij przycisk **Dodaj**.  
  
     **Regionu formularza NewOutlook** zostanie uruchomiony Kreator.  
  
4.  Na **wybierz jak chcesz utworzyć regionu formularza** kliknij przycisk **projektowania nowego regionu formularza**, a następnie kliknij przycisk **dalej**.  
  
5.  Na **wybierz typ regionu formularza, którego chcesz utworzyć** kliknij przycisk **oddzielnych**, a następnie kliknij przycisk **dalej**.  
  
     A *oddzielnych* regionu formularza dodaje nową stronę do formularza programu Outlook. Aby uzyskać więcej informacji na temat typów regionu formularza, zobacz [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).  
  
6.  Na **Podaj opis, a następnie wybierz preferencje wyświetlania** wpisz **mapy go** w **nazwa** pole.  
  
     Ta nazwa jest wyświetlana na Wstążce okna inspektora po otwarciu elementu kontaktu.  
  
7.  Wybierz **trybu tworzenia inspektorzy, które znajdują się w** i **inspektorzy, które znajdują się w trybie odczytu**, a następnie kliknij przycisk **dalej**.  
  
8.  Na **zidentyfikować klasy wiadomości, które spowoduje wyświetlenie tego regionu formularza** wyczyść **wiadomość E-mail**, wybierz pozycję **skontaktuj się z**, a następnie kliknij przycisk **Zakończ**.  
  
     Plik MapIt.cs lub MapIt.vb jest dodane do projektu.  
  
## <a name="designing-the-layout-of-the-form-region"></a>Projektowanie układu regionu formularza  
 Tworzenie regionów formularzy wizualnie przy użyciu *projektanta regionów formularza*. Zarządzane formanty można przeciągnąć na powierzchnię projektanta regionu formularza. Za pomocą projektanta i **właściwości** okno, aby dopasować wygląd i układ formantu.  
  
#### <a name="to-design-the-layout-of-the-form-region"></a>Projektowanie układu regionu formularza  
  
1.  W **Eksploratora rozwiązań**, rozwiń węzeł **MapItAddIn** projektu, a następnie kliknij dwukrotnie MapIt.cs lub MapIt.vb, aby otworzyć projektanta regionów formularza.  
  
2.  Kliknij prawym przyciskiem myszy projektanta, a następnie kliknij przycisk **właściwości**.  
  
3.  W **właściwości** ustaw **rozmiar** do **664, 469**.  
  
     Daje to pewność, że będzie wystarczająco duży, aby wyświetlić mapę regionu formularza.  
  
4.  Na **widoku** menu, kliknij przycisk **przybornika**.  
  
5.  Z **formanty standardowe** karcie **przybornika**, Dodaj **WebBrowser** do regionu formularza.  
  
     **WebBrowser** wyświetli mapy dla każdego adresu, który znajduje się kontaktu.  
  
## <a name="customizing-the-behavior-of-the-form-region"></a>Dostosowywanie zachowania regionu formularza  
 Dodaj kod obsługi zdarzeń regionu formularza, aby dostosować sposób regionu formularza zachowuje się w czasie wykonywania. Dla tego regionu formularza kod sprawdza właściwości elementu programu Outlook i określa, czy mają być wyświetlane regionu formularza mapy go. Jeśli pokazuje regionu formularza Kod przechodzi do lokalnego wyszukiwania usługi Windows Live i ładuje mapę każdego adresu, na liście elementu kontaktów programu Outlook.  
  
#### <a name="to-customize-the-behavior-of-the-form-region"></a>Aby dostosować zachowanie regionu formularza  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy MapIt.cs lub MapIt.vb, a następnie kliknij przycisk **kod widoku**.  
  
     MapIt.cs lub MapIt.vb zostanie otwarty w edytorze kodu.  
  
2.  Rozwiń węzeł **fabryki regionu formularza** kodu regionu.  
  
     Klasa fabryki regionu formularza o nazwie `MapItFactory` jest widoczna.  
  
3.  Dodaj następujący kod do `MapItFactory_FormRegionInitializing` obsługi zdarzeń. Ten program obsługi zdarzeń jest wywoływane, gdy użytkownik otwiera elemencie kontaktu. Poniższy kod określa, czy element kontaktu zawiera adres. Jeśli kontakt nie zawiera adresu, ten kod ustawia <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> klasy do **true** regionu formularza nie jest wyświetlany. W przeciwnym razie dodatku VSTO zgłasza <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> zdarzeń i wyświetla regionu formularza.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
4.  Dodaj następujący kod do <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> obsługi zdarzeń. Kod będzie wykonywał następujące zadania:  
  
    -   Argument każdy adres w elemencie kontaktów i tworzy ciągu adresu URL.  
  
    -   Wywołania <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody <xref:System.Windows.Forms.WebBrowser> obiektu i przekazuje jako parametr ciągu adresu URL.  
  
     Witryna lokalnego wyszukiwania pojawi się w regionie formularz mapy go i przedstawia każdy adres w konsoli podstaw.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]  
  
## <a name="testing-the-outlook-form-region"></a>Testowanie regionów formularzy programu Outlook  
 Po uruchomieniu projektu Visual Studio otworzy program Outlook. Otwórz element kontaktu do wyświetlania regionu formularza mapy go. Region formularza mapy go pojawia się jako strony w postaci dowolnego elementu kontaktu, który zawiera adres.  
  
#### <a name="to-test-the-map-it-form-region"></a>Aby przetestować regionu formularza mapy go  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
     Zostanie otwarty program Outlook.  
  
2.  W programie Outlook na **Home** , kliknij pozycję **nowych elementów**, a następnie kliknij przycisk **skontaktuj się z**.  
  
3.  W formularzu kontaktu wpisz **Beebe pods** jako kontakt nazwy, a następnie określ następujące trzy adresy.  
  
    |Typ adresu|Adres|  
    |------------------|-------------|  
    |**Biznesowa**|**Saint Main 4567 pole, NY**|  
    |**Strona główna**|**Saint Północna 1234 pole, NY**|  
    |**Inne**|**Saint Main 3456 Seattle, WA**|  
  
4.  Zapisz i Zamknij kontakt.  
  
5.  Otwórz ponownie **Beebe pods** kontakt.  
  
6.  W **Pokaż** grupy elementów wstążki, kliknij przycisk **mapy go** do regionu formularza mapy go otworzyć.  
  
     Region formularza mapy go pojawia się i wyświetla witryny lokalnego wyszukiwania. **Firm**, **Home**, i **innych** adresy są wyświetlane w konsoli podstaw. W konsoli podstaw zaznacz adres, który ma być mapowany.  
  
## <a name="next-steps"></a>Następne kroki  
 Można poznać więcej informacji na temat sposobu dostosowywania interfejsu użytkownika aplikacji Outlook w tych tematach:  
  
-   Aby dowiedzieć się więcej o dostosowywaniu wstążki elementu programu Outlook, zobacz [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Wskazówki: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Porady: dodawanie regionu formularza na projekt dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Instrukcje: Ochrona programu Outlook przed wyświetlaniem regionów formularzy](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  