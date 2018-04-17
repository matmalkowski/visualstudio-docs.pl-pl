---
title: 'Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla programu PowerPoint | Dokumentacja firmy Microsoft'
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
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5814262d68d9bf32ee3a0f72e3e0a15811a75a9c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-powerpoint"></a>Przewodnik: tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint
  W tym przewodniku przedstawiono sposób tworzenia dodatku VSTO dla programu Microsoft Office PowerPoint. Funkcje, które możesz utworzyć w tego rodzaju rozwiązania są dostępne dla aplikacji, niezależnie od tego, które są otwarte prezentacji. Aby uzyskać więcej informacji, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie projektów dodatku VSTO dla programu PowerPoint dla programu PowerPoint.  
  
-   Pisanie kodu, który używa modelu obiektów programu PowerPoint można dodać pola tekstowego do każdego nowego slajdu.  
  
-   Tworzenie i uruchamianie projektu, aby przetestować go.  
  
-   Czyszczenie projektu, dzięki czemu dodatku VSTO już nie uruchamia automatycznie na komputerze deweloperskim.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów rozwiń **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office i SharePoint**.  
  
4.  Pod rozwiniętym **Office i SharePoint** węzła, wybierz opcję **dodatków pakietu Office** węzła.  
  
5.  Na liście szablony projektów wybierz projektów dodatku VSTO dla programu PowerPoint.  
  
6.  W **nazwa** wpisz **FirstPowerPointAddIn**.  
  
7.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstPowerPointAddIn** projektu i otwiera **thisaddin —** pliku kodu w edytorze.  
  
## <a name="writing-code-that-adds-text-to-each-new-slide"></a>Pisanie kodu, który dodaje tekst do każdego nowego slajdu  
 Następnie dodaj kod do klasy ThisAddIn pliku kodu. Nowy kod używa modelu obiektów programu PowerPoint, aby dodać pole tekstowe do każdego nowego slajdu. Domyślnie plik kodu klasy ThisAddIn zawiera następujące wygenerowanego kodu:  
  
-   Częściową definicją `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu PowerPoint. Aby uzyskać więcej informacji, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). W pozostałej części `ThisAddIn` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.  
  
-   `ThisAddIn_Startup` i `ThisAddIn_Shutdown` procedury obsługi zdarzeń. Te programy obsługi zdarzeń są wywoływane, gdy program PowerPoint ładuje i zwalnia z dodatku VSTO. Użyj tych programów obsługi zdarzeń zainicjować dodatku VSTO z po załadowaniu go, a także aby wyczyścić zasoby używane przez dodatek VSTO, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-text-box-to-each-new-slide"></a>Aby dodać pole tekstowe do każdego nowego slajdu  
  
1.  W pliku kodu klasy ThisAddIn, Dodaj następujący kod do `ThisAddIn` klasy. Ten kod definiuje programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> zdarzenie <xref:Microsoft.Office.Interop.PowerPoint.Application> obiektu.  
  
     Gdy użytkownik dodaje nowy slajd do aktywnej prezentacji, ten program obsługi zdarzeń dodaje pole tekstowe na początku nowego slajdu i dodaje tekst w polu tekstowym.  
  
     [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]  
  
2.  Jeśli używasz języka C#, Dodaj następujący kod do `ThisAddIn_Startup` obsługi zdarzeń. Ten kod jest wymagany do połączenia `Application_PresentationNewSlide` obsługi zdarzeń z <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> zdarzeń.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]  
  
 Aby zmodyfikować każdego nowego slajdu, w poprzednich przykładach kodu za pomocą następujących obiektów:  
  
-   `Application` Pole `ThisAddIn` klasy. `Application` Pola zwraca <xref:Microsoft.Office.Interop.PowerPoint.Application> obiektu, który reprezentuje bieżące wystąpienie programu PowerPoint.  
  
-   `Sld` Parametrów programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> zdarzeń. `Sld` Parametr jest <xref:Microsoft.Office.Interop.PowerPoint.Slide> obiektu, który reprezentuje nowego slajdu. Aby uzyskać więcej informacji, zobacz [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md).  
  
## <a name="testing-the-project"></a>Testowanie projektu  
 Jeśli skompilujesz i uruchomisz projekt, sprawdź, czy pole tekstowe jest wyświetlany w nowych slajdów, które dodajesz do prezentacji.  
  
#### <a name="to-test-the-project"></a>Aby przetestować projekt  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.  
  
     Podczas kompilowania projektu kod jest kompilowany do zestawu, który jest umieszczana w folderze wyjściowym kompilacji dla projektu. Program Visual Studio tworzy również zbiór wpisów rejestru, które umożliwiają PowerPoint odnaleźć i załadować dodatku VSTO i konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby włączyć dodatku VSTO do uruchomienia. Aby uzyskać więcej informacji, zobacz [kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
2.  W programie PowerPoint należy dodać nowy slajd do aktywnej prezentacji.  
  
3.  Sprawdź, czy następujący tekst została dodana do nowego pola tekstowego w górnej części slajdu.  
  
     **Ten tekst został dodany przy użyciu kodu.**  
  
4.  Zamknij program PowerPoint.  
  
## <a name="cleaning-up-the-project"></a>Czyszczenie projektu  
 Po zakończeniu tworzenia projektu, Usuń dodatku VSTO zestaw, wpisy rejestru i ustawienia zabezpieczeń na komputerze projektowym. W przeciwnym razie dodatku VSTO uruchomi każdym otwarciu programu PowerPoint na komputerze dewelopera.  
  
#### <a name="to-clean-up-your-project"></a>Aby wyczyścić projektu  
  
1.  W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czystą rozwiązania**.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, po utworzeniu podstawowego dodatku VSTO dla programu PowerPoint, można dowiedzieć się więcej o umożliwiające tworzenie dodatków narzędzi VSTO z tych tematów:  
  
-   Ogólne zadania programowania, które można wykonywać w dodatkach VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Za pomocą modelu obiektów programu PowerPoint. Aby uzyskać więcej informacji, zobacz [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md).  
  
-   Dostosowywanie interfejsu użytkownika programu PowerPoint, na przykład przez dodanie kart niestandardowych do Wstążki lub tworzenia własnego niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
-   Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
-   Wdrażanie dodatków narzędzi VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)  
  
  