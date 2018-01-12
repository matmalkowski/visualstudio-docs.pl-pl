---
title: "Wskazówki: Tworzenie Twojego pierwszego dodatku narzędzi VSTO dla programu Word | Dokumentacja firmy Microsoft"
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
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Word [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3452bd5e550ab724dc6c236515579869814a9237
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-word"></a>Przewodnik: tworzenie pierwszego dodatku narzędzi VSTO dla programu Word
  Ten Przewodnik wprowadzający przedstawia sposób tworzenia dodatku VSTO dla programu Microsoft Office Word. Funkcje, które możesz utworzyć w tego rodzaju rozwiązania są dostępne dla aplikacji, niezależnie od tego, które są otwarte dokumenty.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie projektów dodatku VSTO programu Word.  
  
-   Pisanie kodu korzystającego z modelu obiektów programu Word można dodać tekstu do dokumentu, po jego zapisaniu.  
  
-   Tworzenie i uruchamianie projektu, aby przetestować go.  
  
-   Czyszczenie projektu ukończone, aby dodatku VSTO już nie uruchamia automatycznie na komputerze deweloperskim.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
  
#### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Aby utworzyć nowy projekt dodatku VSTO programu Word w Visual Studio  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów rozwiń **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office i SharePoint**.  
  
4.  Pod rozwiniętym **Office i SharePoint** węzła, wybierz opcję **dodatków pakietu Office** węzła.  
  
5.  Na liście szablony projektów wybierz projektów dodatku VSTO programu Word.  
  
6.  W **nazwa** wpisz **FirstWordAddIn**.  
  
7.  Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Tworzy **FirstWordAddIn** projektu i otwarcie pliku kodu klasy ThisAddIn w edytorze.  
  
## <a name="writing-code-to-add-text-to-the-saved-document"></a>Pisanie kodu, aby dodać tekstu do zapisanego dokumentu  
 Następnie dodaj kod do klasy ThisAddIn pliku kodu. Nowy kod używa modelu obiektów programu Word, aby dodawać tekst standardowy do każdego zapisany dokument. Domyślnie plik kodu klasy ThisAddIn zawiera następujące wygenerowanego kodu:  
  
-   Częściową definicją `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). W pozostałej części `ThisAddIn` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.  
  
-   `ThisAddIn_Startup` i `ThisAddIn_Shutdown` procedury obsługi zdarzeń. Te programy obsługi zdarzeń są wywoływane, gdy program Word ładuje i zwalnia z dodatku VSTO. Użyj tych programów obsługi zdarzeń zainicjować dodatku VSTO z po załadowaniu go, a także aby wyczyścić zasoby używane przez dodatek VSTO, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Aby dodać tekstu akapitu do zapisanego dokumentu  
  
1.  W pliku kodu klasy ThisAddIn, Dodaj następujący kod do `ThisAddIn` klasy. Nowy kod definiuje programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzenie, które jest wywoływane, gdy dokument zostanie zapisany.  
  
     Gdy użytkownik zapisuje dokument, program obsługi zdarzeń dodaje nowy tekst na początku dokumentu.  
  
     [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]  
  
    > [!NOTE]  
    >  Ten kod zawiera wartość indeksu 1 dostępu w pierwszym akapicie do <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> kolekcji. Visual Basic i Visual C# Użyj tablic oparte na 0, 1 jest niższe granice tablicy w większości kolekcji w modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz [pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md).  
  
2.  Jeśli używasz języka C#, Dodaj następujący kod wymagany do `ThisAddIn_Startup` obsługi zdarzeń. Ten kod służy do łączenia `Application_DocumentBeforeSave` obsługi zdarzeń z <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeń.  
  
     [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]  
  
 Aby zmodyfikować dokumentu, po jego zapisaniu, w poprzednich przykładach kodu Użyj następujących obiektów:  
  
-   `Application` Pole `ThisAddIn` klasy. `Application` Pola zwraca <xref:Microsoft.Office.Interop.Word.Application> obiektu, który reprezentuje bieżące wystąpienie programu Word.  
  
-   `Doc` Parametrów programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeń. `Doc` Parametr jest <xref:Microsoft.Office.Interop.Word.Document> obiektu, który reprezentuje zapisany dokument. Aby uzyskać więcej informacji, zobacz [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md).  
  
## <a name="testing-the-project"></a>Testowanie projektu  
  
#### <a name="to-test-the-project"></a>Aby przetestować projekt  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.  
  
     Podczas kompilowania projektu kod jest kompilowany do zestawu, który znajduje się w folderze wyjściowym kompilacji dla projektu. Program Visual Studio tworzy również zbiór wpisów rejestru, umożliwiających Word odnaleźć i załadować dodatku VSTO i konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby włączyć dodatku VSTO do uruchomienia. Aby uzyskać więcej informacji, zobacz [kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
2.  W programie Word zapisuje aktywny dokument.  
  
3.  Sprawdź, czy następujący tekst została dodana do dokumentu.  
  
     **Ten tekst został dodany przy użyciu kodu.**  
  
4.  Zamknij program Word.  
  
## <a name="cleaning-up-the-project"></a>Czyszczenie projektu  
 Po zakończeniu tworzenia projektu, Usuń dodatku VSTO zestaw, wpisy rejestru i ustawienia zabezpieczeń na komputerze projektowym. W przeciwnym razie dodatku VSTO będzie nadal działać zawsze Otwórz program Word na komputerze deweloperskim.  
  
#### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończone projektu na komputerze deweloperskim  
  
1.  W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czystą rozwiązania**.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, po utworzeniu podstawowego dodatku VSTO dla programu Word, można dowiedzieć się więcej o umożliwiające tworzenie dodatków narzędzi VSTO z tych tematów:  
  
-   Ogólne zadania programowania, które można wykonywać w dodatkach VSTO: [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Zadania związane z programowaniem, które są specyficzne dla dodatków VSTO programu Word: [rozwiązania programu Word](../vsto/word-solutions.md).  
  
-   Za pomocą modelu obiektów programu Word: [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md).  
  
-   Dostosowywanie interfejsu użytkownika programu Word, na przykład poprzez dodanie kart niestandardowych do Wstążki lub tworzenia własnego niestandardowego okienka zadań: [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
-   Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu Word: [kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
-   Wdrażanie dodatków narzędzi VSTO dla programu Word: [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwój rozwiązań Office ― omówienie &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Rozwiązania programu Word](../vsto/word-solutions.md)   
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)  
  
  