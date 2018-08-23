---
title: 'Przykładowe rozszerzenie programu Excel: Klasa ActionFilter | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5e6aff4a57dfb84760ceb4513e06d063c01a5af0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679695"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Przykładowe rozszerzenie programu Excel: klasa ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Przykładowe rozszerzenie programu Excel: klasa ActionFilter](https://docs.microsoft.com/visualstudio/test/sample-excel-extension-actionfilter-class).  
  
Klasa wewnętrznego rozszerza <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> klasy i reprezentuje filtr akcji testowych na [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] elementu.  
  
## <a name="simple-properties"></a>Proste właściwości  
 Te właściwości tylko do odczytu włączone dla deweloperów określić, jak ten filtr akcji testu jest wykonywane przez kodowanych testów interfejsu użytkownika. Na przykład <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> właściwość zawiera nazwę filtru akcji. Inne właściwości get <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> filtr akcji <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> nazwę dla akcji testów, które są filtrowane według tego testu filtru akcji. Niektóre wskazują czy <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> i tego, czy akcja testu jest także <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## <a name="processrule-method"></a>Metoda ProcessRule  
 Ta metoda jest wywoływana przez kodowanych testów interfejsu użytkownika i wykonuje filtr względem dostarczonego <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>. To zastąpienie określonego usuwa myszy wybierz akcję, komórkę, podczas następnej akcji w stosie wysyła naciśnięcia klawiszy do komórki. Następnie zwraca `false`.  
  
## <a name="private-methods"></a>Metody prywatne  
 `IsLeftClick` Metoda określa, czy podana Akcja reprezentuje kliknięcie lewym przyciskiem myszy kursora myszy. `AreActionsOnSameExcelCell` Metoda określa, czy podane dwie akcje są wykonywane w tej samej komórki w programie Excel.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



