---
title: Nie można usunąć wybranej klasy, ponieważ jest używany jako typ zwracany dla co najmniej jedną metodę DataContext | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b5781508083524a5cf7374a12fd962f0fe34aaf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Nie można usunąć wybranej klasy, ponieważ jest używany jako typ zwracany dla co najmniej jedną metodę DataContext
Typ zwracany co najmniej jednego <xref:System.Data.Linq.DataContext> metod jest klasa wybranej jednostki. Usuwanie klasę jednostki, który jest używany jako typ zwracany dla <xref:System.Data.Linq.DataContext> metoda spowoduje kompilacji projektu, aby zakończyć się niepowodzeniem. Aby usunąć klasy wybranej jednostki, należy zidentyfikować <xref:System.Data.Linq.DataContext> metody, które go używać i wartość zwracanym typem klasy inną jednostkę.  
  
 Aby przywrócić zwracane typy <xref:System.Data.Linq.DataContext> metod do oryginalnego typu generowane automatycznie, najpierw usuń <xref:System.Data.Linq.DataContext> metody z okienka metod, a następnie przeciągnij obiekt z **Eksploratora serwera** / **Eksploratora bazy danych** do Projektanta obiektów relacyjnych ponownie.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zidentyfikuj <xref:System.Data.Linq.DataContext> metody, które używają klasy jednostki jako typu zwracanego przez wybranie <xref:System.Data.Linq.DataContext> metody w metodach okienko i zapoznanie się **typu zwracanego** właściwości w **właściwości** okna .  
  
2.  Ustaw **typu zwracanego** do jednostki innej klasy lub usuń <xref:System.Data.Linq.DataContext> metody z okienka metody.  
  
## <a name="see-also"></a>Zobacz także
[Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)