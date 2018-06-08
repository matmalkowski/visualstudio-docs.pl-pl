---
title: 'Wskazówki: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2a63dd4eae31b99646af04ceabe76e4edb946027
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845707"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Wskazówki: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel
  Ten Przewodnik wprowadzający pokazuje, jak utworzyć dostosowania poziomie dokumentu dla programu Microsoft Office Excel. Funkcje, które możesz utworzyć w tego rodzaju rozwiązania są dostępne tylko wtedy, gdy wybrany skoroszyt jest otwarty. Nie możesz użyć dostosowania poziomie dokumentu do zmiany całej aplikacji, na przykład po otwarciu dowolnego skoroszytu, wyświetlanie nowej karty wstążki.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie projektu skoroszyt programu Excel.  
  
-   Dodawanie tekstu do arkusza obsługiwanej w projektancie programu Visual Studio.  
  
-   Pisanie kodu, który używa modelu obiektów programu Excel można dodać tekstu do arkusza dostosowane po otwarciu.  
  
-   Tworzenie i uruchamianie projektu, aby przetestować go.  
  
-   Czyszczenie projektu zakończone Usuń niepotrzebne kompilacji pliki i ustawienia zabezpieczeń na komputerze projektowym.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Utwórz projekt  
  
### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Aby utworzyć nowy projekt skoroszytu programu Excel w programie Visual Studio  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów rozwiń **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office i SharePoint**.  
  
4.  Pod rozwiniętym **Office i SharePoint** węzła, wybierz opcję **dodatków pakietu Office** węzła.  
  
5.  Na liście szablony projektów wybierz projektów dodatku VSTO programu Excel.  
  
6.  W **nazwa** wpisz **FirstWorkbookCustomization**.  
  
7.  Kliknij przycisk **OK**.  
  
     **Visual Studio Tools dla pakietu Office, Kreator projektu** otwiera.  
  
8.  Wybierz **Utwórz nowy dokument**i kliknij przycisk **OK**.  
  
    -   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstWorkbookCustomization** projektu i dodaje następujące pliki do projektu.  
  
    -   *FirstWorkbookCustomization*xlsx - reprezentuje skoroszytu programu Excel w projekcie. Zawiera wszystkie arkusze i wykresy.  
  
    -   Sheet1 — (*.vb* plików w języku Visual Basic lub *.cs* plik Visual C#)-arkusz zawiera powierzchni projektowej oraz kod pierwszego arkusza w skoroszycie. Aby uzyskać więcej informacji, zobacz [element hosta arkusza](../vsto/worksheet-host-item.md).  
  
    -   Sheet2 — (*.vb* plików w języku Visual Basic lub *.cs* plik Visual C#)-arkusz zawiera powierzchni projektowej oraz kod dla drugiego arkusza w skoroszycie.  
  
    -   Sheet3 — (*.vb* plików w języku Visual Basic lub *.cs* plik Visual C#)-arkusz zawiera powierzchni projektowej oraz kod trzeci arkusza w skoroszycie.  
  
    -   Ten skoroszyt (*.vb* plików w języku Visual Basic lub *.cs* plik Visual C#) — zawiera powierzchni projektowej oraz kod Dostosowywanie na poziomie skoroszytu. Aby uzyskać więcej informacji, zobacz [element hosta skoroszytu](../vsto/workbook-host-item.md).  
  
     Sheet1 — pliku kodu jest otwierana automatycznie w projektancie.  
  
## <a name="close-and-reopen-worksheets-in-the-designer"></a>Zamknij i otwórz ponownie arkuszy w Projektancie  
 Jeśli celowo lub przypadkowo zamknięciu skoroszytu lub skoroszyt w Projektancie podczas tworzenia projektu, zostanie ponownie otwarty.  
  
### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Aby zamknąć i ponownie otwórz arkusz w Projektancie  
  
1.  Zamknij skoroszyt, klikając **Zamknij** przycisk (X) dla okna projektanta.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1 —** code pliku, a następnie kliknij przycisk **Widok projektanta**.  
  
     \- lub -  
  
     W **Eksploratora rozwiązań**, kliknij dwukrotnie **Sheet1 —** pliku kodu.  
  
## <a name="add-text-to-a-worksheet-in-the-designer"></a>Dodawanie tekstu do arkusza w Projektancie  
 Interfejs użytkownika (UI) można zaprojektować z opcji dostosowania, modyfikując arkusz, który jest otwarty w projektancie. Na przykład można dodać tekstu do komórek, zastosuj formuły lub Dodaj formanty programu Excel. Aby uzyskać więcej informacji o sposobie używania projektanta, zobacz [projektów pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Aby dodać tekst do arkusza przy użyciu narzędzia Projektant  
  
1.  W arkuszu, który jest otwarty w projektancie, zaznacz komórkę **A1**, a następnie wpisz następujący tekst.  
  
     **Ten tekst został dodany przy użyciu projektanta.**  
  
> [!WARNING]  
>  Jeśli dodajesz ten wiersz tekstu komórki **A2**, zostanie on zastąpiony przez inny kod w tym przykładzie.  
  
## <a name="add-text-to-a-worksheet-programmatically"></a>Programowane Dodawanie tekstu do arkusza  
 Następnie dodaj kod do pliku kodu Sheet1 —. Nowy kod używa modelu obiektów programu Excel, aby dodać drugi wiersz tekstu w skoroszycie. Domyślnie plik kodu Sheet1 — zawiera następujące wygenerowanego kodu:  
  
-   Częściową definicją `Sheet1` klasy, która reprezentuje model programowania arkusza i zapewnia dostęp do modelu obiektów programu Excel. Aby uzyskać więcej informacji [element hosta arkusza](../vsto/worksheet-host-item.md) i [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md). W pozostałej części `Sheet1` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.  
  
-   `Sheet1_Startup` i `Sheet1_Shutdown` procedury obsługi zdarzeń. Te programy obsługi zdarzeń są wywoływane, gdy program Excel ładuje i zwalnia dostosowanie. Użyj tych programów obsługi zdarzeń zainicjować dostosowanie po załadowaniu go, a także aby wyczyścić zasoby używane przez dostosowanie, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Aby dodać drugi wiersz tekstu w arkuszu przy użyciu kodu  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Sheet1 —**, a następnie kliknij przycisk **kod widoku**.  
  
     Otwiera plik kodu w programie Visual Studio.  
  
2.  Zastąp `Sheet1_Startup` obsługi zdarzeń z następującym kodem. Po otwarciu Sheet1 — ten kod dodaje drugi wiersz tekstu w arkuszu.  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]  
  
## <a name="test-the-project"></a>Projekt testowy  
  
### <a name="to-test-your-workbook"></a>Aby przetestować skoroszytu  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.  
  
     Podczas kompilowania projektu kod jest kompilowany do zestawu, który jest skojarzony z tym skoroszycie. Visual Studio umieszcza kopię skoroszytu i zestawu w folderze wyjściowym kompilacji projektu i konfiguruje ustawienia zabezpieczeń na komputerze dewelopera umożliwiające dostosowanie do uruchomienia. Aby uzyskać więcej informacji, zobacz [rozwiązań Office kompilacji](../vsto/building-office-solutions.md).  
  
2.  W tym skoroszycie Sprawdź, czy zostanie wyświetlony następujący tekst.  
  
     **Ten tekst został dodany przy użyciu projektanta.**  
  
     **Ten tekst został dodany przy użyciu kodu.**  
  
3.  Zamknij skoroszyt.  
  
## <a name="clean-up-the-project"></a>Czyszczenie projektu  
 Po zakończeniu tworzenia projektu, należy usunąć pliki w folderze wyjściowym kompilacji i ustawienia zabezpieczeń utworzone przez proces kompilacji.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończone projektu na komputerze deweloperskim  
  
1.  W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czystą rozwiązania**.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, po utworzeniu podstawowego dostosowywania poziomie dokumentu dla programu Excel, można dowiedzieć się więcej o opracowanie dostosowań w tych tematach:  
  
-   Ogólne zadania programowania, które można wykonywać w dostosowaniach na poziomie dokumentu: [programowania dostosowań na poziome dokumentu](../vsto/programming-document-level-customizations.md).  
  
-   Zadania związane z programowaniem, które są specyficzne dla dostosowań na poziomie dokumentu dla programu Excel: [rozwiązań w programie Excel](../vsto/excel-solutions.md).  
  
-   Za pomocą modelu obiektów programu Excel: [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).  
  
-   Dostosowywanie interfejsu użytkownika programu Excel, na przykład przez dodawanie kart niestandardowych do Wstążki lub tworzenie własnych okienko akcji: [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
-   Przy użyciu rozszerzonych obiektów programu Excel udostępniane przez narzędzia deweloperskie pakietu Office w Visual Studio do wykonywania zadań, które nie są możliwe za pomocą modelu obiektów programu Excel (na przykład zarządzane formanty w dokumentach i hostingu powiązywanie kontrolek programu Excel z danymi za pomocą interfejsu Windows Forms model powiązania danych): [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).  
  
-   Kompilowanie i debugowanie dostosowań na poziomie dokumentu dla programu Excel: [rozwiązań Office kompilacji](../vsto/building-office-solutions.md).  
  
-   Wdrażanie dostosowań na poziomie dokumentu dla programu Excel: [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Rozwiązania programu Excel](../vsto/excel-solutions.md)   
 [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)   
 [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Przegląd szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)  
  
  