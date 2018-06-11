---
title: 'Porady: programowane tworzenie nowych dokumentów programu Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b5b66690d3856a2bf1fc6df417b60ab5e293127
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256747"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Porady: programowane tworzenie nowych dokumentów programu Visio
  Podczas tworzenia nowego rysunku programu Microsoft Office Visio dokumentu, należy dodać go do `Microsoft.Office.Interop.Visio.Documents` kolekcji otwarte dokumenty programu Visio. W rezultacie `Microsoft.Office.Interop.Visio.Documents.Add` metoda tworzy nowy dokument rysunku programu Visio. Aby uzyskać więcej informacji, zobacz dokumentację referencyjną VBA, aby uzyskać [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) metody.  
  
## <a name="create-new-blank-documents"></a>Tworzenie nowych dokumentów puste  
  
### <a name="to-create-a-new-document"></a>Aby utworzyć nowy dokument  
  
-   Użyj `Microsoft.Office.Interop.Visio.Documents.Add` metodę, aby utworzyć nowy pusty dokument, który nie jest oparty na szablonie.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="create-documents-copied-from-existing-documents"></a>Tworzenie dokumentów skopiowane z istniejących dokumentów  
 `Microsoft.Office.Interop.Visio.Documents.Add` Metody można utworzyć nowy dokument, który jest kopią istniejącego dokumentu programu Visio. Należy podać nazwę pliku i w pełni kwalifikowana diagramu.  
  
### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Aby utworzyć nowy dokument, który jest skopiowany z istniejącego dokumentu  
  
-   Wywołanie `Microsoft.Office.Interop.Visio.Documents.Add` metodę i określić ścieżkę diagram programu Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="create-stencils-copied-from-existing-stencils"></a>Utwórz wzorników skopiowane z istniejącego wzorników  
 [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) metody można utworzyć nowy wzornik kopię istniejącego wzornika programu Visio. Należy podać nazwę pliku i w pełni kwalifikowana wzornika.  
  
### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Aby utworzyć nowy wzornik, które zostaną skopiowane z istniejącego wzornika  
  
-   Wywołanie `Microsoft.Office.Interop.Visio.Documents.Add` metodę i określić ścieżkę wzornika.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="create-documents-based-on-existing-templates"></a>Tworzenie dokumentów na podstawie istniejących szablonów  
 `Microsoft.Office.Interop.Visio.Documents.Add` Metody można utworzyć nowego dokumentu ( *VSD* pliku) opartego na podstawie istniejącego szablonu programu Visio ( *.vst* pliku). Ta metoda umożliwia skopiowanie wzorników, style i ustawienia, które są częścią obszaru roboczego szablonu. Należy podać nazwę pliku i w pełni kwalifikowana szablonu.  
  
### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Aby utworzyć nowy dokument, który jest oparty na podstawie istniejącego szablonu  
  
-   Wywołanie `Microsoft.Office.Interop.Visio.Documents.Add` — metoda i podaj ścieżkę pliku szablonu.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compile-the-code"></a>Kompilowanie kodu  
 W tym przykładzie kodu wymaga następujących elementów:  
  
-   Dokument programu Visio o nazwie `myDrawing.vsd` musi znajdować się w katalogu o nazwie `Test` w *Moje dokumenty* folder (dla systemu Windows XP i starszych) lub *dokumenty* folder (dla systemu Windows Vista).  
  
-   Dokument programu Visio o nazwie `myStencil.vss` musi znajdować się w katalogu o nazwie `Test` w *Moje dokumenty* folder (dla systemu Windows XP i starszych) lub *dokumenty* folder (dla systemu Windows Vista).  
  
-   Dokument programu Visio o nazwie `myTemplate.vst` musi znajdować się w katalogu o nazwie `Test` w *Moje dokumenty* folder (dla systemu Windows XP i starszych) lub *dokumenty* folder (dla systemu Windows Vista).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Porady: programowane otwieranie dokumentów Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Porady: programowane zamykanie dokumentów Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Porady: programowane zapisywanie dokumentów Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Porady: programowane drukowanie dokumentów Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  