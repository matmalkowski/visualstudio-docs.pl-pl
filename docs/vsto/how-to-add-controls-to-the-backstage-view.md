---
title: 'Porady: dodawanie formantów do widoku Backstage '
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6b775c7613b8cc0953e419b2546ec017c96e8454
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Porady: dodawanie formantów do widoku Backstage
  Projektant wstążki umożliwia dodawanie formantów do menu dostępnym po kliknięciu **pliku** kartę. Po uruchomieniu aplikacji, kontrolek, które dodajesz do **pliku** karta jest wyświetlana grupa o nazwie **dodatki**.  
  
 Nie możesz umieścić kontrolek przed lub po formantów wbudowanych za pomocą projektanta wstążki w programie Visual Studio. Wbudowane funkcje sterowania jest już wyświetlany w widoku Backstage formantu. Jeśli chcesz umieścić kontrolek przed lub po formantów wbudowanych, należy użyć XML wstążki. Aby uzyskać więcej informacji na temat **wstążki (XML)**, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md). Aby uzyskać więcej informacji dotyczących dostosowywania widoku Backstage, zobacz [wprowadzenie do pakietu Office 2010 Backstage widoku dla deweloperów](http://go.microsoft.com/fwlink/?LinkId=182189) i [dostosować widok pakietu Office 2010 Backstage dla deweloperów](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Do dodawania formantów do widoku Backstage  
  
1.  Otwórz element wstążki w widoku Projekt.  
  
     Aby uzyskać informacje o sposobie dodawania **wstążki (projektanta wizualnego)** elementu do projektu, zobacz [porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  W Projektancie Wstążki kliknij **pliku** kartę.  
  
     Zostanie wyświetlona projektanta menu. Tę powierzchnię nie zawiera żadnych formantów.  
  
3.  Z **formantów wstążki pakietu Office** karcie **przybornika**, przeciągnij dowolną z poniższych formantów do Konstruktora menu:  
  
    -   Przycisk  
  
    -   CheckBox  
  
    -   Galerii  
  
    -   Menu  
  
    -   Separator  
  
    -   Przycisk podziału  
  
    -   ToggleButton  
  
4.  Przeciągnij formanty, aby przenieść je w nowe położenie, w menu.  
  
## <a name="see-also"></a>Zobacz także  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML wstążki](../vsto/ribbon-xml.md)   
 [Porady: rozpoczynanie pracy Dostosowywanie Wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  