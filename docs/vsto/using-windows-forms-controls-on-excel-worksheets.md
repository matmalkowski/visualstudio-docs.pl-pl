---
title: Formanty formularzy systemu Windows w arkuszach programu Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fd367087f48ababb390ddd87e289ec22258b4921
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767926"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Formanty formularzy systemu Windows w arkuszach programu Excel
  Formanty formularzy systemu Windows można dodać do skoroszytów programu Microsoft Office Excel w taki sam sposób jak dodawanie formantów do formularzy systemu Windows. Aby uzyskać ogólne informacje na temat pracy z kontroli nad dokumentami, zobacz [formanty formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Zagadnienia dotyczące kontroli dla programu Excel  
 Istnieje kilka kwestii, które są specyficzne dla programu Excel.  
  
### <a name="match-control-size-to-cell-size"></a>Rozmiar formantu dopasowania do rozmiaru komórek  
 Można ustawić formant zmieniany automatycznie po zmianie rozmiaru komórki nadrzędnej. Aby uzyskać więcej informacji, zobacz [porady: zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>Dodaj składniki, które są współużytkowane przez wszystkie arkusze  
 Można dodać składniki, które chcesz udostępnić wśród wszystkich arkuszy, takich jak <xref:System.Data.DataSet>, do projektanta skoroszytu, zamiast do arkuszy. Składnik będą wyświetlane na pasku składnika.  
  
### <a name="formula-for-embedding-controls"></a>Formuła osadzania formantów  
 Po wybraniu formantu w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest i nie należy go usunąć.  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Porady: ukrywanie formantów w arkuszu podczas drukowania](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Wskazówki: Zmiana formatowania arkusza za pomocą formantów CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Wskazówki: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Wskazówki: Aktualizacja wykresu w arkuszu za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  