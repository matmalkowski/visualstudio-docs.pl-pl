---
title: Nie można usunąć właściwości
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d12f974e1949bfb96cd2d6bb774eb2b73f371689
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Właściwość \<właściwość name > nie można usunąć

Właściwość \<właściwość name > nie można usunąć, ponieważ jest ona ustawiona jako **właściwość rozróżniacza** dziedziczenia między \<Nazwa klasy > i \<Nazwa klasy >

Wybranej właściwości jest ustawiana jako **właściwość rozróżniacza** dziedziczenia między klasami wskazany w komunikacie o błędzie. Nie można usunąć właściwości, jeśli są elementami konfiguracji dziedziczenia między klasami danych.

Ustaw **właściwość rozróżniacza** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. W Projektancie obiektów relacyjnych wybierz linii dziedziczenia, który łączy klas danych wskazany w komunikacie o błędzie.

2. Ustaw **rozróżniacza** właściwości inną właściwość.

3. Spróbuj ponownie usunąć właściwości.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)