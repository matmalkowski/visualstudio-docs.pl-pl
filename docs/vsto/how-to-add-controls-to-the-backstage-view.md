---
title: "Porady: dodawanie formantów do widoku Zakulisowego | Dokumentacja firmy Microsoft"
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
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
ms.assetid: 4fda1278-9aea-4d54-928a-269a81584494
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a16c564b39afdc2ec3cf3e15883fc05b2a13f5d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Porady: dodawanie formantów do widoku zakulisowego
  Projektant wstążki umożliwia dodawanie formantów do menu dostępnym po kliknięciu **pliku** kartę po uruchomieniu aplikacji, kontrolek, które dodajesz do **pliku** karta jest wyświetlana grupa o nazwie  **Dodatki**.  
  
 Nie możesz umieścić kontrolek przed lub po formantów wbudowanych za pomocą projektanta wstążki w programie Visual Studio. Wbudowane funkcje sterowania jest już wyświetlany w widoku Backstage formantu. Jeśli chcesz umieścić kontrolek przed lub po formantów wbudowanych, należy użyć XML wstążki. Aby uzyskać więcej informacji na temat **wstążki (XML)**, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md). Aby uzyskać więcej informacji dotyczących dostosowywania widoku Backstage, zobacz [wprowadzenie do pakietu Office 2010 Backstage widoku dla deweloperów](http://go.microsoft.com/fwlink/?LinkId=182189) i [dostosowywania widoku Backstage pakietu Office 2010 dla deweloperów](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Aby dodać kontrolki do widoku Backstage  
  
1.  Otwórz element wstążki w widoku Projekt.  
  
     Aby uzyskać informacje o sposobie dodawania **wstążki (projektanta wizualnego)** elementu do projektu, zobacz [jak: pobrać uruchomiona Dostosowywanie wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML wstążki](../vsto/ribbon-xml.md)   
 [Porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  