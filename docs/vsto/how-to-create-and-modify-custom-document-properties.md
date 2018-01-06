---
title: "Porady: tworzenie i modyfikowanie właściwości niestandardowego dokumentu | Dokumentacja firmy Microsoft"
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
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
ms.assetid: 99d9dfaf-891f-4f3b-a580-67362afdaf34
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1ab68f9bd5c6a6bc1176fc211b99ad1de777ca38
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Porady: tworzenie i modyfikowanie właściwości niestandardowego dokumentu.
  Aplikacje Microsoft Office wymienionych powyżej Podaj wbudowanych właściwości, które są przechowywane z dokumentami. Ponadto można tworzyć i modyfikować niestandardowe właściwości dokumentu, jeśli ma dodatkowych informacji, które mają być przechowywane w dokumencie.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Użyj właściwości CustomDocumentProperties dokumentu do pracy z właściwości niestandardowych. Na przykład w projekcie poziomie dokumentu dla programu Microsoft Office Excel, należy użyć <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> właściwość `ThisWorkbook` klasy. W projekcie dodatku narzędzi VSTO dla programu Excel, użyj <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> właściwość <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu. Te właściwości zwracają <xref:Microsoft.Office.Core.DocumentProperties> obiektu, który jest kolekcją z <xref:Microsoft.Office.Core.DocumentProperty> obiektów. Można użyć `Item` właściwość kolekcji można pobrać określonej właściwości, według nazwy lub indeks w kolekcji.  
  
 W poniższym przykładzie pokazano, jak dodać niestandardowe właściwości w dostosowaniu poziomie dokumentu dla programu Excel i przypisz jej wartość.  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak czy I: dostępu i modyfikowania właściwości dokumentu niestandardowe w programie Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Przykład  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Próby dostępu `Value` właściwość niezdefiniowanymi właściwościami zgłasza wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programowania dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Instrukcje: Odczytywanie i zapisywanie właściwości dokumentów](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  