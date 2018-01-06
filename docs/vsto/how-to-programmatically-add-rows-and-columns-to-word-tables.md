---
title: 'Porady: programowane Dodawanie wierszy i kolumn do tabel Word | Dokumentacja firmy Microsoft'
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
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 56d8c3d0c578d2dc13cf65af680bc2fb804f3539
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Porady: Programowane dodawanie wierszy i kolumn do tabel programu Word
  W tabeli programu Microsoft Office Word komórki są zorganizowane w wiersze i kolumny. Można użyć <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Rows> obiekt do dodania wierszy do tabeli i <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Columns> obiekt, aby dodać kolumny.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customization-examples"></a>Przykłady dostosowania na poziomie dokumentu  
 W poniższych przykładach kodu może służyć w dostosowaniu poziomie dokumentu. Aby użyć tych przykładów, uruchom je z `ThisDocument` klasy w projekcie. Tych przykładów założono, że dokument skojarzony z dostosowanie już ma co najmniej jedna tabela.  
  
> [!IMPORTANT]  
>  Ten kod zadziała tylko w przypadku projektów utworzonych za pomocą dowolnej z następujących szablonów projektu:  
>   
>  -   Dokument programu Word 2013  
> -   Szablon programu Word 2013  
> -   Dokument programu Word 2010  
> -   Szablon programu Word 2010  
>   
>  Jeśli chcesz wykonać tego zadania w żadnym innym typem projektu, należy dodać odwołanie do **Microsoft.Office.Interop.Word** zestawu, a następnie użyć klasy z tego zestawu można dodać wierszy i kolumn do tabel. Aby uzyskać więcej informacji, zobacz [porady: docelowy Office aplikacji za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołania zestawu Interop Word 2010 podstawowy](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### <a name="to-add-a-row-to-a-table"></a>Aby dodać wiersz do tabeli  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody, aby dodać wiersz do tabeli.  
  
     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>Aby dodać kolumnę do tabeli  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody, a następnie użyć <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metody, aby wyświetlić wszystkie kolumny tej samej szerokości.  
  
     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]  
  
## <a name="vsto-add-in-examples"></a>Przykłady dodatku narzędzi VSTO  
 W poniższych przykładach kodu można w dodatku VSTO. Aby użyć w przykładach, uruchom je z `ThisAddIn` klasy w projekcie. Tych przykładów założono, że aktywny dokument ma już co najmniej jedna tabela.  
  
> [!IMPORTANT]  
>  Ten kod zadziała tylko w przypadku projektów utworzonych za pomocą szablonów w dodatku VSTO programu Word.  
>   
>  Jeśli chcesz wykonać tego zadania w żadnym innym typem projektu, należy dodać odwołanie do **Microsoft.Office.Interop.Word** zestawu, a następnie użyć klasy z tego zestawu można dodać wierszy i kolumn do tabel. Aby uzyskać więcej informacji, zobacz [porady: docelowy Office aplikacji za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołania zestawu Interop Word 2010 podstawowy](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### <a name="to-add-a-row-to-a-table"></a>Aby dodać wiersz do tabeli  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody, aby dodać wiersz do tabeli.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>Aby dodać kolumnę do tabeli  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody, a następnie użyć <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metody, aby wyświetlić wszystkie kolumny tej samej szerokości.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: programowane Tworzenie tabel programu Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Porady: programowane Dodawanie tekstu i formatowania do komórek w tabelach programu Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Instrukcje: Programowe wypełnianie tabel programu Word właściwościami dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  