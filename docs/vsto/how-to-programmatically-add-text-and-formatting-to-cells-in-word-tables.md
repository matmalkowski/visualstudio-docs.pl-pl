---
title: "Porady: programowane Dodawanie tekstu i formatowania do komórek w tabelach Word | Dokumentacja firmy Microsoft"
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
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2742215f01065fb90d8a312eaa324e0cecccb57b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
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
  
  