---
title: 'Porady: tworzenie i modyfikowanie właściwości niestandardowego dokumentu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb66d2fbd1af41cfa89fc38f7694ee3783d10f76
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254439"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Porady: tworzenie i modyfikowanie właściwości niestandardowego dokumentu
  Aplikacje Microsoft Office wymienionych powyżej Podaj wbudowanych właściwości, które są przechowywane z dokumentami. Ponadto można tworzyć i modyfikować niestandardowe właściwości dokumentu, jeśli ma dodatkowych informacji, które mają być przechowywane w dokumencie.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Użyj właściwości CustomDocumentProperties dokumentu do pracy z właściwości niestandardowych. Na przykład w projekcie poziomie dokumentu dla programu Microsoft Office Excel, należy użyć <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> właściwość `ThisWorkbook` klasy. W projekcie dodatku narzędzi VSTO dla programu Excel, użyj <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> właściwość <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu. Te właściwości zwracają <xref:Microsoft.Office.Core.DocumentProperties> obiektu, który jest kolekcją z <xref:Microsoft.Office.Core.DocumentProperty> obiektów. Można użyć `Item` właściwość kolekcji można pobrać określonej właściwości, według nazwy lub indeks w kolekcji.  
  
 W poniższym przykładzie pokazano, jak dodać niestandardowe właściwości w dostosowaniu poziomie dokumentu dla programu Excel i przypisz jej wartość.  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak I: dostępu i manipulowania niestandardowe właściwości dokumentu w programie Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Przykład  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Próby dostępu `Value` właściwość niezdefiniowanymi właściwościami zgłasza wyjątek.  
  
## <a name="see-also"></a>Zobacz także  
 [Program dodatków VSTO](../vsto/programming-vsto-add-ins.md)   
 [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)   
 [Porady: Odczyt z i zapisu do właściwości dokumentu](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  