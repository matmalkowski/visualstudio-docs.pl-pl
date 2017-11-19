---
title: "Porady: Odczyt z oraz zapisywanie właściwości dokumentów | Dokumentacja firmy Microsoft"
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
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
ms.assetid: e9ef9fa3-36b9-48fb-8148-f5152463c03c
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca687f9482d65621ad848c2ca6459c6fe782f8ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Porady: odczytywanie i zapisywanie właściwości dokumentów
  Możesz zapisać dokument, właściwości wraz z dokumentu. Aplikacje pakietu Office zapewniają wiele wbudowanych właściwości, takie jak autor, tytuł i temat. W tym temacie przedstawiono sposób ustawiania właściwości dokumentu w programie Microsoft Office Excel i Microsoft Office Word.  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: dostępu i modyfikowania właściwości dokumentu niestandardowe w programie Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## <a name="setting-document-properties-in-excel"></a>Ustawienie właściwości dokumentu w programie Excel  
 Aby pracować z wbudowanych właściwości w programie Excel, należy użyć następujących właściwości:  
  
-   W projekcie poziomie dokumentu za pomocą <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> właściwość `ThisWorkbook` klasy.  
  
-   W projekcie dodatku narzędzi VSTO użyj <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> właściwość <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu.  
  
 Te właściwości zwracają <xref:Microsoft.Office.Core.DocumentProperties> obiektu, który jest kolekcją z <xref:Microsoft.Office.Core.DocumentProperty> obiektów. Można użyć `Item` właściwość kolekcji można pobrać określonej właściwości, według nazwy lub indeks w kolekcji.  
  
 Poniższy przykład kodu pokazuje, jak zmienić wbudowanej **numer poprawki** właściwości w projektach na poziomie dokumentu.  
  
#### <a name="to-change-the-revision-number-property-in-excel"></a>Aby zmienić właściwość numer wersji w programie Excel  
  
1.  Właściwości dokumentu wbudowanych można przypisać do zmiennej.  
  
     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]  
  
2.  Przyrost `Revision Number` właściwości o jeden.  
  
     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]  
  
## <a name="setting-document-properties-in-word"></a>Ustawienie właściwości dokumentu programu Word  
 Aby pracować z wbudowanych właściwości w programie Word, należy użyć następujących właściwości:  
  
-   W projekcie poziomie dokumentu za pomocą <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> właściwość `ThisDocument` klasy.  
  
-   W projekcie dodatku narzędzi VSTO użyj <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> właściwość <xref:Microsoft.Office.Interop.Word.Document> obiektu.  
  
 Te właściwości zwracają <xref:Microsoft.Office.Core.DocumentProperties> obiektu, który jest kolekcją z <xref:Microsoft.Office.Core.DocumentProperty> obiektów. Można użyć `Item` właściwość kolekcji można pobrać określonej właściwości, według nazwy lub indeks w kolekcji.  
  
 Poniższy przykład kodu pokazuje, jak zmienić wbudowanej **podmiotu** właściwości w projektach na poziomie dokumentu.  
  
#### <a name="to-change-the-subject-property"></a>Aby zmienić właściwość podmiotu  
  
1.  Właściwości dokumentu wbudowanych można przypisać do zmiennej.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]  
  
2.  Zmień `Subject` dla właściwości "W dokumencie".  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Przykładów założono, że kod zostały zapisane `ThisWorkbook` klasy w projektach na poziomie dokumentu dla programu Excel, a `ThisDocument` klasy w projektach na poziomie dokumentu dla programu Word.  
  
 Mimo że korzystasz z programu Word i Excel i ich obiektami, Microsoft Office udostępnia listę właściwości dostępne wbudowane dokumentu. Próba uzyskania dostępu do niezdefiniowanej właściwości zgłasza wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programowania dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Porady: tworzenie i modyfikowanie właściwości niestandardowego dokumentu](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  