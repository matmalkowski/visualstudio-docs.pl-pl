---
title: "Porady: Dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO | Dokumentacja firmy Microsoft"
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
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
ms.assetid: 872d2beb-193b-49f9-9a7b-dcebab91a73b
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4f7c88ca0ef06ea74f6963166a2b6f421058c0da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Porady: dodawanie niestandardowych części XML do dokumentów za pomocą dodatków narzędzi VSTO
  Dane XML można przechowywać w następujących typów dokumentów, tworząc z niestandardowym elementem XML w dodatku VSTO:  
  
-   Skoroszyt programu Microsoft Office Excel.  
  
-   Dokument programu Microsoft Office Word.  
  
-   Prezentacji programu Microsoft Office PowerPoint.  
  
 Aby uzyskać więcej informacji, zobacz [przegląd części XML niestandardowe](../vsto/custom-xml-parts-overview.md).  
  
 **Dotyczy:** informacje w tym temacie dotyczą projektów na poziomie aplikacji dla programu Excel, PowerPoint i Word. Aby uzyskać więcej informacji, zobacz [dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Aby dodać do skoroszytu programu Excel z niestandardowym elementem XML  
  
1.  Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> do obiektu <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> kolekcji w skoroszycie. <xref:Microsoft.Office.Core.CustomXMLPart> Zawiera ciąg XML, który ma być przechowywany w skoroszycie.  
  
     Poniższy przykładowy kod dodaje z niestandardowym elementem XML do określonego skoroszytu.  
  
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]  
  
2.  Dodaj `AddCustomXmlPartToWorkbook` metody `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Excel.  
  
3.  Wywoływanie metody z innego kodu w projekcie. Na przykład, aby utworzyć niestandardowym elementem XML, gdy użytkownik otwiera skoroszyt, wywołaj metodę z obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> zdarzeń.  
  
### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Aby dodać do dokumentu programu Word z niestandardowym elementem XML  
  
1.  Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> do obiektu <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> kolekcji w dokumencie. <xref:Microsoft.Office.Core.CustomXMLPart> Zawiera ciąg XML, który ma być przechowywany w dokumencie.  
  
     Poniższy przykładowy kod dodaje z niestandardowym elementem XML do określonego dokumentu.  
  
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]  
  
2.  Dodaj `AddCustomXmlPartToDocument` metody `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Word.  
  
3.  Wywoływanie metody z innego kodu w projekcie. Na przykład, aby utworzyć niestandardowym elementem XML, gdy użytkownik otwiera dokument, wywołaj metodę z obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzeń.  
  
### <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Aby dodać niestandardowe części XML do prezentacji programu PowerPoint  
  
1.  Dodaj nową <xref:Microsoft.Office.Core.CustomXMLPart> do obiektu <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> kolekcji w prezentacji. <xref:Microsoft.Office.Core.CustomXMLPart> Zawiera ciąg XML, który ma być przechowywany w prezentacji.  
  
     Poniższy przykładowy kod dodaje z niestandardowym elementem XML do określonej prezentacji.  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]  
  
2.  Dodaj `AddCustomXmlPartToPresentation` metody `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu PowerPoint.  
  
3.  Wywoływanie metody z innego kodu w projekcie. Na przykład, aby utworzyć niestandardowym elementem XML, gdy użytkownik otwiera prezentacji, wywołaj metodę z obsługi zdarzeń dla <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen> zdarzeń.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Dla uproszczenia w tym przykładzie użyto ciągu XML, który jest zdefiniowany jako zmienną lokalną w metodzie. Zazwyczaj należy uzyskać XML ze źródła zewnętrznego, takiego jak plik lub bazy danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd części niestandardowy plik XML](../vsto/custom-xml-parts-overview.md)   
 [Instrukcje: Dodawanie niestandardowych części XML do dostosowywania na poziomie dokumentów](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  