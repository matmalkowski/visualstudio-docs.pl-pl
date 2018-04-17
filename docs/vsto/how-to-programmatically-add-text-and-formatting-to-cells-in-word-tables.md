---
title: 'Porady: programowane Dodawanie tekstu i formatowania do komórek w tabelach Word | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c7d50a5531bdb4e073c2760ae6d4e746b4970af6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Porady: Programowane dodawanie tekstu i formatowania do komórek w tabelach programu Word
  Każda tabela składa się z kolekcji komórek. Każda osoba <xref:Microsoft.Office.Interop.Word.Cell> obiekt reprezentuje jedną komórkę tabeli. To odwołanie do każdej komórki na podstawie jej lokalizacji w tabeli. Ten przykład dotyczy komórki znajdujące się w pierwszym wierszu i pierwsza kolumna tabeli; dodaje tekst do komórki; i stosuje formatowanie.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-add-text-and-formatting-to-cells"></a>Aby dodać tekstu i formatowania do komórek  
  
1.  Odwołanie do komórki na podstawie jej lokalizacji w tabeli, Dodaj tekst do komórki i sformatowany.  
  
     Poniższy przykład kodu może służyć w dostosowaniu poziomie dokumentu. Aby użyć tego przykładu, uruchom go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]  
  
     Poniższy przykład kodu można używać w dodatku VSTO. W tym przykładzie użyto aktywny dokument. Aby użyć w przykładzie, uruchom go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane Tworzenie tabel programu Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Porady: programowane Dodawanie wierszy i kolumn do tabel Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Instrukcje: Programowe wypełnianie tabel programu Word właściwościami dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  