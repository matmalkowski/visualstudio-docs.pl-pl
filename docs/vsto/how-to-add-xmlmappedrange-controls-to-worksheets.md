---
title: 'Porady: dodawanie formantów XMLMappedRange do arkuszy'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55b6c83624c3ccb6c28701cd97753ea155e37288
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263983"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Porady: dodawanie formantów XMLMappedRange do arkuszy
  Podczas mapowania elementu XML do komórki w programie Microsoft Office Excel, programu Visual Studio automatycznie dodaje <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> formantu do arkusza.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Formant nie jest dostępny na **przybornika** lub **źródeł danych** okna. Ponadto nie można utworzyć <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> steruje programowo.  
  
## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Aby dodać do arkusza xmlmappedrange — formant  
  
1.  Otwórz skoroszyt programu Excel w projektancie programu Visual Studio.  
  
2.  Otwórz skoroszyt, w której chcesz dodać kontrolki.  
  
3.  Na **Developer** , kliknij pozycję **źródła**.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna na Wstążce, należy ją włączyć. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     **Źródło XML** pojawi się okienko zadań.  
  
4.  W **źródło XML** okienka zadań, kliknij przycisk **mapy XML**.  
  
5.  W **mapy XML** okno dialogowe, kliknij przycisk **Dodaj**.  
  
     **Źródło XML** zostanie wyświetlone okno dialogowe.  
  
6.  Wybierz schemat XML z **źródło XML** okno dialogowe i kliknij przycisk **Otwórz**.  
  
     Schemat jest dodawany do **mapy XML** okno dialogowe.  
  
7.  W **mapy XML** okno dialogowe, kliknij przycisk **OK**.  
  
8.  Przeciągnij element na podstawie **źródło XML** okienka zadań do komórki w arkuszu.  
  
     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Jest tworzony i dodawany do projektu.  
  
    > [!NOTE]  
    >  Przeciągnięcie elementu nadrzędnego z **źródło XML** okienka zadań <xref:Microsoft.Office.Tools.Excel.ListObject> formant nie zostanie utworzony.  
  
## <a name="see-also"></a>Zobacz także  
 [Xmlmappedrange — formant](../vsto/xmlmappedrange-control.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Porady: mapowanie schematów z arkuszami w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  