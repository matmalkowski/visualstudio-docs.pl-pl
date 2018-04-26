---
title: Nie można usunąć właściwości, ponieważ uczestniczy ona w skojarzeniu
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 98f95c489758b808ae7a210f7d83332f84571d1f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Właściwość &lt;nazwa właściwości&gt; nie można usunąć, ponieważ uczestniczy ona w skojarzeniu &lt;Nazwa skojarzenia&gt;

Wybranej właściwości jest ustawiana jako **właściwości skojarzenia** dla skojarzenia między klasami wskazany w komunikacie o błędzie. Nie można usunąć właściwości, jeśli są elementami skojarzenie między klasami danych.

Ustaw **właściwości skojarzenia** na inną właściwość klasy danych, aby umożliwić pomyślne usunięcie żądanej właściwości.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Wybierz wiersz skojarzenia w Projektancie obiektów relacyjnych łączącego klas danych wskazany w komunikacie o błędzie.

2. Kliknij dwukrotnie linię, aby otworzyć **Edytor skojarzenia** okno dialogowe.

3. Usuń właściwość z **właściwości skojarzenia**.

4. Spróbuj ponownie usunąć właściwości.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)