---
title: 'Wskazówki: Tworzenie pierwszego VSTO dodatek dla programu Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Outlook [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25155e6dee56fd816425f795a5082667c90c242a
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845551"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>Wskazówki: Tworzenie pierwszego VSTO dodatek dla programu Outlook
  W tym przewodniku przedstawiono sposób tworzenia dodatku VSTO dla programu Microsoft Office Outlook. Funkcje, które możesz utworzyć w tego rodzaju rozwiązania są dostępne dla aplikacji, niezależnie od tego, która jest otwarta elementu programu Outlook. Aby uzyskać więcej informacji, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie projektów dodatku VSTO dla programu Outlook dla programu Outlook.  
  
-   Pisanie kodu, który używa modelu obiektów programu Outlook można dodać tekstu do tematu i treści nową wiadomość e-mail.  
  
-   Tworzenie i uruchamianie projektu, aby przetestować go.  
  
-   Czyszczenie projektu ukończone, aby dodatku VSTO już nie uruchamia automatycznie na komputerze deweloperskim.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Outlook  
  
## <a name="create-the-project"></a>Utwórz projekt  
  
### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Aby utworzyć nowy projekt programu Outlook w programie Visual Studio  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów rozwiń **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office i SharePoint**.  
  
4.  Pod rozwiniętym **Office i SharePoint** węzła, wybierz opcję **dodatków pakietu Office** węzła.  
  
5.  Na liście szablony projektów wybierz projektów dodatku VSTO dla programu Outlook.  
  
6.  W **nazwa** wpisz **FirstOutlookAddIn**.  
  
7.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstOutlookAddIn** projektu i otwiera **thisaddin —** pliku kodu w edytorze.  
  
## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Pisanie kodu, który dodaje tekst do każdego nową wiadomość e-mail  
 Następnie dodaj kod do klasy ThisAddIn pliku kodu. Nowy kod używa modelu obiektów programu Outlook można dodać tekstu do każdego nową wiadomość e-mail. Domyślnie plik kodu klasy ThisAddIn zawiera następujące wygenerowanego kodu:  
  
-   Częściową definicją `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Outlook. Aby uzyskać więcej informacji, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md). W pozostałej części `ThisAddIn` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.  
  
-   `ThisAddIn_Startup` i `ThisAddIn_Shutdown` procedury obsługi zdarzeń. Te programy obsługi zdarzeń są wywoływane, gdy program Outlook ładuje i zwalnia z dodatku VSTO. Użyj tych programów obsługi zdarzeń zainicjować dodatku VSTO z po załadowaniu go, a także aby wyczyścić zasoby używane przez dodatek VSTO, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Aby dodać tekst do tematu i treści każdego nową wiadomość e-mail  
  
1.  W pliku kodu klasy ThisAddIn, należy zadeklarować pole o nazwie `inspectors` w `ThisAddIn` klasy. `inspectors` Pola obsługuje odwołania do kolekcji inspektora windows w bieżącym wystąpieniu programu Outlook. To odwołanie uniemożliwia zwolnić pamięć, który zawiera program obsługi zdarzeń dla modułu zbierającego elementy bezużyteczne <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzeń.  
  
     [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]  
  
2.  Zastąp `ThisAddIn_Startup` metodę z następującym kodem. Ten kod dołącza program obsługi zdarzeń do <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzeń.  
  
     [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
     [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]  
  
3.  W pliku kodu klasy ThisAddIn, Dodaj następujący kod do `ThisAddIn` klasy. Ten kod definiuje programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzeń.  
  
     Gdy użytkownik tworzy nową wiadomość e-mail, ten program obsługi zdarzeń dodaje tekst do tematu i treści wiadomości.  
  
     [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
     [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]  
  
 Aby zmodyfikować każdy nową wiadomość e-mail, w poprzednich przykładach kodu za pomocą następujących obiektów:  
  
-   `Application` Pole `ThisAddIn` klasy. `Application` Pola zwraca <xref:Microsoft.Office.Interop.Outlook.Application> obiektu, który reprezentuje bieżące wystąpienie programu Outlook.  
  
-   `Inspector` Parametrów programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzeń. `Inspector` Parametr jest <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektu, który reprezentuje okna Inspektora nową wiadomość e-mail. Aby uzyskać więcej informacji, zobacz [rozwiązania programu Outlook](../vsto/outlook-solutions.md).  
  
## <a name="test-the-project"></a>Projekt testowy  
 Podczas skompilować i uruchomić projekt, sprawdź, czy tekst jest wyświetlany w wierszu tematu i treści nową wiadomość e-mail.  
  
### <a name="to-test-the-project"></a>Aby przetestować projekt  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.  
  
     Podczas kompilowania projektu kod jest kompilowany do zestawu, który znajduje się w folderze wyjściowym kompilacji dla projektu. Program Visual Studio tworzy również zbiór wpisów rejestru, które umożliwiają programu Outlook odnaleźć i załadować dodatku VSTO i konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby włączyć dodatku VSTO do uruchomienia. Aby uzyskać więcej informacji, zobacz [Omówienie procesu kompilacji rozwiązania pakietu Office](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).  
  
2.  W programie Outlook utwórz nową wiadomość e-mail.  
  
3.  Sprawdź, czy następujący tekst została dodana do tematu i treści wiadomości.  
  
     **Ten tekst został dodany przy użyciu kodu.**  
  
4.  Zamknij program Outlook.  
  
## <a name="clean-up-the-project"></a>Czyszczenie projektu  
 Po zakończeniu tworzenia projektu, Usuń dodatku VSTO zestaw, wpisy rejestru i ustawienia zabezpieczeń na komputerze projektowym. W przeciwnym razie dodatku VSTO uruchomi każdym otwarciu programu Outlook na komputerze dewelopera.  
  
### <a name="to-clean-up-your-project"></a>Aby wyczyścić projektu  
  
1.  W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czystą rozwiązania**.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, gdy utworzono podstawowe Add VSTO dla programu Outlook, można dowiedzieć się więcej o umożliwiające tworzenie dodatków narzędzi VSTO z tych tematów:  
  
-   Ogólne zadania programowania, które można wykonywać za pomocą dodatków narzędzi VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
-   Za pomocą modelu obiektów programu Outlook. Aby uzyskać więcej informacji, zobacz [rozwiązania programu Outlook](../vsto/outlook-solutions.md).  
  
-   Dostosowywanie interfejsu użytkownika programu Outlook, na przykład przez dodanie kart niestandardowych do Wstążki lub tworzenia własnego niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
-   Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [rozwiązań Office kompilacji](../vsto/building-office-solutions.md).  
  
-   Wdrażanie dodatków narzędzi VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Program dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Rozwiązania programu Outlook](../vsto/outlook-solutions.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Przegląd szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)  
  
  