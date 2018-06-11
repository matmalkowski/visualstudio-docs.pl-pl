---
title: 'Porady: programowane Tworzenie tabel programu Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a44c87a796a5f4d9add4dad122933fbbbd2fe13c
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257842"
---
# <a name="how-to-programmatically-create-word-tables"></a>Porady: programowane Tworzenie tabel programu Word
  <xref:Microsoft.Office.Interop.Word.Tables> Kolekcji jest elementem członkowskim <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, i <xref:Microsoft.Office.Interop.Word.Range> klasy, które oznacza, że w żadnym z tych kontekstach, można utworzyć tabeli. Możesz użyć <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Tables> kolekcji, aby dodać tabelę w określonym zakresie.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="create-tables-in-document-level-customizations"></a>Tworzenie tabel w dostosowaniach na poziomie dokumentu  
  
### <a name="to-add-a-simple-table-to-a-document"></a>Aby dodać prostą tabelę do dokumentu  
  
-   Użyj <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metody w celu dodania tabeli składające się z trzech wierszy i kolumn cztery na początku dokumentu.  
  
     Skorzystaj z następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
 Podczas tworzenia tabeli jest automatycznie dodawany do <xref:Microsoft.Office.Interop.Word.Tables> Kolekcja <xref:Microsoft.Office.Tools.Word.Document> elementu host. Można następnie odwołanie do tabeli za pomocą numeru elementu za pomocą <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości, jak pokazano w poniższym kodzie.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>Aby odwołać się do tabeli przez towaru  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości i podaj numer tabeli, która ma dotyczyć.  
  
     Skorzystaj z następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
 Każdy <xref:Microsoft.Office.Interop.Word.Table> obiekt ma również <xref:Microsoft.Office.Interop.Word.Table.Range%2A> właściwości, które umożliwia formatowanie ustawić atrybutów.  
  
### <a name="to-apply-a-style-to-a-table"></a>Aby zastosować styl z tabelą  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Table.Style%2A> właściwości, aby zastosować jedną z wbudowanych stylów programu Word do tabeli.  
  
     Skorzystaj z następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="create-tables-in-vsto-add-ins"></a>Tworzenie tabel w dodatkach VSTO  
  
### <a name="to-add-a-simple-table-to-a-document"></a>Aby dodać prostą tabelę do dokumentu  
  
-   Użyj <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metody w celu dodania tabeli składające się z trzech wierszy i kolumn cztery na początku dokumentu.  
  
     Poniższy przykładowy kod dodaje tabeli do aktywnego dokumentu. Aby użyć tego przykładu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
 Podczas tworzenia tabeli jest automatycznie dodawany do <xref:Microsoft.Office.Interop.Word.Tables> kolekcji <xref:Microsoft.Office.Interop.Word.Document>. Można następnie odwołanie do tabeli za pomocą numeru elementu za pomocą <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości, jak pokazano w poniższym kodzie.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>Aby odwołać się do tabeli przez towaru  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości i podaj numer tabeli, która ma dotyczyć.  
  
     Poniższy przykład kodu wykorzystuje aktywny dokument. Aby użyć tego przykładu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
 Każdy <xref:Microsoft.Office.Interop.Word.Table> obiekt ma również <xref:Microsoft.Office.Interop.Word.Table.Range%2A> właściwości, które umożliwia formatowanie ustawić atrybutów.  
  
### <a name="to-apply-a-style-to-a-table"></a>Aby zastosować styl z tabelą  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Table.Style%2A> właściwości, aby zastosować jedną z wbudowanych stylów programu Word do tabeli.  
  
     Poniższy przykład kodu wykorzystuje aktywny dokument. Aby użyć tego przykładu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane Dodawanie tekstu i formatowania do komórek w tabelach programu Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Porady: programowane Dodawanie wierszy i kolumn do tabel Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Porady: programowane Wypełnianie tabel programu Word właściwościami dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  