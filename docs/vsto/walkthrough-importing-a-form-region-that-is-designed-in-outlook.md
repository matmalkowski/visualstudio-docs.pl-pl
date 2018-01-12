---
title: "Wskazówki: Importowanie regionów formularzy zaprojektowanych w programie Outlook | Dokumentacja firmy Microsoft"
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
- importing form regions
- form regions [Office development in Visual Studio], importing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e8a6abfd5c09194fe9fb37f05a50d874c0239cde
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-importing-a-form-region-that-is-designed-in-outlook"></a>Wskazówki: importowanie regionów formularzy zaprojektowanych w programie Outlook
  W tym przewodniku pokazano, jak projektowanie regionów formularzy w programie Microsoft Office Outlook, a następnie zaimportuj regionów formularzy w projekcie dodatku narzędzi VSTO programu Outlook przy użyciu **nowego regionu formularza** kreatora. Projektowanie regionów formularzy programu Outlook umożliwia dodanie kontrolki natywne Outlook do regionu formularza, który powiązanie z danymi programu Outlook. Po zaimportowaniu regionu formularza można obsługiwać zdarzenia każdej kontrolki.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Projektowanie regionów formularzy przy użyciu projektanta regionów formularzy w programie Outlook.  
  
-   Importowanie regionów formularzy w projekcie dodatku narzędzi VSTO programu Outlook.  
  
-   Obsługa zdarzeń kontroli regionu formularza.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)]lub [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy i. Tworzenie programu Outlook formularza regionów przy użyciu programu Visual Studio 2008?](http://go.microsoft.com/fwlink/?LinkID=130305).  
  
## <a name="designing-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Projektowanie regionów formularzy przy użyciu projektanta regionów formularzy w programie Outlook  
 W tym kroku zostanie projektowanie regionów formularzy w programie Outlook. Możesz następnie zostanie zapisany regionu formularza do lokalizacji łatwy do znalezienia tak, aby zaimportować je do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Ten przykład regionu formularza całkowicie zastępuje zwykle formularz zadania. Zapewnia sposób, aby śledzić postęp wszystkich zadań, które należy wykonać, aby można było głównym zadaniem wykonać (zadania wstępne). Region formularza zostanie wyświetlona lista zadań wstępnych i pokazuje stan ukończenia dla każdego zadania na liście. Użytkownicy mogą dodać zadania do listy i usuń je. Można również odświeżyć stan ukończenia każdego zadania.  
  
#### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Projektowanie regionów formularzy przy użyciu projektanta regionów formularzy w programie Outlook  
  
1.  Uruchom program Microsoft Office Outlook.  
  
2.  W programie Outlook na **Developer** , kliknij pozycję **projektowania formularza**. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  W **projektowania formularza** kliknij **zadań**, a następnie kliknij przycisk **Otwórz**.  
  
4.  W programie Outlook na **Developer** karcie **projekt** kliknij przycisk **nowego regionu formularza**.  
  
     Zostanie otwarty nowy regionu formularza. Jeśli **wybór pola** nie jest wyświetlana, kliknij przycisk **wybór pola** w **narzędzia** grupy.  
  
5.  Przeciągnij **podmiotu** pola i **Ukończono** pola **wybór pola** do regionu formularza.  
  
6.  W **narzędzia** kliknij przycisk **przybornik** otworzyć **przybornika**.  
  
7.  Przeciągnij etykietę z **przybornika** do regionu formularza. Umieść etykiety pod **podmiotu** i **Ukończono** pola.  
  
8.  Kliknij etykietę prawym przyciskiem myszy, a następnie kliknij przycisk **właściwości zaawansowane**.  
  
9. W **właściwości** ustaw **podpis** właściwości **tego zadania zależy od następujących zadań**ustaw **szerokość** właściwości **200**, a następnie kliknij przycisk **Zastosuj**.  
  
10. Przeciągnij kontrolki ListBox z **przybornika** do regionu formularza. Ustaw pole listy poniżej **tego zadania zależy od następujących zadań** etykiety.  
  
11. Zaznacz pole listy, który właśnie został dodany.  
  
12. W **właściwości** ustaw **szerokość** do **300**, a następnie kliknij przycisk **Zastosuj**.  
  
13. Przeciągnij etykietę z **przybornika** do regionu formularza. Pozycja etykiety poniżej pola listy.  
  
14. Wybierz etykietę, którą właśnie został dodany.  
  
15. W **właściwości** ustaw **podpis** właściwości **wybierz zadanie, aby dodać do listy zadań zależnych**ustaw **szerokość** dla właściwości **200**, a następnie kliknij przycisk **Zastosuj**.  
  
16. Przeciągnij kontrolki ComboBox z **przybornika** do regionu formularza. Położenie pola kombi poniżej **wybierz zadanie, aby dodać do listy zadań zależnych** etykiety.  
  
17. Wybierz pola kombi, który właśnie został dodany.  
  
18. W **właściwości** ustaw **szerokość** właściwości **300**, a następnie kliknij przycisk **Zastosuj**.  
  
19. Przeciągnij formantu CommandButton **przybornika** do regionu formularza. Położenie przycisku polecenia, obok pola kombi.  
  
20. Wybierz przycisk polecenia, który właśnie został dodany.  
  
21. W **właściwości** ustaw **nazwa** do **AddDependentTask**ustaw **podpis** do **Dodaj zadanie zależne**ustaw **szerokość** do **100**, a następnie kliknij przycisk **Zastosuj**.  
  
22. W **wybór pola**, kliknij przycisk **nowy**.  
  
23. W **nowe pole** okno dialogowe, typ **pole ukryte** w **nazwa** pola, a następnie kliknij przycisk **OK**.  
  
24. Przeciągnij **pole ukryte** pola **wybór pola** do regionu formularza.  
  
25. W **właściwości** ustaw **Visible** do **0 - False**, a następnie kliknij przycisk **Zastosuj**.  
  
26. W programie Outlook na **Developer** karcie **projekt** kliknij przycisk **zapisać** przycisk, a następnie kliknij przycisk **Zapisz regionu formularza jako**.  
  
     Nazwa regionu formularza **TaskFormRegion** i zapisać go do katalogu lokalnego na komputerze.  
  
     Outlook zapisuje regionu formularza jako plik magazynu formularzy programu Outlook (.ofs). Region formularza jest zapisywany o nazwie TaskFormRegion.ofs.  
  
27. Zamknij program Outlook.  
  
## <a name="creating-a-new-outlook-add-in-project"></a>Tworzenie nowego programu Outlook dodatku projektu  
 W tym kroku utworzysz projektów dodatku VSTO dla programu Outlook. W dalszej części tego przewodnika zostaną zaimportowane do regionu formularza do projektu.  
  
#### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO dla programu Outlook  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], tworzenie projektów dodatku VSTO dla programu Outlook o nazwie **TaskAddIn**.  
  
2.  W **nowy projekt** okno dialogowe, wybierz opcję **Utwórz katalog rozwiązania**.  
  
3.  Zapisz projekt w katalogu projektu.  
  
     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="importing-the-form-region"></a>Importowanie regionów formularzy  
 Możesz zaimportować regionu formularza, która została zaprojektowana w programie Outlook w projekcie dodatku narzędzi VSTO programu Outlook przy użyciu **nowych regionów formularzy programu Outlook** kreatora.  
  
#### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>Aby zaimportować regionu formularza do projektu dodatku VSTO dla programu Outlook  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **TaskAddIn** projektu, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **nowy element**.  
  
2.  W **szablony** okienku wybierz **regionów formularzy programu Outlook**, nadaj nazwę plikowi **TaskFormRegion**, a następnie kliknij przycisk **Dodaj**.  
  
     **Regionu formularza NewOutlook** zostanie uruchomiony Kreator.  
  
3.  Na **wybierz jak chcesz utworzyć regionu formularza** kliknij przycisk **zaimportować magazynu formularzy programu Outlook (.ofs) pliku**, a następnie kliknij przycisk **Przeglądaj**.  
  
4.  W **istniejącej lokalizacji pliku regionu formularza Outlook** okno dialogowe, przejdź do lokalizacji **TaskFormRegion.ofs**, wybierz pozycję **TaskFormRegion.ofs**, kliknij przycisk **Otwórz**, a następnie kliknij przycisk **dalej**.  
  
5.  Na **wybierz typ regionu formularza, którego chcesz utworzyć** kliknij przycisk **Zamień wszystkie**, a następnie kliknij przycisk **dalej**.  
  
     A *Zamień wszystkie* regionu formularza zamienia cały formularz programu Outlook. Aby uzyskać więcej informacji na temat typów regionu formularza, zobacz [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).  
  
6.  Na **Podaj opis, a następnie wybierz preferencje wyświetlania** kliknij przycisk **dalej**.  
  
7.  Na **zidentyfikować klasy wiadomości, które spowoduje wyświetlenie tego regionu formularza** strony w **klas niestandardowych komunikatów, które spowoduje wyświetlenie tego regionu formularza** wpisz **IPM. Task.TaskFormRegion**, a następnie kliknij przycisk **Zakończ**.  
  
     Plik TaskFormRegion.cs lub TaskFormRegion.vb jest dodane do projektu.  
  
## <a name="handling-the-events-of-controls-on-the-form-region"></a>Obsługa zdarzeń kontroli regionu formularza  
 Teraz, gdy masz regionów formularzy w projekcie, możesz dodać kod obsługujący zdarzenia Microsoft.Office.Interop.Outlook.OlkCommandButton.Click przycisku, który został dodany do regionów formularzy w programie Outlook.  
  
 Ponadto Dodaj kod, aby <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> zdarzeń, która aktualizuje formantów na region formularza, gdy region formularza zostanie wyświetlony.  
  
#### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>Do obsługi zdarzeń dla formantów na region formularza  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy TaskFormRegion.cs lub TaskFormRegion.vb, a następnie kliknij przycisk **kod widoku**.  
  
     TaskFormRegion.cs lub TaskFormRegion.vb zostanie otwarty w edytorze kodu.  
  
2.  Dodaj następujący kod do `TaskFormRegion` klasy. Ten kod wypełnienie pola kombi na regionu formularza z wiersz tematu każdego zadania w folderze zadań programu Outlook.  
  
     [!code-csharp[Trin_Outlook_FR_Import#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#1)]
     [!code-vb[Trin_Outlook_FR_Import#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#1)]  
  
3.  Dodaj następujący kod do `TaskFormRegion` klasy. Kod będzie wykonywał następujące zadania:  
  
    -   Lokalizuje Microsoft.Office.Interop.Outlook.TaskItem w folderze zadań, wywołując `FindTaskBySubjectName` metody pomocniczej i przekazywanie temat żądane zadania. Spowoduje dodanie `FindTaskBySubjectName` metody pomocniczej w następnym kroku.  
  
    -   Dodaje wartości Microsoft.Office.Interop.Outlook.TaskItem.Subject i Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete do listy zadań zależnych.  
  
    -   Dodaje temat zadania do pola ukryte w regionu formularza. Ukryte pole przechowuje te wartości jako część elementu programu Outlook.  
  
     [!code-csharp[Trin_Outlook_FR_Import#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#2)]
     [!code-vb[Trin_Outlook_FR_Import#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#2)]  
  
4.  Dodaj następujący kod do `TaskFormRegion` klasy. Ten kod zawiera metody pomocnika `FindTaskBySubjectName` który został opisany w poprzednim kroku.  
  
     [!code-csharp[Trin_Outlook_FR_Import#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#3)]
     [!code-vb[Trin_Outlook_FR_Import#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#3)]  
  
5.  Dodaj następujący kod do `TaskFormRegion` klasy. Kod będzie wykonywał następujące zadania:  
  
    -   Odświeża pola listy na regionu formularza z bieżącym stanem ukończenia każdego zadania zależne.  
  
    -   Analizuje pole tekstu ukrytego uzyskanie podmiotu każdego zadania zależne. Następnie klient zlokalizuje każdego Microsoft.Office.Interop.Outlook.TaskItem w folderze zadań, wywołując `FindTaskBySubjectName` metody pomocniczej i przekazywanie podmiotu każdego zadania.  
  
    -   Dodaje wartości Microsoft.Office.Interop.Outlook.TaskItem.Subject i Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete do listy zadań zależnych.  
  
     [!code-csharp[Trin_Outlook_FR_Import#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#4)]
     [!code-vb[Trin_Outlook_FR_Import#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#4)]  
  
6.  Zastąp `TaskFormRegion_FormRegionShowing` obsługi zdarzeń z następującym kodem. Kod będzie wykonywał następujące zadania:  
  
    -   Wypełnienie pola kombi na regionu formularza z zadań tematów, gdy region formularza zostanie wyświetlony.  
  
    -   Wywołania `RefreshTaskListBox` metody pomocniczej, gdy region formularza zostanie wyświetlony. Spowoduje to wyświetlenie zależne zadania, które zostały dodane do pola listy, jeśli element został wcześniej otwarty.  
  
     [!code-csharp[Trin_Outlook_FR_Import#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#5)]
     [!code-vb[Trin_Outlook_FR_Import#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#5)]  
  
## <a name="testing-the-outlook-form-region"></a>Testowanie regionów formularzy programu Outlook  
 Aby przetestować regionu formularza, należy dodać zadania do listy zadań wstępnych na regionu formularza. Zaktualizuj stan ukończenia zadania wymagań wstępnych, a następnie Wyświetl stan ukończenia zaktualizowane zadania na liście zadań wymagań wstępnych.  
  
#### <a name="to-test-the-form-region"></a>Aby przetestować regionu formularza  
  
1.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
     Uruchamia program Outlook.  
  
2.  W programie Outlook na **Home** , kliknij pozycję **nowych elementów**, a następnie kliknij przycisk **zadań**.  
  
3.  W formularzu zadania wpisz **zadanie zależne** w **podmiotu** pola.  
  
4.  Na **zadań** karty wstążki w **akcje** kliknij przycisk **Zapisz i Zamknij**.  
  
5.  W programie Outlook na **Home** , kliknij pozycję **nowych elementów**, kliknij przycisk **więcej elementów**, a następnie kliknij przycisk **wybierz formularz**.  
  
6.  W **wybierz formularz** okno dialogowe, kliknij przycisk **TaskFormRegion**, a następnie kliknij przycisk **Otwórz**.  
  
     **TaskFormRegion** region formularza zostanie wyświetlony. Ten formularz zastępuje formularza całego zadania. **Wybierz zadanie, aby dodać do listy zadań zależnych** pola kombi jest wypełniane przy użyciu innych zadań w folderze zadania.  
  
7.  W formularzu zadania w **podmiotu** wpisz **głównym zadaniem**.  
  
8.  W **wybierz zadanie, aby dodać do listy zadań zależnych** pola kombi, wybierz **zadanie zależne**, a następnie kliknij przycisk **Dodaj zadanie zależne**.  
  
     **0% Complete — zadanie zależne** pojawia się w **tego zadania zależy od następujących zadań** pola listy. Oznacza to, pomyślnie obsługi zdarzeń Microsoft.Office.Interop.Outlook.OlkCommandButton.Click przycisku.  
  
9. Zapisz i Zamknij **głównym zadaniem** elementu.  
  
10. Otwórz element zależnego zadania w programie Outlook.  
  
11. W formularzu zadania zależne zmienić **Ukończono** do **50%**.  
  
12. Na **zadań** karty wstążki zadania zależne w **akcje** kliknij przycisk **Zapisz i Zamknij**.  
  
13. Otwórz ponownie **głównym zadaniem** elementu programu Outlook.  
  
     **50% Complete — zadanie zależne** jest teraz wyświetlany w **tego zadania zależy od następujących zadań** pola listy.  
  
## <a name="next-steps"></a>Następne kroki  
 Można poznać więcej informacji na temat sposobu dostosowywania interfejsu użytkownika aplikacji Outlook w tych tematach:  
  
-   Aby dowiedzieć się więcej na temat projektowania wyglądu regionów formularzy przez przeciągania zarządzane formanty do projektanta wizualnego, zobacz [wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
-   Aby dowiedzieć się więcej o dostosowywaniu wstążki elementu programu Outlook, zobacz [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
-   Aby dowiedzieć się więcej na temat sposobu dodawania niestandardowego okienka zadań do programu Outlook, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Porady: dodawanie regionu formularza na projekt dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Instrukcje: Ochrona programu Outlook przed wyświetlaniem regionów formularzy](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  