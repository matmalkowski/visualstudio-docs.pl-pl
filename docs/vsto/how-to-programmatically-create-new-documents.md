---
title: 'Porady: programowane tworzenie nowych dokumentów'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 964bcfe9d582d51794ec3f9469686df029c7cab1
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257436"
---
# <a name="how-to-programmatically-create-new-documents"></a>Porady: programowane tworzenie nowych dokumentów
  Po utworzeniu dokumentu programowo, nowy dokument jest natywny <xref:Microsoft.Office.Interop.Word.Document> obiektu. Ten obiekt nie ma dodatkowych zdarzeń i możliwości wiązania danych <xref:Microsoft.Office.Tools.Word.Document> element hosta. Aby uzyskać więcej informacji, zobacz [ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Podczas opracowywania projektu poziomie dokumentu nie można dodać programistycznie <xref:Microsoft.Office.Tools.Word.Document> hosta elementy do projektu. W projekcie dodatku narzędzi VSTO można przekonwertować żadnego <xref:Microsoft.Office.Interop.Word.Document> do obiektu <xref:Microsoft.Office.Tools.Word.Document> element hosta w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [dokumentów rozszerzania programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Aby utworzyć nowy dokument na podstawie szablonu normalnej  
  
-   Użyj <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Documents> kolekcję, aby utworzyć nowy dokument oparty na szablonie normalnego. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]  
  
## <a name="use-custom-templates"></a>Użyj szablonów niestandardowych  
 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Metoda ma opcjonalny *szablonu* argumentu, aby utworzyć nowy dokument na podstawie szablonu innego niż szablon Normal. Należy podać nazwę pliku i w pełni kwalifikowana szablonu.  
  
### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Aby utworzyć nowy dokument na podstawie szablonu niestandardowego  
  
-   Wywołanie <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Documents> kolekcji i określ ścieżkę do szablonu. Aby użyć w tym przykładzie kodu, uruchom go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  