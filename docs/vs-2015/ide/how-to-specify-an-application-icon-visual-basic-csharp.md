---
title: 'Porady: Określanie ikony aplikacji (Visual Basic, C#) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d696766d2dd32ada86d74754dce87320e8f1627
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680283"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Porady: określanie ikony aplikacji (Visual Basic, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Określanie ikony aplikacji (Visual Basic, C#)](https://docs.microsoft.com/visualstudio/ide/how-to-specify-an-application-icon-visual-basic-csharp).  
  
`Icon` Właściwość dla projektu określa plik ikony (.ico), która będzie wyświetlana dla aplikacji skompilowanych w Eksploratorze plików i na pasku zadań Windows.  
  
 `Icon` Właściwości można uzyskiwać w **aplikacji** okienku **projektanta projektu**; zawiera on listę ikon, które zostały dodane do projektu jako zasoby lub pliki zawartości.  
  
> [!NOTE]
>  Po ustawieniu właściwości ikony dla aplikacji, możesz również ustawić `Icon` właściwości każdego **okna** lub **formularza** w aplikacji. Aby uzyskać informacji na temat okna ikony dla aplikacji autonomicznych Windows Presentation Foundation (WPF), zobacz <xref:System.Windows.Window.Icon%2A> właściwości.  
  
### <a name="to-specify-an-application-icon"></a>Aby określić ikony aplikacji  
  
1.  W **Eksploratora rozwiązań**, wybierz węzeł projektu (nie **rozwiązania** węzła).  
  
2.  Na pasku menu wybierz **projektu**, **właściwości**.  
  
3.  Gdy **projektanta projektu** pojawi się, wybierz **aplikacji** kartę.  
  
4.  **(Visual Basic)**  w **ikonę** listy, wybierz plik ikony (.ico).  
  
     **C#** w pobliżu **ikonę** wybierz  **\<Przeglądaj … >** przycisk, a następnie przejdź do lokalizacji pliku ikony, która ma.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Zarządzanie właściwościami aplikacji](../ide/application-properties.md)  
 [Porady: Dodawanie lub usuwanie zasobów](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)



