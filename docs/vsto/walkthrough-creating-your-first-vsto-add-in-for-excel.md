---
title: 'Wskazówki: Tworzenie pierwszego dodatek VSTO dla programu Excel'
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
- Excel [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6421df0109d68d2647cafff5713aecb297c3536d
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845811"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Wskazówki: Tworzenie pierwszego dodatek VSTO dla programu Excel
  Ten Przewodnik wprowadzający przedstawia sposób tworzenia dodatku poziomie aplikacji dla programu Microsoft Office Excel. Funkcje, które możesz utworzyć w tego rodzaju rozwiązania są dostępne dla aplikacji, niezależnie od tego, które są otwarte skoroszyty.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie projektów dodatku VSTO programu Excel dla programu Excel.  
  
-   Pisanie kodu, który używa modelu obiektów programu Excel można dodać tekstu do skoroszytu, po jego zapisaniu.  
  
-   Tworzenie i uruchamianie projektu, aby przetestować go.  
  
-   Czyszczenie projektu ukończone, aby dodatku VSTO już nie uruchamia automatycznie na komputerze deweloperskim.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Utwórz projekt  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Aby utworzyć nowy projekt dodatku VSTO programu Excel w programie Visual Studio  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów rozwiń **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office i SharePoint**.  
  
4.  Pod rozwiniętym **Office i SharePoint** węzła, wybierz opcję **dodatków pakietu Office** węzła.  
  
5.  Na liście szablony projektów, wybierz **programu Excel 2010 Add-in** lub **programu Excel 2013 Add-in**.  
  
6.  W **nazwa** wpisz **FirstExcelAddIn**.  
  
7.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstExcelAddIn** projektu i otwarcie pliku kodu klasy ThisAddIn w edytorze.  
  
## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Napisz kod umożliwiający dodawanie tekstu do zapisanego skoroszytu  
 Następnie dodaj kod do klasy ThisAddIn pliku kodu. Nowy kod używa modelu obiektów programu Excel, aby wstawić tekst podstawowy w pierwszym wierszu aktywnego arkusza. Aktywny arkusz jest arkusza, która jest otwarta, gdy użytkownik zapisuje skoroszytu. Domyślnie plik kodu klasy ThisAddIn zawiera następujące wygenerowanego kodu:  
  
-   Częściową definicją `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Excel. Aby uzyskać więcej informacji, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md). W pozostałej części `ThisAddIn` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.  
  
-   `ThisAddIn_Startup` i `ThisAddIn_Shutdown` procedury obsługi zdarzeń. Te programy obsługi zdarzeń są wywoływane, gdy program Excel ładuje i zwalnia z dodatku VSTO. Użyj tych programów obsługi zdarzeń zainicjować dodatku VSTO z po załadowaniu go, a także aby wyczyścić zasoby używane przez dodatek, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Aby dodać wiersz tekstu do zapisanego skoroszytu  
  
1.  W pliku kodu klasy ThisAddIn, Dodaj następujący kod do `ThisAddIn` klasy. Nowy kod definiuje programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzenie, które jest wywoływane, gdy skoroszyt jest zapisywany.  
  
     Gdy użytkownik zapisuje skoroszyt, program obsługi zdarzeń dodaje nowy tekst w chwili rozpoczęcia aktywnego arkusza.  
  
     [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]  
  
2.  Jeśli używasz języka C#, Dodaj następujący kod wymagany do `ThisAddIn_Startup` obsługi zdarzeń. Ten kod służy do łączenia `Application_WorkbookBeforeSave` obsługi zdarzeń z <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzeń.  
  
     [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]  
  
 Można zmodyfikować skoroszytu, po jego zapisaniu, w poprzednich przykładach kodu za pomocą następujących obiektów:  
  
-   `Application` Pole `ThisAddIn` klasy. `Application` Pola zwraca <xref:Microsoft.Office.Interop.Excel.Application> obiektu, który reprezentuje bieżące wystąpienie programu Excel.  
  
-   `Wb` Parametrów programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzeń. `Wb` Parametr jest <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu, który reprezentuje zapisany skoroszyt. Aby uzyskać więcej informacji, zobacz [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).  
  
## <a name="test-the-project"></a>Projekt testowy  
  
### <a name="to-test-the-project"></a>Aby przetestować projekt  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.  
  
     Podczas kompilowania projektu kod jest kompilowany do zestawu, który znajduje się w folderze wyjściowym kompilacji dla projektu. Program Visual Studio tworzy również zbiór wpisów rejestru, które umożliwiają programu Excel odnaleźć i załadować dodatku VSTO i konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby włączyć dodatku VSTO do uruchomienia. Aby uzyskać więcej informacji, zobacz [rozwiązań Office kompilacji](../vsto/building-office-solutions.md).  
  
2.  W programie Excel Zapisz skoroszyt.  
  
3.  Sprawdź, czy następujący tekst została dodana do skoroszytu.  
  
     **Ten tekst został dodany przy użyciu kodu.**  
  
4.  Zamknij program Excel.  
  
## <a name="clean-up-the-project"></a>Czyszczenie projektu  
 Po zakończeniu tworzenia projektu, Usuń dodatku VSTO zestaw, wpisy rejestru i ustawienia zabezpieczeń na komputerze projektowym. W przeciwnym razie dodatku VSTO będzie nadal działać zawsze otwierania programu Excel na komputerze deweloperskim.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończone projektu na komputerze deweloperskim  
  
1.  W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czystą rozwiązania**.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, po utworzeniu podstawowego dodatku VSTO dla programu Excel, można dowiedzieć się więcej o umożliwiające tworzenie dodatków narzędzi VSTO z tych tematów:  
  
-   Ogólne zadania programowania, które można wykonywać w dodatkach VSTO: [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
-   Zadania związane z programowaniem, które są specyficzne dla dodatków VSTO programu Excel: [rozwiązań w programie Excel](../vsto/excel-solutions.md).  
  
-   Za pomocą modelu obiektów programu Excel: [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).  
  
-   Dostosowywanie interfejsu użytkownika (UI) programu Excel, na przykład poprzez dodanie kart niestandardowych do Wstążki lub tworzenia własnego niestandardowego okienka zadań: [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
-   Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu Excel: [rozwiązań Office kompilacji](../vsto/building-office-solutions.md).  
  
-   Wdrażanie dodatków narzędzi VSTO dla programu Excel: [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Rozwiązania programu Excel](../vsto/excel-solutions.md)   
 [Program dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Przegląd szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)  
  
  