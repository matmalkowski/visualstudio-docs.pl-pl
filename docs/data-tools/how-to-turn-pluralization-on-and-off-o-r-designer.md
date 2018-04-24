---
title: 'Porady: Włączanie określania liczby mnogiej i wyłączanie (Projektant O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 34e0c0f57b7da90a78166057762cb0a5c0e015e1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Porady: Włączanie określania liczby mnogiej i wyłączanie (Projektanta obiektów relacyjnych)
Domyślnie podczas przeciągania obiektów bazy danych, które mają nazwy kończące się s lub IE z **Eksploratora serwera**/**Eksploratora bazy danych** na [składnika LINQ to SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), nazw wygenerowanych klas jednostek nie zostaną zmienione w liczbie mnogiej na liczbę pojedynczą. To jest bardziej przedstawiać fakt, że klasa jednostki wystąpień mapuje pojedynczy rekord danych. Na przykład dodawania tabeli klientów do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] wyniki w klasie jednostki o nazwie odbiorcy, ponieważ klasa będą przechowywane dane tylko jednego odbiorcy.

> [!NOTE]
>  Pluralizacja jest domyślnie tylko w języku angielskim wersji programu Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Aby włączyć określania liczby mnogiej lub wyłączyć

1.  Na **narzędzia** menu, kliknij przycisk **opcje**.

2.  W **opcje** okna dialogowego rozwiń **narzędzi bazy danych**.

    > [!NOTE]
    >  Wybierz **Pokaż wszystkie ustawienia** Jeśli **narzędzi bazy danych** węzeł nie jest widoczne.

3.  Kliknij przycisk **Projektanta obiektów relacyjnych**.

4.  Ustaw **Pluralizację nazw** do **włączone** = **False** można ustawić [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] tak, aby nie zmienia nazwy klasy.

5.  Ustaw **Pluralizację nazw** do **włączone** = **True** do stosowania reguł do określania liczby mnogiej do nazwy klasy obiektów dodanych do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)