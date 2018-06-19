---
title: Co najmniej jeden wybrany element zawiera typ danych, który nie jest obsługiwany przez projektanta
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
ms.openlocfilehash: 710bd42ea87f4d994a3176a736a55f534d1d9fd4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920789"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Co najmniej jeden wybrany element zawiera typ danych, który nie jest obsługiwany przez projektanta

Co najmniej jeden z elementów przeciągnięte z **Eksploratora serwera**/**Eksploratora bazy danych** na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] zawiera dane typu, który nie jest obsługiwany przez [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] na przykład [Typy danych zdefiniowane przez użytkownika CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Utwórz widok, w którym jest oparty na żądaną tabeli i nie zawiera nieobsługiwany typ danych.

2. Przeciągnij widoku z **Eksploratora serwera**/**Eksploratora bazy danych** do projektanta.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)