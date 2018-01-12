---
title: 'Porady: programowane wyszukiwanie tekstu w zakresach arkusza | Dokumentacja firmy Microsoft'
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
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 42c95ab26437ad590d457ad926db6e070a7c8de0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Porady: Programowane wyszukiwanie tekstu w zakresach arkusza
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> Metody <xref:Microsoft.Office.Interop.Excel.Range> obiektu umożliwia wyszukiwanie tekstu w zakresie. Ten tekst również może być ciągów błędów, które mogą być wyświetlane w komórce arkusza takich jak `#NULL!` lub `#VALUE!`. Aby uzyskać więcej informacji na temat ciągów błąd, zobacz [wartości błędów komórki](http://msdn.microsoft.com/library/office/ff839168.aspx).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Poniższy przykład wyszukuje zakres o nazwie `Fruits` i modyfikuje czcionkę dla komórki zawierające słowo "jabłek". Ta procedura używa również <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metodę, która używa uprzednio ustawione ustawienia powtórzeń wyszukiwania wyszukiwania. Określ komórki, po upływie którego do wyszukiwania i <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metoda obsługuje pozostałe.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Metody wyszukiwania opakowuje powrót do początku zakresu wyszukiwania po osiągnięciu końca zakresu. Kodu musi zapewnić, że wyszukiwanie otacza w pętli nieskończonej. Przykładowa procedura przedstawia sposób rozwiązać przy użyciu <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> właściwości.  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak I: Użyj metody Znajdź w dodatku Excel?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### <a name="to-search-for-text-in-a-worksheet-range"></a>Aby wyszukać tekst w zakresie arkusza  
  
1.  Zadeklaruj zmienne dla śledzenia całego zakresu, pierwszy znaleziony zakres i znaleziono bieżącego zakresu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2.  Wyszukiwanie pierwszego dopasowania określenia wszystkich parametrów, z wyjątkiem komórki do wyszukiwania po.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3.  Kontynuować wyszukiwanie, tak długo, jak długo są zgodne.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4.  Porównanie pierwszego zakresu znaleziono (`firstFind`) do **nic**. Jeśli `firstFind` nie zawiera wartości, magazynów kodu optymalizacji znaleziono zakresu (`currentFind`).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5.  Zamknij pętli, jeśli adres zakresu znaleziono zgodny z adresem pierwszy znaleziony zakresu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6.  Ustaw efekt znaleziono zakresu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7.  Wykonaj wyszukiwanie w innym.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
 W poniższym przykładzie przedstawiono metody ukończenia.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z zakresami](../vsto/working-with-ranges.md)   
 [Porady: programowane stosowanie stylów do zakresów arkusza w skoroszycie](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Porady: programowane odwoływanie do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  