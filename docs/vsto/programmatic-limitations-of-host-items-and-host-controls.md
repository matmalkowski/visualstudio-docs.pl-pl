---
title: Ograniczenia programowe elementów hosta i formantów hosta
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0b7e45ed9ba8e9fcd42d57a1cc6aaf34ce3e3711
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693386"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Ograniczenia programowe elementów hosta i formantów hosta
  Każdy z elementów hosta i kontroli hosta jest przeznaczona do przypominają odpowiedniego natywnego programu Microsoft Office Word lub obiektu programu Microsoft Office Excel o dodatkowe funkcje. Istnieją pewne podstawowe różnice między zachowanie elementów hosta i formantów hosta i natywnego obiektów pakietu Office w czasie wykonywania.  
  
 Aby uzyskać ogólne informacje na temat elementów hosta i formantów hosta, zobacz [elementów, a informacje o formantach](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="programmatically-create-host-items"></a>Programowe tworzenie obiekty hosta  
 Gdy programowo utworzyć lub otworzyć dokument, skoroszytu lub arkusza w czasie wykonywania za pomocą modelu obiektów programu Word czy Excel, element nie jest elementem hosta. Zamiast tego nowy obiekt jest obiektem natywnego pakietu Office. Na przykład, jeśli używasz <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metodę, aby utworzyć nowy dokument programu Word w czasie wykonywania, będzie on natywny <xref:Microsoft.Office.Interop.Word.Document> obiektu zamiast <xref:Microsoft.Office.Tools.Word.Document> element hosta. Podobnie po utworzeniu nowego arkusza w czasie wykonywania za pomocą <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody, zostanie wyświetlony natywny <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu zamiast <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta.  
  
 W projektach na poziomie dokumentu nie można utworzyć elementów hosta w czasie wykonywania. Obiekty hosta mogą być tworzone tylko w czasie projektowania w projektach na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [element hosta dokumentu](../vsto/document-host-item.md), [element hosta skoroszytu](../vsto/workbook-host-item.md), i [element hosta arkusza](../vsto/worksheet-host-item.md).  
  
 W dodatku VSTO projektów, można utworzyć <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, lub <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementów w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [dokumentów rozszerzania programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="programmatically-create-host-controls"></a>Programowe tworzenie kontrolki hosta  
 Można programowo Dodaj formanty hosta do <xref:Microsoft.Office.Tools.Word.Document> lub <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Formanty hosta nie można dodać do natywny <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Interop.Excel.Worksheet>.  
  
> [!NOTE]  
>  Następujące formanty hosta nie można dodać programistycznie do arkuszy lub dokumentów: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>, i <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Opis typu różnic między elementami hosta, kontrolki hosta i natywnego obiektów pakietu Office  
 Dla każdego elementu hosta i kontroli hosta ma podstawowego natywnego obiektu Microsoft Office Word i Microsoft Office Excel. Obiekt źródłowy mogą korzystać za pomocą właściwości InnerObject element hosta lub host formantu. Istnieje jednak nie można rzutować natywnego obiektu Office do odpowiedniego elementu hosta lub kontroli hosta. Jeśli spróbujesz można rzutować obiektu macierzystego pakietu Office na typ elementu hosta lub kontroli hosta <xref:System.InvalidCastException> jest generowany.  
  
 Istnieje kilka scenariuszy, w którym różnice między typami elementów hosta i formantów hosta i natywnego obiektów pakietu Office może mieć wpływ na kod.  
  
### <a name="pass-host-controls-to-methods-and-properties"></a>Przekaż do metody i właściwości kontrolki hosta  
 W programie Word kontroli hosta nie można przekazać do metody lub właściwości, która wymaga natywnego obiektu Word jako parametr. Należy użyć właściwości InnerObject formantu hosta do zwrócenia obiekt natywny programu Word. Na przykład można przekazać <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu do metody, przekazując <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> właściwość <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do metody hosta.  
  
 W programie Excel możesz korzystać z właściwością InnerObject kontroli hosta do przekazania kontroli hosta do metody lub właściwości, gdy ta metoda lub właściwość oczekuje obiektu źródłowego programu Excel.  
  
 Poniższy przykład tworzy <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli i przekazuje je do <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metody. W kodzie użyto <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> właściwości nazwanego zakresu, aby przywrócić źródłowy urząd <xref:Microsoft.Office.Interop.Excel.Range> , co jest wymagane przez <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metody.  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]  
  
### <a name="return-types-of-native-office-methods-and-properties"></a>Zwracane typy właściwości i metod natywnych pakietu Office  
 Większość metod i właściwości elementów hosta zwraca natywnego Office obiektu źródłowego podstawie element hosta. Na przykład <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> właściwość <xref:Microsoft.Office.Tools.Excel.NamedRange> hosta sterowania w programie Excel zwraca <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu zamiast <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta. Podobnie <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> właściwość <xref:Microsoft.Office.Tools.Word.RichTextContentControl> hosta sterowania w programie Word zwraca <xref:Microsoft.Office.Interop.Word.Document> obiektu zamiast <xref:Microsoft.Office.Tools.Word.Document> element hosta.  
  
### <a name="access-collections-of-host-controls"></a>Dostęp do kolekcji formantów hosta  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Nie zapewnia poszczególnych kolekcji dla każdego typu kontroli hosta. Zamiast tego użyj właściwości Controls elementu hosta do iteracji wszystkie zarządzane formanty (kontrolki hosta i formantów formularzy systemu Windows) w dokumencie lub arkusz, a następnie sprawdź dla elementów zgodnych z typem formantu hosta, który chcesz. Poniższy przykład kodu sprawdza każdego formantu w dokumencie programu Word i określa, czy formant jest <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]  
  
 Aby uzyskać więcej informacji dotyczących właściwości formantów elementów hosta, zobacz [dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Modele obiektów programu Word i Excel zawierają właściwości, które udostępniają kolekcje natywnego kontroli nad dokumentami i arkuszy. Nie można uzyskać dostępu zarządzane formanty, używając tych właściwości. Na przykład nie jest możliwe wyliczenie każdego <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki w dokumencie hosta za pomocą <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> właściwość <xref:Microsoft.Office.Interop.Word.Document> lub <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> właściwość <xref:Microsoft.Office.Tools.Word.Document>. Te właściwości obejmują tylko <xref:Microsoft.Office.Interop.Word.Bookmark> formantów w dokumencie; nie zawierają <xref:Microsoft.Office.Tools.Word.Bookmark> hostowania formantów w dokumencie.  
  
## <a name="see-also"></a>Zobacz także  
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Element hosta arkusza](../vsto/worksheet-host-item.md)   
 [Element hosta skoroszytu](../vsto/workbook-host-item.md)   
 [Element hosta dokumentu](../vsto/document-host-item.md)  
  
  