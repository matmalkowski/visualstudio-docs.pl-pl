---
title: 'Porady: Zarządzanie układem formantu w okienkach akcji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0831740c612e4e9d4eddd47a0648302e9460f060
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Porady: zarządzanie układem formantu w okienkach akcji
  W okienku Akcje jest zadokowane po prawej stronie dokumentu lub arkusz domyślnie; jednak może być zadokowany do lewej, top lub bottom. Jeśli używasz wielu formantów użytkownika można napisać kod poprawnie stosu kontrolek użytkownika w okienku Akcje. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Kolejność stosu formantów zależy od tego, czy w okienku Akcje jest zadokowany w pionie lub poziomie.  
  
> [!NOTE]  
>  Jeśli użytkownik zmieni rozmiar okienka akcji w czasie wykonywania, można ustawić służy do zmiany rozmiaru w okienku Akcje. Można użyć <xref:System.Windows.Forms.Control.Anchor%2A> właściwości formantu formularzy systemu Windows z formantami zakotwiczenia w okienku Akcje. Aby uzyskać więcej informacji, zobacz [porady: zakotwiczenie formantów na formularzach systemu Windows](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Aby ustawić kolejność stosu kontrolek okienku akcji  
  
1.  Otwórz projekt poziomie dokumentu dla programu Microsoft Office Word obejmuje okienek akcji z wieloma kontrolki użytkownika lub formantów w okienku Akcje zagnieżdżonych. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  Kliknij prawym przyciskiem myszy **ThisDocument.cs** lub **ThisDocument.vb** w **Eksploratora rozwiązań** , a następnie kliknij przycisk **kod widoku**.  
  
3.  W <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> obsługi zdarzeń w okienku Akcje, sprawdź, czy jest poziomy orientację w okienku Akcje.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  W przypadku orientacji poziomej stosu kontrolek okienku akcji z lewej strony; w przeciwnym razie stosu je od góry.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  W języku C#, należy dodać program obsługi zdarzeń dla `ActionsPane` do <xref:Microsoft.Office.Tools.Word.Document.Startup> obsługi zdarzeń. Aby uzyskać informacje dotyczące tworzenia procedury obsługi zdarzeń, zobacz [porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  Uruchom projekt i sprawdź, czy formanty w okienku Akcje stos od lewej do prawej gdy jest zadokowany w okienku Akcje, w górnej części dokumentu i formanty są skumulowany od góry do dołu, gdy jest zadokowany w okienku Akcje, po prawej stronie dokumentu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Określa projekt poziomie dokumentu programu Word z okienek akcji, który zawiera wiele formantów użytkownika lub w okienku Akcje zagnieżdżonych.  
  
## <a name="see-also"></a>Zobacz też  
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Wskazówki: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Przewodnik: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  