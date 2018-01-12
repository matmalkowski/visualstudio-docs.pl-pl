---
title: "Porady: ochrona programu Outlook przed wyświetlaniem regionów formularzy | Dokumentacja firmy Microsoft"
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
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: def4454f1031e5958dfc10e1a1fc77ccaed59067
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>Porady: ochrona programu Outlook przed wyświetlaniem regionów formularzy
  Mogą wystąpić sytuacje, w których nie ma programu Microsoft Office Outlook do wyświetlania regionu formularza dla danego elementu. Na przykład w elemencie kontaktu nie zawierają adresu biznesowych, może uniemożliwić pokazujący lokalizacji biznesowe na mapie wyświetlaniu regionu formularza.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Aby zapobiec wyświetlaniu regionu formularza programu Outlook  
  
1.  Otwórz plik kodowy dla regionu formularza, który chcesz zmodyfikować.  
  
2.  Rozwiń węzeł **fabryki regionu formularza** kodu regionu.  
  
3.  Dodaj kod, aby `FormRegionInitializing` obsługi zdarzeń, który ustawia <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> klasy do **true**.  
  
 W tym przykładzie, jeśli kontakt nie zawierają adresu <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość jest ustawiona na **true**, i nie ma regionu formularza.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Porady: dodawanie regionu formularza na projekt dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  