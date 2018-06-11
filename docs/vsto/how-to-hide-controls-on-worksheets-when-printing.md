---
title: 'Porady: ukrywanie formantów w arkuszu podczas drukowania'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: e240f4b4be5ce4092705615f060f4e0ef0076e3a
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254481"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Porady: ukrywanie formantów w arkuszu podczas drukowania
  Po wydrukowaniu dokumentu programu Microsoft Office Excel, który zawiera formanty formularzy systemu Windows kontrolki są widoczne w arkuszu wydruku. Można ukryć formantów podczas drukowania arkusza.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Jeżeli ukrywanie formantów wyświetlających dane, takie jak <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, danych w formancie nie będą widoczne w arkuszu wydruku.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Ukrywanie formantów podczas arkusz jest drukowany  
  
1.  Utwórz lub Otwórz projekt programu Excel w programie Visual Studio i sprawdź, czy **Sheet1 —** jest widoczne w projektancie. Informacji o tworzeniu projektów, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Z **formanty standardowe** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Excel.Controls.Button> kontrolować w komórce na `Sheet1`.  
  
3.  W **właściwości** ustaw <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> właściwości **False**.  
  
## <a name="see-also"></a>Zobacz także  
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Formanty formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Porady: dodawanie formantów formularzy systemu Windows do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Porady: zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  