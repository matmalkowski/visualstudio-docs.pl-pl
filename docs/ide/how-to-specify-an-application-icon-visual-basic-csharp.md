---
title: "Porady: Określanie ikony aplikacji (Visual Basic, C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 17cce04dd94829225823de676e286b7d0158abec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Porady: określanie ikony aplikacji (Visual Basic, C#)
`Icon` Właściwości dla projektu określa plik ikony (.ico) który będzie wyświetlany dla skompilowanej aplikacji w Eksploratorze plików, a na pasku zadań systemu Windows.  
  
 `Icon` Właściwości można uzyskać w **aplikacji** okienku **projektanta projektu**; zawiera listę ikony, które zostały dodane do projektu jako zasoby lub plików zawartości.  
  
> [!NOTE]
>  Po ustawieniu właściwości ikona dla aplikacji, można również ustawić `Icon` właściwości każdego **okna** lub **formularza** w aplikacji. Informacje o okna ikony dla aplikacji autonomicznych Windows Presentation Foundation (WPF), zobacz <xref:System.Windows.Window.Icon%2A> właściwości.  
  
### <a name="to-specify-an-application-icon"></a>Aby określić ikony aplikacji  
  
1.  W **Eksploratora rozwiązań**, wybierz węzeł projektu (nie **rozwiązania** węzła).  
  
2.  Na pasku menu wybierz **projektu**, **właściwości**.  
  
3.  Gdy **projektanta projektu** zostanie wyświetlone, wybierz **aplikacji** kartę.  
  
4.  **(Visual Basic)**  w **ikona** listy, wybierz plik ikony (.ico).  
  
     **C#** pobliżu **ikona** wybierz  **\<Przeglądaj >** przycisk, a następnie przejdź do lokalizacji pliku ikony, która ma.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Zarządzanie właściwościami aplikacji](../ide/application-properties.md)  
 [Porady: Dodawanie lub usuwanie zasobów](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)