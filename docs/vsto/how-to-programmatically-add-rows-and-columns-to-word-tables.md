---
title: 'Porady: programowane Dodawanie wierszy i kolumn do tabel Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 865a33e181d761665dbe2e44976f171a2b60d433
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255892"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Porady: programowane Dodawanie wierszy i kolumn do tabel Word
  W tabeli programu Microsoft Office Word komórki są zorganizowane w wiersze i kolumny. Można użyć <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Rows> obiekt do dodania wierszy do tabeli i <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Columns> obiekt, aby dodać kolumny.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customization-examples"></a>Przykłady dostosowania na poziomie dokumentu  
 W poniższych przykładach kodu może służyć w dostosowaniu poziomie dokumentu. Aby użyć tych przykładów, uruchom je z `ThisDocument` klasy w projekcie. Tych przykładów założono, że dokument skojarzony z dostosowanie już ma co najmniej jedna tabela.  
  
> [!IMPORTANT]  
>  Ten kod zadziała tylko w przypadku projektów utworzonych za pomocą dowolnej z następujących szablonów projektu:  
>   
> -   Dokument programu Word 2013  
> -   Szablon programu Word 2013  
> -   Dokument programu Word 2010  
> -   Szablon programu Word 2010  
>   
>  Jeśli chcesz wykonać tego zadania w żadnym innym typem projektu, należy dodać odwołanie do **Microsoft.Office.Interop.Word** zestawu, a następnie użyć klasy z tego zestawu można dodać wierszy i kolumn do tabel. Aby uzyskać więcej informacji, zobacz [porady: aplikacje pakietu Office docelowym za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołania podstawowego zestawu międzyoperacyjnego Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
### <a name="to-add-a-row-to-a-table"></a>Aby dodać wiersz do tabeli  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody, aby dodać wiersz do tabeli.  
  
     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]  
  
### <a name="to-add-a-column-to-a-table"></a>Aby dodać kolumnę do tabeli  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody, a następnie użyć <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metody, aby wyświetlić wszystkie kolumny tej samej szerokości.  
  
     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]  
  
## <a name="vsto-add-in-examples"></a>Przykłady dodatku narzędzi VSTO  
 W poniższych przykładach kodu można w dodatku VSTO. Aby użyć w przykładach, uruchom je z `ThisAddIn` klasy w projekcie. Tych przykładów założono, że aktywny dokument ma już co najmniej jedna tabela.  
  
> [!IMPORTANT]  
>  Ten kod zadziała tylko w przypadku projektów utworzonych za pomocą szablonów w dodatku VSTO programu Word.  
>   
>  Jeśli chcesz wykonać tego zadania w żadnym innym typem projektu, należy dodać odwołanie do **Microsoft.Office.Interop.Word** zestawu, a następnie użyć klasy z tego zestawu można dodać wierszy i kolumn do tabel. Aby uzyskać więcej informacji, zobacz [porady: aplikacje pakietu Office docelowym za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołania podstawowego zestawu międzyoperacyjnego Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
### <a name="to-add-a-row-to-a-table"></a>Aby dodać wiersz do tabeli  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metody, aby dodać wiersz do tabeli.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]  
  
### <a name="to-add-a-column-to-a-table"></a>Aby dodać kolumnę do tabeli  
  
1.  Użyj <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metody, a następnie użyć <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metody, aby wyświetlić wszystkie kolumny tej samej szerokości.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: programowane Tworzenie tabel programu Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Porady: programowane Dodawanie tekstu i formatowania do komórek w tabelach programu Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Porady: programowane Wypełnianie tabel programu Word właściwościami dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  