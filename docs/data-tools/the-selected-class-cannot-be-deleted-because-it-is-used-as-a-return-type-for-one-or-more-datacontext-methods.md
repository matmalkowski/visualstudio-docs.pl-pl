---
title: "Nie można usunąć wybranej klasy, ponieważ jest używany jako typ zwracany dla co najmniej jedną metodę DataContext | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 865c8f9fa91c24eed1e10bde68b239932237a62b
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Nie można usunąć wybranej klasy, ponieważ jest używany jako typ zwracany dla co najmniej jedną metodę DataContext
Typ zwracany co najmniej jednego <xref:System.Data.Linq.DataContext> metod jest klasa wybranej jednostki. Usuwanie klasę jednostki, który jest używany jako typ zwracany dla <xref:System.Data.Linq.DataContext> metoda spowoduje kompilacji projektu, aby zakończyć się niepowodzeniem. Aby usunąć klasy wybranej jednostki, należy zidentyfikować <xref:System.Data.Linq.DataContext> metody, które go używać i wartość zwracanym typem klasy inną jednostkę.  
  
 Aby przywrócić zwracane typy <xref:System.Data.Linq.DataContext> metod do oryginalnego typu generowane automatycznie, najpierw usuń <xref:System.Data.Linq.DataContext> metody z okienka metod, a następnie przeciągnij obiekt z **Eksploratora serwera** / **Eksploratora bazy danych** do Projektanta obiektów relacyjnych ponownie.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zidentyfikuj <xref:System.Data.Linq.DataContext> metody, które używają klasy jednostki jako typu zwracanego przez wybranie <xref:System.Data.Linq.DataContext> metody w metodach okienko i zapoznanie się **typu zwracanego** właściwości w **właściwości** okna .  
  
2.  Ustaw **typu zwracanego** do jednostki innej klasy lub usuń <xref:System.Data.Linq.DataContext> metody z okienka metody.  
  
## <a name="see-also"></a>Zobacz także
[Komunikaty Projektanta obiektów relacyjnych](../data-tools/o-r-designer-messages.md)  
[LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)