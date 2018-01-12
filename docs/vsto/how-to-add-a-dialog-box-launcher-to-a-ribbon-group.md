---
title: "Porady: Dodawanie przycisk Uruchom okno dialogowe do grupy wstążek | Dokumentacja firmy Microsoft"
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
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 49dee3d090e2b7f985fd85a6061dea3a2c204e4a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Porady: dodawanie przycisk Uruchom okno dialogowe do grupy wstążek
  Uruchom okno dialogowe można dodać do żadnej grupy na Wstążce. Uruchom okno dialogowe jest mała ikona, który pojawia się w grupie. Użytkownicy kliknij tę ikonę, aby otworzyć określone okno dialogowe lub okienka zadań, które zapewniają więcej opcji, które odnoszą się do grupy.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Aby dodać przycisk Uruchom okno dialogowe do grupy wstążek  
  
1.  Wybierz plik kodu wstążki (plik .vb lub CS) w **Eksploratora rozwiązań**.  
  
2.  Na **widoku** menu, kliknij przycisk **projektanta**.  
  
3.  W Projektancie wstążki, kliknij prawym przyciskiem myszy dowolną grupę, a następnie kliknij przycisk **dodać DialogBoxLauncher**.  
  
     Dodaj kod, aby <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> zdarzeń grupy, aby otworzyć okno dialogowe niestandardowych i wbudowanych.  
  
## <a name="see-also"></a>Zobacz też  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office Development ― przykłady i wskazówki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [Model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md)   
 [XML wstążki](../vsto/ribbon-xml.md)   
 [Porady: eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Porady: zmiana położenia zakładki na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Porady: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)   
 [Porady: dodawanie formantów do widoku Zakulisowego](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Porady: Pokaż błędy interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Wskazówki: Aktualizowanie formantów na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  