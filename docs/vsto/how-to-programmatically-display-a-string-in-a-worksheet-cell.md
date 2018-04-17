---
title: 'Porady: programowane wyświetlanie ciągu w komórce arkusza | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 29dafd7a3eace9350bdb045b2aee0d90a92a445c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Porady: Programowane wyświetlanie ciągu w komórce arkusza
  W tym przykładzie przedstawiono sposób wyświetlania tekstu w komórce programowo. Do wyświetlania tekstu w komórce, użyj <xref:Microsoft.Office.Tools.Excel.NamedRange> formant lub obiekt zakresu natywnego programu Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Używanie formantu NamedRange  
 W tym przykładzie użyto <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `message`. Kontrolka musi zostać dodana do dostosowania na poziomie dokumentu, w czasie projektowania. Poniższy kod muszą znajdować się w klasie arkusza nie znajduje się w `ThisWorkbook` klasy.  
  
#### <a name="to-display-text-in-a-namedrange-control"></a>Do wyświetlania tekstu w namedrange — formant  
  
1.  Ustaw wartość <xref:Microsoft.Office.Tools.Excel.NamedRange> formant **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="using-a-native-excel-range"></a>Za pomocą natywnego zakresu programu Excel  
 Poniższy kod tworzy nowy zakres programowo i następnie przypisuje wartość do niego.  
  
#### <a name="to-display-text-in-an-excel-range"></a>Do wyświetlania tekstu w zakresie programu Excel  
  
1.  Pobieranie zakresu w komórce **A1** na `Sheet1` i ustaw wartość **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Zbieranie danych za pomocą formularza systemu Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Rozwiązywanie problemów z rozwiązań pakietu Office](../vsto/troubleshooting-office-solutions.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  