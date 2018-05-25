---
title: 'Porady: Dodawanie okienek akcji do dokumentów programu Word lub skoroszyty programu Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ebf4896411a46b2c75edd8216bd61623bc9b728f
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Porady: dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel
  Aby dodać okienek akcji do skoroszytu programu Microsoft Excel lub dokumentu programu Microsoft Office Word, należy najpierw utworzyć formantu użytkownika formularzy systemu Windows. Następnie dodaj kontrolkę użytkownika do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwość `ThisDocument.ActionsPane` pola (Word) lub `ThisWorkbook.ActionsPane` pola (Excel) w projekcie.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Tworzenie formantu użytkownika  
 W poniższej procedurze wyjaśniono sposób tworzenia kontrolki użytkownika w programie lub projekt programu Excel. Dodaje również przycisk do kontrolki użytkownika, który zapisuje tekstu do dokumentu lub skoroszytu, po kliknięciu.  
  
#### <a name="to-create-the-user-control"></a>Aby utworzyć kontrolkę użytkownika  
  
1.  Otwórz projekt poziomie dokumentu programu Word i Excel w Visual Studio.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **formant okienka Akcje**, nadaj jej nazwę **HelloControl**i kliknij przycisk **Dodaj**.  
  
    > [!NOTE]  
    >  Możesz również dodać **kontrolki użytkownika** elementu do projektu. Klasy generowane przez **formant okienka Akcje** i **kontrolki użytkownika** elementy działają tak samo.  
  
4.  Z **formularzy systemu Windows** karcie **przybornika,** przeciągnij **przycisk** formantu w formancie.  
  
    > [!NOTE]  
    >  Jeśli formant nie jest widoczne w projektancie, kliknij dwukrotnie **HelloControl** w **Eksploratora rozwiązań**.  
  
5.  Dodaj kod, aby <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń przycisku. Poniższy przykład przedstawia kod dla dokumentu programu Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  W języku C# należy dodać obsługi zdarzenia kliknięcia przycisku. Możesz umieścić ten kod w `HelloControl` Konstruktor po wywołaniu `IntializeComponent`.  
  
     Aby uzyskać informacje o sposobie tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="add-the-user-control-to-the-actions-pane"></a>Dodaj kontrolkę użytkownika w okienku Akcje  
 Aby wyświetlić w okienku Akcje, Dodaj kontrolkę użytkownika, aby <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwość `ThisDocument.ActionsPane` pola (Word) lub `ThisWorkbook.ActionsPane` pola (Excel).  
  
### <a name="to-add-the-user-control-to-the-actions-pane"></a>Aby dodać kontrolkę użytkownika w okienku Akcje  
  
1.  Dodaj następujący kod do `ThisDocument` lub `ThisWorkbook` klasy jako deklaracji klasy poziomu (nie dodawaj ten kod do metody).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Dodaj następujący kod do `ThisDocument_Startup` obsługi zdarzeń `ThisDocument` klasy lub `ThisWorkbook_Startup` obsługi zdarzeń `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>Zobacz także  
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Wskazówki: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Porady: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Wskazówki: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  