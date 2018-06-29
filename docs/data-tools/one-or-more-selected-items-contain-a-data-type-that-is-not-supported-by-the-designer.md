---
title: Co najmniej jeden wybrany element zawiera typ danych nieobsługiwany przez projektanta
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 68d8675df54e37b9a6122b853e742addc0d8060c
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089493"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Co najmniej jeden wybrany element zawiera typ danych nieobsługiwany przez projektanta

Co najmniej jeden z elementów przeciągnięte z **Eksploratora serwera** lub **Eksploratora bazy danych** na **Projektanta obiektów relacyjnych** zawiera dane typu, który nie jest obsługiwany przez **O /R projektanta**, na przykład [typy danych zdefiniowane przez użytkownika CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Utwórz widok, w którym jest oparty na żądaną tabeli i nie zawiera nieobsługiwany typ danych.

2. Przeciągnij widoku z **Eksploratora serwera** lub **Eksploratora bazy danych** do projektanta.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)