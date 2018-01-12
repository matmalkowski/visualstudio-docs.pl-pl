---
title: "Porady: programowane tworzenie nowych dokumentów programu Visio | Dokumentacja firmy Microsoft"
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
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 072a279bd342f60f8ebfb307a880c39bdc8b2d51
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Porady: Programowane tworzenie nowych dokumentów programu Visio
  Podczas tworzenia nowego rysunku programu Microsoft Office Visio dokumentu, Dodaj do kolekcji Microsoft.Office.Interop.Visio.Documents otwarte dokumenty programu Visio. W związku z tym metoda Microsoft.Office.Interop.Visio.Documents.Add tworzy nowy dokument rysunku programu Visio. Aby uzyskać więcej informacji, zobacz dokumentację referencyjną VBA, aby uzyskać [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) metody.  
  
## <a name="creating-new-blank-documents"></a>Tworzenie nowych dokumentów puste  
  
#### <a name="to-create-a-new-document"></a>Aby utworzyć nowy dokument  
  
-   Aby utworzyć nowy pusty dokument, który nie jest oparty na szablonie, należy użyć metody Microsoft.Office.Interop.Visio.Documents.Add.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="creating-documents-copied-from-existing-documents"></a>Tworzenie dokumentów skopiowane z istniejących dokumentów  
 Metoda Microsoft.Office.Interop.Visio.Documents.Add można utworzyć nowy dokument, który jest kopią istniejącego dokumentu programu Visio. Należy podać nazwę pliku i w pełni kwalifikowana diagramu.  
  
#### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Aby utworzyć nowy dokument, który jest skopiowany z istniejącego dokumentu  
  
-   Wywołaj metodę Microsoft.Office.Interop.Visio.Documents.Add i określ ścieżkę diagram programu Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="creating-stencils-copied-from-existing-stencils"></a>Tworzenie wzorników skopiowane z istniejącego wzorników  
 [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) metody można utworzyć nowy wzornik kopię istniejącego wzornika programu Visio. Należy podać nazwę pliku i w pełni kwalifikowana wzornika.  
  
#### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Aby utworzyć nowy wzornik, które zostaną skopiowane z istniejącego wzornika  
  
-   Wywołaj metodę Microsoft.Office.Interop.Visio.Documents.Add i określ ścieżkę wzornika.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="creating-documents-based-on-existing-templates"></a>Tworzenie dokumentów na podstawie istniejących szablonów  
 Metoda Microsoft.Office.Interop.Visio.Documents.Add można utworzyć nowego dokumentu (pliku vsd) oparty na podstawie istniejącego szablonu programu Visio (plikiem vst). Ta metoda umożliwia skopiowanie wzorników, style i ustawienia, które są częścią obszaru roboczego szablonu. Należy podać nazwę pliku i w pełni kwalifikowana szablonu.  
  
#### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Aby utworzyć nowy dokument, który jest oparty na podstawie istniejącego szablonu  
  
-   Wywołaj metodę Microsoft.Office.Interop.Visio.Documents.Add i podaj ścieżkę pliku szablonu.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 W tym przykładzie kodu wymaga następujących elementów:  
  
-   Dokument programu Visio o nazwie `myDrawing.vsd` musi znajdować się w katalogu o nazwie `Test` w folderze Moje dokumenty (dla systemu Windows XP i starszych) lub w folderze dokumenty (dla systemu Windows Vista).  
  
-   Dokument programu Visio o nazwie `myStencil.vss` musi znajdować się w katalogu o nazwie `Test` w folderze Moje dokumenty (dla systemu Windows XP i starszych) lub w folderze dokumenty (dla systemu Windows Vista).  
  
-   Dokument programu Visio o nazwie `myTemplate.vst` musi znajdować się w katalogu o nazwie `Test` w folderze Moje dokumenty (dla systemu Windows XP i starszych) lub w folderze dokumenty (dla systemu Windows Vista).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Porady: programowane otwieranie dokumentów Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Porady: programowane zamykanie dokumentów Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Porady: programowane zapisywanie dokumentów Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Instrukcje: Programowe drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  