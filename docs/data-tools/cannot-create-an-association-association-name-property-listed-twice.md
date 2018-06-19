---
title: Nie można utworzyć skojarzenia - dwukrotnie właściwość
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d508cc407087e481ff77e29956db7511bba81165
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916832"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Nie można utworzyć skojarzenia &lt;Nazwa skojarzenia&gt; — właściwość wymieniony dwukrotnie

Nie można utworzyć skojarzenia \<Nazwa skojarzenia >. Tę samą właściwość jest wymieniona więcej niż raz: \<właściwość name >.

Skojarzenia są zdefiniowane przez wybrany **właściwości skojarzenia** w **Edytor skojarzenia** okno dialogowe. Właściwości może być wymieniona tylko jeden raz dla każdej klasy skojarzenia.

Właściwość w komunikacie zostanie wyświetlone więcej niż jeden raz w nadrzędnym lub podrzędnym klasy **właściwości skojarzenia**.

## <a name="to-resolve-this-condition"></a>Aby rozwiązać ten problem

- Sprawdź komunikat i zanotuj właściwości określony w komunikacie.

- Kliknij przycisk **OK** aby zamknąć okno komunikatu.

- Sprawdź **właściwości skojarzenia** i Usuń zduplikowane wpisy.

- Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Porady: Tworzenie skojarzenia między klasy LINQ do SQL (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)