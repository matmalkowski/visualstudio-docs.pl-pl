---
title: 'Porady: zmiana położenia zakładki na Wstążce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 65a610ac75af4fe6e29070b83286fb3b4f8b91cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Porady: zmiana położenia zakładki na wstążce
  Można zmienić kolejność kart niestandardowych na Wstążce za pomocą **edytora kolekcji kartę**. Niestandardowe karty można umieścić przed lub po wbudowanej karty na Wstążce. Tabulator wbudowana jest karta, która jest już na Wstążce aplikacji pakietu Microsoft Office. Na przykład **danych** karta jest wbudowanej karty w programie Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Aby zmienić kolejność kart na Wstążce  
  
1.  Wybierz plik kodu wstążki (plik .vb lub CS) w **Eksploratora rozwiązań**.  
  
2.  Na **widoku** menu, kliknij przycisk **projektanta**.  
  
3.  Kliknij prawym przyciskiem myszy projektanta wstążki, a następnie kliknij przycisk **właściwości**.  
  
4.  W **właściwości** wybierz **karty** właściwości, a następnie kliknij przycisk wielokropka (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Projektant elipsy")).  
  
     **Edytora kolekcji kartę** pojawi się.  
  
5.  W **edytora kolekcji kartę**w **członków** listy, wybierz kartę, aby przenieść i kliknij w górę lub strzałkę w dół, aby zmienić kolejność tabulacji.  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Aby umieścić na karcie przed lub po wbudowanej karty na Wstążce  
  
1.  Projektant wstążki wybierz kart niestandardowych.  
  
2.  W **właściwości** okna, rozwiń węzeł **ControlId** właściwości, a następnie upewnij się, że wartość **ControlIdType** właściwość jest ustawiona na **niestandardowy**.  
  
3.  W **właściwości** okna, rozwiń węzeł **pozycji** właściwości.  
  
4.  Ustaw **PositionType** odpowiedniej wartości dla właściwości:  
  
    -   **BeforeOfficeId** umieszcza grupy przed określonym wbudowanej karty.  
  
    -   **AfterOfficeId** umieszcza grupy po określonym wbudowanej karty.  
  
5.  Ustaw **OfficeId** właściwość identyfikatora formantu karty wbudowane.  
  
     Lista kontroli identyfikatorów, zobacz [pliki Pomocy pakietu Office 2010: identyfikatory formantu interfejsu użytkownika Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Zobacz też  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML wstążki](../vsto/ribbon-xml.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  