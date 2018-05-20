---
title: 'Porady: Sprawdzanie poprawności danych po dodaniu nowego rzędu do formantu ListObject'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55dc8852952482914bc57a41579163c90672d1db
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Porady: Sprawdzanie poprawności danych po dodaniu nowego rzędu do formantu ListObject
  Użytkownicy mogą dodawać nowe wiersze do <xref:Microsoft.Office.Tools.Excel.ListObject> formant, który jest powiązany z danymi. Przed zatwierdzeniem zmian w źródle danych, można sprawdzić poprawność danych użytkownika.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>Sprawdzanie poprawności danych  
 Zawsze, gdy wiersz jest dodawany do <xref:Microsoft.Office.Tools.Excel.ListObject> który jest powiązany z danymi, <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> zdarzenia. To zdarzenie do weryfikowania danych może obsłużyć. Na przykład jeśli aplikacja wymaga, aby tylko pracownikom między wieku 18 i 65 mogą być dodawane do źródła danych, sprawdź, czy wieku wprowadzona mieści się w zakresie przed dodaniem wiersza.  
  
> [!NOTE]  
>  Należy zawsze sprawdzić danych wejściowych użytkownika na serwerze oprócz klienta. Aby uzyskać więcej informacji, zobacz [Secure aplikacje klienckie](/dotnet/framework/data/adonet/secure-client-applications).  
  
### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Aby sprawdzić poprawność danych, gdy nowy wiersz jest dodawana do ListObject powiązane z danymi  
  
1.  Utwórz zmienne dla Identyfikatora i <xref:System.Data.DataTable> na poziomie klasy.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  Utwórz nową <xref:System.Data.DataTable> i Dodawanie przykładowych kolumn i dane w `Startup` obsługi zdarzeń `Sheet1` klasy (w projektach na poziomie dokumentu) lub `ThisAddIn` klasy (w projekcie dodatku narzędzi VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  Dodaj kod, aby `list1_BeforeAddDataBoundRow` obsługi zdarzeń, aby sprawdzić, czy wprowadzony wiek mieści się w dopuszczalnym zakresem.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 Ten przykład kodu zakłada, że masz istniejącą <xref:Microsoft.Office.Tools.Excel.ListObject> o nazwie `list1` w arkuszu, w której znajduje się ten kod.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject — formant](../vsto/listobject-control.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Porady: kolumn mapy ListObject do danych](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  