---
title: Ta metoda powiązane jest metoda pomocnicza następujące domyślne insert, update lub metody delete
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 232f8622592a6abd17df4dfefddf6cf26c0c7511
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Ta metoda powiązane jest metoda pomocnicza następujące domyślne insert, update lub metody delete

Ta metoda powiązane jest metoda pomocnicza następujące domyślne insert, update lub metody delete. Jeśli zostanie usunięta, te metody także zostaną usunięte. Czy chcesz kontynuować?

Wybrane `DataContext` metody jest obecnie używana jako jedną z metod Insert, Update lub Delete dla jednej z klas jednostek w Projektancie obiektów relacyjnych. Usunięcie wybranej metody powodują klasę jednostki, która była za pomocą tej metody można powrócić do domyślne zachowanie środowiska wykonawczego do operacji Insert, Update, lub usunąć w trakcie aktualizacji.

## <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Aby usunąć wybranej metody, powodując klasy jednostki do korzystania z aktualizacji środowiska uruchomieniowego

- Kliknij przycisk **Tak**.

    Wybrane metody zostaną usunięte i wszystkie klasy, które użyć tej metody dla zastępowanie zachowania aktualizacji są przywracane do przy użyciu domyślnego LINQ do SQL zachowania w czasie wykonywania.

## <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Aby zamknąć okno komunikatu, pozostawiając wybranej metody bez zmian

- Kliknij przycisk **nr**.

    Zamyka okno komunikatu i nie zostały zmienione.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)