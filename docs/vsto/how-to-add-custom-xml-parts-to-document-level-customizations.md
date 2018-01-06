---
title: "Porady: Dodawanie niestandardowych części XML na poziomie dokumentu | Dokumentacja firmy Microsoft"
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
- document-level customizations [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
ms.assetid: e305a3d6-3a0e-4e72-ab8c-6a87a3590068
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b01646196e0bb755b351c02b4225a60bbfe1ad63
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-custom-xml-parts-to-document-level-customizations"></a>Porady: dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentów
  Dane XML można przechowywać w skoroszycie programu Microsoft Office Excel lub dokumentu programu Microsoft Office Word, tworząc z niestandardowym elementem XML w dostosowaniu poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [przegląd części XML niestandardowe](../vsto/custom-xml-parts-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Program Visual Studio nie ma projektów na poziomie dokumentu dla programu Microsoft Office PowerPoint. Aby dowiedzieć się, jak dodawanie niestandardowych części XML do prezentacji programu PowerPoint przy użyciu dodatku VSTO, zobacz [porady: Dodawanie niestandardowych części XML do dokumentów za pomocą VSTO Add-Ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Aby dodać do skoroszytu programu Excel z niestandardowym elementem XML  
  
1.  Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> do obiektu <xref:Microsoft.Office.Core.CustomXMLParts> kolekcji w skoroszycie. <xref:Microsoft.Office.Core.CustomXMLPart> Zawiera ciąg XML, który ma być przechowywany w skoroszycie.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]  
  
2.  Dodaj `AddCustomXmlPartToWorkbook` metody `ThisWorkbook` klasy w projektach na poziomie dokumentu dla programu Excel.  
  
3.  Wywoływanie metody z innego kodu w projekcie. Na przykład, aby utworzyć niestandardowym elementem XML, gdy użytkownik otwiera skoroszyt, należy wywołać metodę z `ThisWorkbook_Startup` obsługi zdarzeń.  
  
### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Aby dodać do dokumentu programu Word z niestandardowym elementem XML  
  
1.  Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> do obiektu <xref:Microsoft.Office.Core.CustomXMLParts> kolekcji w dokumencie. <xref:Microsoft.Office.Core.CustomXMLPart> Zawiera ciąg XML, który ma być przechowywany w dokumencie.  
  
     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]  
  
2.  Dodaj `AddCustomXmlPartToDocument` metody `ThisDocument` klasy w projektach na poziomie dokumentu dla programu Word.  
  
3.  Wywoływanie metody z innego kodu w projekcie. Na przykład, aby utworzyć niestandardowym elementem XML, gdy użytkownik otwiera dokument, wywołaj metodę z `ThisDocument_Startup` obsługi zdarzeń.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Dla uproszczenia w tym przykładzie użyto ciągu XML, który jest zdefiniowany jako zmienną lokalną w metodzie. Zazwyczaj należy uzyskać XML ze źródła zewnętrznego, takiego jak plik lub bazy danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd części niestandardowy plik XML](../vsto/custom-xml-parts-overview.md)   
 [Instrukcje: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
  