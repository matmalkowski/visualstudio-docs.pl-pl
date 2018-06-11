---
title: 'Porady: dostosowywanie wbudowanej karty'
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
- built-in tabs [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 30b4af116df218f3f778b9efa1e295fbadbad86a
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257270"
---
# <a name="how-to-customize-a-built-in-tab"></a>Porady: dostosowywanie wbudowanej karty
  Możesz dodać grup i kontroli do wbudowanej karty. Tabulator wbudowana jest karta, która jest już na Wstążce aplikacji pakietu Microsoft Office. Na przykład **danych** karta jest wbudowanej karty w programie Excel. Podczas tworzenia niestandardowych grup pojawia się na karcie ostatnich, ale można przenieść tej grupy dowolne miejsce na karcie.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Można dodać grupy do wbudowanej karty, ale nie można usunąć wbudowanych grup z wbudowanej karty.  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>Aby dodać grupy do wbudowanej karty  
  
1.  Kliknij prawym przyciskiem myszy plik kodu wstążki w **Eksploratora rozwiązań**, a następnie kliknij przycisk **Widok projektanta**.  
  
    > [!NOTE]  
    >  Jeśli nie ma pliku kodu wstążki **Eksploratora rozwiązań**, należy dodać **element wstążki** do projektu. Zobacz [porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Kliknij prawym przyciskiem myszy dowolną kartę w Projektancie wstążki, a następnie kliknij przycisk **właściwości**.  
  
3.  W **właściwości** okna, rozwiń węzeł **ControlId** właściwości, a następnie ustawić **ControlIdType** właściwości **Office**.  
  
4.  Ustaw **OfficeId** właściwości *identyfikator formantu* karty wbudowane, który chcesz dostosować.  
  
     Identyfikator formantu jest to nazwa, który unikatowo identyfikuje kart, grup i kontrolek, które są wbudowane w aplikacji Microsoft Office.  
  
     Lista kontroli identyfikatorów, zobacz [pliki Pomocy pakietu Office 2010: identyfikatory formantu interfejsu użytkownika fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  Z **formantów wstążki pakietu Office** karcie **przybornika**, przeciągnij grupy na karcie.  
  
    > [!NOTE]  
    >  Wbudowane grupy nie są wyświetlane w projektancie. Dlatego jedynym sposobem, aby określić, czy użytkownik korzysta z wbudowanej karty jest zbadanie **ControlId** właściwości karty.  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>Aby umieścić grupy wbudowanej karty  
  
1.  Wybierz grupę niestandardowych w Projektancie wstążki.  
  
2.  W **właściwości** okna, rozwiń węzeł **pozycji** właściwości.  
  
3.  Ustaw **PositionType** odpowiedniej wartości dla właściwości:  
  
    -   **BeforeOfficeId** umieszcza grupy przed określonej grupy wbudowane.  
  
    -   **AfterOfficeId** umieszcza po określonej grupy wbudowane grupy.  
  
4.  Ustaw **OfficeId** właściwość identyfikatora formantu wbudowane grupy.  
  
     Lista kontroli identyfikatorów, zobacz [pliki Pomocy pakietu Office 2010: identyfikatory formantu interfejsu użytkownika fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Zobacz także  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML wstążki](../vsto/ribbon-xml.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Porady: zmiana położenia zakładki na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Porady: dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Porady: dodatek Pokaż błędy interfejsu użytkownika](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  