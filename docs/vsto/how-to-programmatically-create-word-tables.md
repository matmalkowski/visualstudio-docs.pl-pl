---
title: 'Porady: programowane Tworzenie tabel programu Word | Dokumentacja firmy Microsoft'
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
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
ms.assetid: fe1f9143-9622-45e8-b0a5-511336d99ad1
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0c903ed815e35c3d4f6821d70910ef56611889f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-create-word-tables"></a>Porady: Programowane tworzenie tabel programu Word
  <xref:Microsoft.Office.Interop.Word.Tables> Kolekcji jest elementem członkowskim <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, i <xref:Microsoft.Office.Interop.Word.Range> klasy, które oznacza, że w żadnym z tych kontekstach, można utworzyć tabeli. Możesz użyć <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Tables> kolekcji, aby dodać tabelę w określonym zakresie.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="creating-tables-in-document-level-customizations"></a>Tworzenie tabel w dostosowaniach na poziomie dokumentu  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>Aby dodać prostą tabelę do dokumentu  
  
-   Użyj <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metody w celu dodania tabeli składające się z trzech wierszy i kolumn cztery na początku dokumentu.  
  
     Skorzystaj z następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
 Podczas tworzenia tabeli jest automatycznie dodawany do <xref:Microsoft.Office.Interop.Word.Tables> Kolekcja <xref:Microsoft.Office.Tools.Word.Document> elementu host. Można następnie odwołanie do tabeli za pomocą numeru elementu za pomocą <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości, jak pokazano w poniższym kodzie.  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>Aby odwołać się do tabeli przez towaru  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości i podaj numer tabeli, która ma dotyczyć.  
  
     Skorzystaj z następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
 Każdy <xref:Microsoft.Office.Interop.Word.Table> obiekt ma również <xref:Microsoft.Office.Interop.Word.Table.Range%2A> właściwości, które umożliwia formatowanie ustawić atrybutów.  
  
#### <a name="to-apply-a-style-to-a-table"></a>Aby zastosować styl z tabelą  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Table.Style%2A> właściwości, aby zastosować jedną z wbudowanych stylów programu Word do tabeli.  
  
     Skorzystaj z następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="creating-tables-in-vsto-add-ins"></a>Trwa tworzenie tabel w dodatkach VSTO  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>Aby dodać prostą tabelę do dokumentu  
  
-   Użyj <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metody w celu dodania tabeli składające się z trzech wierszy i kolumn cztery na początku dokumentu.  
  
     Poniższy przykładowy kod dodaje tabeli do aktywnego dokumentu. Aby użyć tego przykładu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
 Podczas tworzenia tabeli jest automatycznie dodawany do <xref:Microsoft.Office.Interop.Word.Tables> kolekcji <xref:Microsoft.Office.Interop.Word.Document>. Można następnie odwołanie do tabeli za pomocą numeru elementu za pomocą <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości, jak pokazano w poniższym kodzie.  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>Aby odwołać się do tabeli przez towaru  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> właściwości i podaj numer tabeli, która ma dotyczyć.  
  
     Poniższy przykład kodu wykorzystuje aktywny dokument. Aby użyć tego przykładu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
 Każdy <xref:Microsoft.Office.Interop.Word.Table> obiekt ma również <xref:Microsoft.Office.Interop.Word.Table.Range%2A> właściwości, które umożliwia formatowanie ustawić atrybutów.  
  
#### <a name="to-apply-a-style-to-a-table"></a>Aby zastosować styl z tabelą  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Table.Style%2A> właściwości, aby zastosować jedną z wbudowanych stylów programu Word do tabeli.  
  
     Poniższy przykład kodu wykorzystuje aktywny dokument. Aby użyć tego przykładu, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane Dodawanie tekstu i formatowania do komórek w tabelach programu Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Porady: programowane Dodawanie wierszy i kolumn do tabel Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Porady: programowane Wypełnianie tabel programu Word właściwościami dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  