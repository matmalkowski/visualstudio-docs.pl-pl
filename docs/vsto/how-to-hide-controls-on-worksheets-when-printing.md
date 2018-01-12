---
title: "Porady: ukrywanie formantów w arkuszu podczas drukowania | Dokumentacja firmy Microsoft"
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
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 32a967371cb247139285d5db5d3cf88a2a7cc8f9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Porady: ukrywanie formantów w arkuszu podczas drukowania
  Po wydrukowaniu dokumentu programu Microsoft Office Excel, który zawiera formanty formularzy systemu Windows kontrolki są widoczne w arkuszu wydruku. Można ukryć formantów podczas drukowania arkusza.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Jeżeli ukrywanie formantów wyświetlających dane, takie jak <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, danych w formancie nie będą widoczne w arkuszu wydruku.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Ukrywanie formantów podczas arkusz jest drukowany  
  
1.  Utwórz lub Otwórz projekt programu Excel w programie Visual Studio i sprawdź, czy **Sheet1 —** jest widoczne w projektancie. Informacje o tworzeniu projektów, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Z **formanty standardowe** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Excel.Controls.Button> kontrolować w komórce na `Sheet1`.  
  
3.  W **właściwości** ustaw <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> właściwości **False**.  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Formanty formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Porady: dodawanie formantów do dokumentów pakietu Office formularzy systemu Windows](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Instrukcje: Zmiana rozmiaru kontrolek w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  