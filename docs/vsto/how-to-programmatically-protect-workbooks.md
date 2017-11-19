---
title: "Porady: programowane Włączanie ochrony skoroszytów | Dokumentacja firmy Microsoft"
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
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7dcbedb2c30758c762af0c301c239dd03fe4b10f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-protect-workbooks"></a>Porady: Programowane włączanie ochrony skoroszytów
  Można chronić programu Microsoft Office Excel, dzięki czemu użytkownicy nie Dodawanie lub usuwanie arkuszy i również programowo Wyłącz ochronę skoroszytu. Opcjonalnie można określić hasło, wskazują, czy mają strukturę chronione (tak, aby użytkownicy nie można przenieść arkusze) oraz wskazuje, czy chroniony windows skoroszytu programu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Ochrona skoroszytu nie zatrzymuje użytkowników Edycja komórki. Aby chronić dane, należy chronić arkusze. Aby uzyskać więcej informacji, zobacz [porady: programowane ochrony arkuszy](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 W poniższych przykładach kodu użyć zmiennej zawiera hasło, które są uzyskiwane przez użytkownika.  
  
## <a name="protecting-a-workbook-that-is-part-of-a-document-level-customization"></a>Ochronę skoroszytu, który jest częścią dostosowania poziomie dokumentu  
  
#### <a name="to-protect-a-workbook"></a>Aby chronić skoroszyt  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metody skoroszytu i zawierały hasło. Aby użyć w poniższym przykładzie kodu, uruchom go `ThisWorkbook` klasy, a nie w klasie arkusza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]  
  
#### <a name="to-unprotect-a-workbook"></a>Aby wyłączyć ochronę skoroszytu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> metody przekazywanie hasła, jeśli jest to wymagane. Aby użyć w poniższym przykładzie kodu, uruchom go `ThisWorkbook` klasy, a nie w klasie arkusza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]  
  
## <a name="protecting-a-workbook-by-using-an-application-level-add-in"></a>Ochrona skoroszytu przy użyciu dodatku poziomie aplikacji  
  
#### <a name="to-protect-a-workbook"></a>Aby chronić skoroszyt  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> metody skoroszytu i zawierały hasło. W tym przykładzie kodu używane aktywnym skoroszycie. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]  
  
#### <a name="to-unprotect-a-workbook"></a>Aby wyłączyć ochronę skoroszytu  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> metody aktywnym skoroszycie przekazywanie hasła, jeśli jest to wymagane. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca ze skoroszytami](../vsto/working-with-workbooks.md)   
 [Porady: programowane Włączanie ochrony arkuszy](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Porady: programowane ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  