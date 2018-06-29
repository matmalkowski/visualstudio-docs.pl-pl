---
title: 'Porady: Włączanie określania liczby mnogiej i wyłączanie (Projektant O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0a2d2e44efc284c38cfc450833839776effb9936
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089386"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Porady: Włączanie określania liczby mnogiej i wyłączanie (Projektanta obiektów relacyjnych)
Domyślnie podczas przeciągania obiektów bazy danych, które mają nazwy kończące się s lub IE z **Eksploratora serwera** lub **Eksploratora bazy danych** na [narzędzi LINQ do SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), nazw wygenerowanych klas jednostek są zmieniane w liczbie mnogiej do pojedynczej. To jest bardziej przedstawiać fakt, że klasa jednostki wystąpień mapuje pojedynczy rekord danych. Na przykład dodać `Customers` do tabeli **Projektanta obiektów relacyjnych** powoduje klasę jednostki o nazwie `Customer` ponieważ klasa będą przechowywane dane tylko jednego odbiorcy.

> [!NOTE]
>  Pluralizacja jest domyślnie tylko w języku angielskim wersji programu Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Aby włączyć określania liczby mnogiej lub wyłączyć

1.  Na **narzędzia** menu, kliknij przycisk **opcje**.

2.  W **opcje** okna dialogowego rozwiń **narzędzi bazy danych**.

    > [!NOTE]
    >  Wybierz **Pokaż wszystkie ustawienia** Jeśli **narzędzi bazy danych** węzeł nie jest widoczne.

3.  Kliknij przycisk **Projektanta obiektów relacyjnych**.

4.  Ustaw **Pluralizację nazw** do **włączone** = **False** można ustawić **Projektanta obiektów relacyjnych** tak, aby nie zmienia nazwy klas .

5.  Ustaw **Pluralizację nazw** do **włączone** = **True** do stosowania reguł do określania liczby mnogiej do nazwy klasy obiektów dodanych do **obiektów relacyjnych Projektant**.

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)