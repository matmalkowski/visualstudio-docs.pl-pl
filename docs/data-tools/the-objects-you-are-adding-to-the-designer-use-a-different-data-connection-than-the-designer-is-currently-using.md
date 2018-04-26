---
title: Obiekty, które są dodawane do projektanta, użyj innego połączenia danych niż aktualnie używa narzędzia Projektant
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 33a6083fb9e52ebdafbc827fc19666c1df9a3f7e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Obiekty, dodawanego do projektanta używają innego połączenia danych niż projektanta

Obiekty, które są dodawane do projektanta Użyj innego połączenia danych niż aktualnie używa projektanta. Czy chcesz zastąpić połączenie używane przez projektanta?

Po dodaniu elementów do [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), wszystkie elementy korzystały z jednego połączenia danych udostępnionych. (Powierzchni projektowej reprezentuje <xref:System.Data.Linq.DataContext>, który używa pojedynczego połączenia dla wszystkich obiektów na powierzchni.) Jeśli obiekt zostanie dodany do projektanta, który korzysta z połączenia danych, która różni się od połączenia danych aktualnie używane przez projektanta, zostanie wyświetlony ten komunikat. Aby rozwiązać ten problem, można zachować istniejące połączenie. Jeśli ta opcja, nie można dodać wybranego obiektu. Alternatywnie można dodać obiektu i zresetuj <xref:System.Data.Linq.DataContext> połączenia do nowego połączenia.

> [!NOTE]
> Jeśli klikniesz przycisk **tak**, klas wszystkie jednostki na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] są mapowane na nowe połączenie.

## <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Aby zastąpić istniejące połączenie połączenie używane przez wybrany obiekt

- Kliknij przycisk **Tak**.

    Wybrany obiekt jest dodawany do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], a DataContext.Connection jest ustawiona na nowe połączenie.

## <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Aby nadal korzystać z istniejącego połączenia i Anuluj dodawanie wybranego obiektu

- Kliknij przycisk **nr**.

    Akcja została anulowana. Ustaw pozostaje DataContext.Connection do istniejącego połączenia.

## <a name="see-also"></a>Zobacz także

- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
