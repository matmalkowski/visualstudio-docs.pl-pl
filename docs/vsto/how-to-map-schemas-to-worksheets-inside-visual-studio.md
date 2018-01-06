---
title: "Porady: mapowanie schematów z arkuszami w programie Visual Studio | Dokumentacja firmy Microsoft"
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
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2dc089fb2c4ae2714a0b94d7756aaa432406ef74
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Porady: mapowanie schematów z arkuszami w programie Visual Studio
  Gdy arkusz jest otwarty w programie Visual Studio, możesz mapować schematu XML do arkusza. Można użyć tych samych narzędzi Microsoft Office Excel, których używasz, gdy skoroszyt jest otwarty poza Visual Studio. Office project tworzy obiekty tej samej, czy mapowanie schematu do arkusza przed lub po utworzeniu rozwiązania programu Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Nie można użyć wieloczęściowego schematów XML rozwiązania programu Excel.  
  
### <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Do mapowania schematu XML arkusza programu Excel w programie Visual Studio  
  
1.  Otwórz projekt skoroszytu lub szablon programu Excel w programie Visual Studio.  
  
2.  Kliknij arkusz, aby przejść do projektanta.  
  
3.  Na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, należy go najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  W **XML** kliknij przycisk **źródła**.  
  
     **Źródło XML** zostanie otwarte okno.  
  
5.  W **źródło XML** okna, kliknij przycisk **mapy XML**.  
  
     **Mapy XML** zostanie otwarte okno dialogowe.  
  
6.  W **mapy XML** okno dialogowe, kliknij przycisk **Dodaj**.  
  
7.  Przejdź do pliku schematu, zaznacz go, a następnie kliknij przycisk **Otwórz**.  
  
8.  Kliknij przycisk **OK**.  
  
     Schemat jest reprezentowana w **źródło XML** okna. W projekcie typu <xref:System.Data.DataSet> jest generowany na podstawie schematu, a <xref:System.Windows.Forms.BindingSource> jest tworzony.  
  
9. Przeciągnij elementy z **źródło XML** okna miejsc, w arkuszu miejscu odpowiedniego służy do utworzenia.  
  
     Przeciągnięcie elementu schematu niepowtarzającymi Office project generuje <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> formant, który jest automatycznie powiązany <xref:System.Windows.Forms.BindingSource>.  
  
     Przeciągnięcie powtarzający się element schematu Office project generuje <xref:Microsoft.Office.Tools.Excel.ListObject> formant, który nie jest automatycznie powiązany ze źródłem danych. Aby uzyskać więcej informacji, zobacz [schematów XML i danych na poziomie dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: mapowanie schematów z dokumentami programu Word w Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Schematy XML i dane dostosowywane na poziomie dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  