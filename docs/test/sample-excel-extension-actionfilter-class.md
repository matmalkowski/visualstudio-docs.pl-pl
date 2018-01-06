---
title: "Przykładowe rozszerzenie programu Excel: Klasa ActionFilter | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: "11"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 6a76f89db120f8655d63a064cb3d851abb9eac64
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sample-excel-extension-actionfilter-class"></a>Przykładowe rozszerzenie programu Excel: klasa ActionFilter
Wewnętrzna klasa rozszerza <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> klasy i reprezentuje filtr akcji testu na [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] elementu.  
  
## <a name="simple-properties"></a>Proste właściwości  
 Te właściwości tylko do odczytu Włącz projektanta określić, jak ten filtr akcji testu ma zostać wykonana przez platformę testowanie kodowanego interfejsu użytkownika. Na przykład <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> właściwość zawiera nazwę filtru akcji. Inne get właściwości <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> filtr akcji <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> nazwę akcji testów, które zostały przefiltrowane przez filtr akcji tego testu. Inne wskazuje czy <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> , a także, czy akcja testu jest <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## <a name="processrule-method"></a>ProcessRule — metoda  
 Ta metoda jest wywoływana przez framework testowanie kodowanego interfejsu użytkownika i wykonuje filtr przed dostarczonych <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>. To zastąpienie określonego usuwa myszy wybierz akcję w komórce, podczas następnej akcji w stosie wysyła naciśnięcia klawiszy do komórki. Następnie zwraca `false`.  
  
## <a name="private-methods"></a>Metody prywatne  
 `IsLeftClick` Metoda określa, czy podanej akcji reprezentuje kliknięcie lewym przyciskiem myszy myszy. `AreActionsOnSameExcelCell` Metoda określa, czy dwie podane akcje są wykonywane na tym samym komórki w programie Excel.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
