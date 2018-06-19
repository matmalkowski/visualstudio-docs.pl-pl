---
title: Zmiany zwracanego typu metody DataContext nie można cofnąć
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 40c68aba0599f2f86285cbea841d06f0a652828a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921489"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Zmiany zwracanego typu metody DataContext nie można cofnąć

Nie można cofnąć zmiany zwracanego typu metody DataContext. Aby przywrócić automatycznie wygenerowany typ, musisz przeciągnąć element z Eksploratora serwera Explorer/bazy danych do Projektanta obiektów relacyjnych ponownie. Czy na pewno chcesz zmienić zwracany typ?

Zwracany typ <xref:System.Data.Linq.DataContext> metoda różni się w zależności od tego, gdzie upuścić element [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Jeśli musisz porzucić elementu bezpośrednio na istniejącej klasy jednostki, <xref:System.Data.Linq.DataContext> utworzeniu metodę, która ma zwracany typ klasy jednostka. Jeśli element jest upuścić nad pustym obszarem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], <xref:System.Data.Linq.DataContext> metodę zwracającą automatycznie wygenerowany typ jest tworzony. Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu do okienka metody. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz go i kliknij **typu zwracanego** właściwości w **właściwości** okna.

## <a name="to-change-the-return-type-of-a-datacontext"></a>Aby zmienić zwracany typ DataContext

- Kliknij przycisk **Tak**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Aby zamknąć okno komunikatu i pozostawić bez zmian typu zwracanego

- Kliknij przycisk **nr**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Aby przywrócić oryginalny typ zwracany po zmianie typu zwracanego

1. Wybierz <xref:System.Data.Linq.DataContext> metoda [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] i usuń go.

2. Znajdź element w **Eksploratora Explorer/bazy danych serwera** i przeciągnij go na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

    A <xref:System.Data.Linq.DataContext> metody jest tworzony z oryginalnego domyślny typ zwracany.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)