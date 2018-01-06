---
title: "Wskazówki: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word | Dokumentacja firmy Microsoft"
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
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
ms.assetid: ec9f5173-0923-4aee-985a-e760e80eaae3
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6d732f16d6794fbe59dd6f67fa904fcee916ce69
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-your-first-document-level-customization-for-word"></a>Wskazówki: tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word
  Ten Przewodnik wprowadzający pokazuje, jak utworzyć dostosowania poziomie dokumentu dla programu Microsoft Office Word. Funkcje, które możesz utworzyć w tego rodzaju rozwiązania są dostępne tylko wtedy, gdy określony dokument jest otwarty. Nie możesz użyć dostosowania poziomie dokumentu do zmiany całej aplikacji, na przykład po otwarciu dokumentu, wyświetlanie nowej karty wstążki.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie projektu dokument programu Word.  
  
-   Dodawanie tekstu do dokumentu, który znajduje się w projektancie programu Visual Studio.  
  
-   Pisanie kodu, który używa modelu obiektów programu Word można dodać tekstu do dokumentu dostosowane po otwarciu.  
  
-   Tworzenie i uruchamianie projektu, aby przetestować go.  
  
-   Czyszczenie projektu, aby usunąć niepotrzebne kompilacji pliki i ustawienia zabezpieczeń na komputerze projektowym.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
  
#### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Aby utworzyć nowy projekt dokumentu programu Word w Visual Studio  
  
1.  Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W okienku szablonów rozwiń **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office i SharePoint**.  
  
4.  Pod rozwiniętym **Office i SharePoint** węzła, wybierz opcję **dodatków pakietu Office** węzła.  
  
5.  Na liście szablony projektów wybierz projekt dokument VSTO programu Word.  
  
6.  W **nazwa** wpisz **FirstDocumentCustomization**.  
  
7.  Kliknij przycisk **OK**.  
  
     **Visual Studio Tools dla pakietu Office, Kreator projektu** otwiera.  
  
8.  Wybierz **Utwórz nowy dokument**i kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Tworzy **FirstDocumentCustomization** projektu i dodaje **FirstDocumentCustomization** dokument i ThisDocument pliku kodu do projektu. **FirstDocumentCustomization** automatycznie otworzyć dokumentu w projektancie.  
  
## <a name="closing-and-reopening-the-document-in-the-designer"></a>Zamknąć i ponownie otworzyć dokument w Projektancie  
 Jeśli celowo lub przypadkowo zamknięto dokumentu w Projektancie podczas tworzenia projektu, zostanie ponownie otwarty.  
  
#### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Aby zamknąć i ponownie otworzyć dokument w Projektancie  
  
1.  Zamyka dokument, klikając **Zamknij** przycisk (X) dla okna projektanta.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument** code pliku, a następnie kliknij przycisk **Widok projektanta**.  
  
     \-lub -  
  
     W **Eksploratora rozwiązań**, kliknij dwukrotnie **ThisDocument** pliku kodu.  
  
## <a name="adding-text-to-the-document-in-the-designer"></a>Dodawanie tekstu do dokumentu w Projektancie  
 Interfejs użytkownika (UI) można zaprojektować z opcji dostosowania, modyfikując dokument, który jest otwarty w projektancie. Na przykład można dodać tekstu, tabel lub formanty programu Word. Aby uzyskać więcej informacji o sposobie używania projektanta, zobacz [projekty pakietu Office w Visual Studio środowiska](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
#### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Aby dodać tekstu do dokumentu przy użyciu narzędzia Projektant  
  
1.  W dokumencie, który jest otwarty w Projektancie tekst.  
  
     **Ten tekst został dodany przy użyciu projektanta.**  
  
## <a name="adding-text-to-the-document-programmatically"></a>Programowane Dodawanie tekstu do dokumentu  
 Następnie dodaj kod do pliku kodu ThisDocument. Nowy kod używa modelu obiektów programu Word, aby dodać drugi akapit tekstu do dokumentu. Domyślnie plik kodu ThisDocument zawiera następujące wygenerowanego kodu:  
  
-   Częściową definicją `ThisDocument` klasy, która reprezentuje model programowania dokumentu i zapewnia dostęp do modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz [element hosta dokumentu](../vsto/document-host-item.md) i [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md). W pozostałej części `ThisDocument` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.  
  
-   `ThisDocument_Startup` i `ThisDocument_Shutdown` procedury obsługi zdarzeń. Te programy obsługi zdarzeń są wywoływane, gdy dokument jest otwarte i zamknięte. Użyj tych programów obsługi zdarzeń zainicjować dostosowanie po otwarciu dokumentu, a także aby wyczyścić zasoby używane przez dostosowanie, gdy dokument zostanie zamknięty. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Aby dodać drugi akapit tekstu do dokumentu przy użyciu kodu  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument**, a następnie kliknij przycisk **kod widoku**.  
  
     Otwiera plik kodu w programie Visual Studio.  
  
2.  Zastąp `ThisDocument_Startup` obsługi zdarzeń z następującym kodem. Po otwarciu dokumentu, ten kod dodaje drugi akapit tekstu do dokumentu.  
  
     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]  
  
    > [!NOTE]  
    >  Ten kod zawiera wartość indeksu 1 dostępu w pierwszym akapicie do <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A> właściwości. Visual Basic i Visual C# Użyj tablic oparte na 0, 1 jest niższe granice tablicy w większości kolekcji w modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz [pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="testing-the-project"></a>Testowanie projektu  
  
#### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.  
  
     Podczas kompilowania projektu kod jest kompilowany do zestawu, który jest skojarzony z dokumentem. Visual Studio umieszcza kopię dokumentu i zestawu w folderze wyjściowym kompilacji projektu i konfiguruje ustawienia zabezpieczeń na komputerze dewelopera umożliwiające dostosowanie do uruchomienia. Aby uzyskać więcej informacji, zobacz [kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
2.  W tym dokumencie Sprawdź, czy zostanie wyświetlony następujący tekst.  
  
     **Ten tekst został dodany przy użyciu projektanta.**  
  
     **Ten tekst został dodany przy użyciu kodu.**  
  
3.  Zamyka dokument.  
  
## <a name="cleaning-up-the-project"></a>Czyszczenie projektu  
 Po zakończeniu tworzenia projektu, należy usunąć pliki w folderze wyjściowym kompilacji i ustawienia zabezpieczeń utworzone przez proces kompilacji.  
  
#### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończone projektu na komputerze deweloperskim  
  
1.  W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czystą rozwiązania**.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, po utworzeniu podstawowego dostosowywania poziomie dokumentu dla programu Word, można dowiedzieć się więcej o opracowanie dostosowań w tych tematach:  
  
-   Ogólne zadania programowania, które można wykonywać w dostosowaniach na poziomie dokumentu: [programowania dostosowań na poziome dokumentu](../vsto/programming-document-level-customizations.md).  
  
-   Zadania związane z programowaniem, które są specyficzne dla dostosowań na poziomie dokumentu dla programu Word: [rozwiązania programu Word](../vsto/word-solutions.md).  
  
-   Za pomocą modelu obiektów programu Word: [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md).  
  
-   Dostosowywanie interfejsu użytkownika programu Word, na przykład przez dodawanie kart niestandardowych do Wstążki lub tworzenie własnych okienko akcji: [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
-   Przy użyciu rozszerzonych obiektów programu Word podał rozwiązań pakietu Office w Visual Studio do wykonywania zadań, które nie są możliwe za pomocą modelu obiektów programu Word (na przykład zarządzane formanty w dokumentach i hostingu powiązywanie kontrolek programu Word z danymi przy użyciu danych formularzy systemu Windows Powiązanie modelu): [automatyzacji programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Kompilowanie i debugowanie na poziomie dokumentu dla programu Word: [kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
-   Wdrażanie dostosowań na poziomie dokumentu dla programu Word: [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwój rozwiązań Office ― omówienie &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Rozwiązania programu Word](../vsto/word-solutions.md)   
 [Programowania dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Przegląd modelu obiektów programu Word](../vsto/word-object-model-overview.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)  
  
  