---
title: Ta powiązana metoda to metoda zapasowa następujących domyślnych metod wstawiania, aktualizowania lub usuwania
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 30e08cb10b6e1912fe5962620faf34a1c6250cf3
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174171"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Ta powiązana metoda to metoda zapasowa następujących domyślnych metod wstawiania, aktualizowania lub usuwania

Ta powiązana metoda to metoda zapasowa następujące domyślne `Insert`, `Update`, lub `Delete` metody. Jeśli zostanie usunięta, te metody także zostaną usunięte. Czy chcesz kontynuować?

Wybrane `DataContext` metoda jest obecnie używany jako jeden z `Insert`, `Update`, lub `Delete` metody dla jednej z klas jednostek na **O/R Designer**. Usunięcie przyczyny wybranej metody Klasa jednostki, która została przy użyciu tej metody, aby powrócić do domyślnego zachowania czasu wykonywania do operacji wstawiania, aktualizowania lub usuwania podczas aktualizacji.

## <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Można usunąć wybranej metody, powodując Klasa jednostki użyć aktualizacje środowiska uruchomieniowego

- Kliknij przycisk **Tak**.

    Wybranej metody zostanie usunięty, a wszystkie klasy, które umożliwiający zastępowanie zachowania aktualizacji tej metody są przywracane przy użyciu domyślnego LINQ do zachowania w czasie wykonywania SQL.

## <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Aby zamknąć okno komunikatu, pozostawiając wybranej metody bez zmian

- Kliknij przycisk **nie**.

    Zamyka okno komunikatu, i są wprowadzane żadne zmiany.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)