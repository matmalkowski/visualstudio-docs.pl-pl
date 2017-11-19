---
title: "Przy użyciu systemu Windows Forms formantów w arkuszu programu Excel | Dokumentacja firmy Microsoft"
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
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bbd9c19698a9c81b5af29d27bba91b8aa36dcd2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="using-windows-forms-controls-on-excel-worksheets"></a>Korzystanie z formantów formularzy Windows w arkuszach Excel
  Formanty formularzy systemu Windows można dodać do skoroszytów programu Microsoft Office Excel w taki sam sposób jak dodawanie formantów do formularzy systemu Windows. Aby uzyskać ogólne informacje na temat pracy z kontroli nad dokumentami, zobacz [formantów formularzy systemu Windows na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="control-considerations-for-excel"></a>Zagadnienia dotyczące kontroli dla programu Excel  
 Istnieje kilka kwestii, które są specyficzne dla programu Excel.  
  
### <a name="matching-control-size-to-cell-size"></a>Dopasowywanie rozmiaru formantu do rozmiaru komórek  
 Można ustawić formant zmieniany automatycznie po zmianie rozmiaru komórki nadrzędnej. Aby uzyskać więcej informacji, zobacz [porady: zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="adding-components-that-are-shared-by-all-worksheets"></a>Dodawanie składników, które są współużytkowane przez wszystkie arkusze  
 Można dodać składniki, które chcesz udostępnić wśród wszystkich arkuszy, takich jak <xref:System.Data.DataSet>, do projektanta skoroszytu, zamiast do arkuszy. Składnik będą wyświetlane na pasku składnika.  
  
### <a name="formula-for-embedding-controls"></a>Formuła osadzania formantów  
 Po wybraniu formantu w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest i nie należy go usunąć.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Porady: ukrywanie formantów w arkuszu podczas drukowania](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Wskazówki: Zmiana formatowania arkusza za pomocą formantów CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Wskazówki: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Wskazówki: Aktualizacja wykresu w arkuszu za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  