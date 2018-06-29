---
title: 'Porady: Zmienianie zwracanego typu metody DataContext (Projektant O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5c67d6dea4c64e858acdab25ecc4a6cede6bf262
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089360"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Porady: Zmienianie zwracanego typu metody DataContext (Projektanta obiektów relacyjnych)
Zwracany typ <xref:System.Data.Linq.DataContext> — metoda (utworzone na podstawie procedury składowanej lub funkcji) różni się w zależności od tego, gdzie porzucić procedury składowanej lub funkcji w **Projektanta obiektów relacyjnych**. Jeśli musisz porzucić elementu bezpośrednio na istniejącej klasy jednostki, <xref:System.Data.Linq.DataContext> metodę, która ma zwracany typ klasy jednostka jest tworzony (Jeśli schemat danych zwróconych przez procedura składowana lub funkcja odpowiada kształtu klasy jednostka). Jeśli element jest upuścić nad pustym obszarem **Projektanta obiektów relacyjnych**, <xref:System.Data.Linq.DataContext> metodę zwracającą automatycznie wygenerowany typ jest tworzony. Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu do okienka metody. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz go i kliknij **typu zwracanego** właściwości w **właściwości** okna.

> [!NOTE]
>  Nie można przywrócić <xref:System.Data.Linq.DataContext> metod, które mają zwracany typ. ustawione na klasę jednostki, aby zwracany typ generowane automatycznie za pomocą **właściwości** okna. Aby przywrócić <xref:System.Data.Linq.DataContext> metody, aby przywrócić automatycznie wygenerowany typ, musisz przeciągnąć oryginalny obiekt bazy danych na **Projektanta obiektów relacyjnych** ponownie.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Aby zmienić zwracanego typu metody DataContext z typu automatycznie generowanej klasy jednostki

1.  Wybierz <xref:System.Data.Linq.DataContext> metody w okienku metody.

2.  Wybierz **typu zwracanego** w **właściwości** okna, a następnie wybierz dostępne jednostki klasy w **typu zwracanego** listy. Jeśli klasa żądanej jednostki nie jest na liście, dodaj go do lub utwórz go w **Projektanta obiektów relacyjnych** ją dodać do listy.

3.  Zapisz *.dbml* pliku.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Aby zmienić zwracany typ metody DataContext z klasy jednostki do automatycznie generowanej typu

1.  Wybierz <xref:System.Data.Linq.DataContext> metody w **metody** okienku i usuń go.

2.  Przeciągnij obiekty z **Eksploratora serwera** lub **Eksploratora bazy danych** na pustym obszarem **Projektanta obiektów relacyjnych**.

3.  Zapisz *.dbml* pliku.

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metody DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md)
- [Porady: tworzenie metodę DataContext mapowane na procedury składowane i funkcje (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)