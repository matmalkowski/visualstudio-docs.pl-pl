---
title: Zapisz dane z obiektu do bazy danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 641b598eb855fb1f2c3a7ca38d966630fbac15bb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924720"
---
# <a name="save-data-from-an-object-to-a-database"></a>Zapisz dane z obiektu do bazy danych
Można zapisać danych w obiektach do bazy danych przez przekazanie wartości z obiektu do jednego z TableAdapter DBDirect — metody (na przykład `TableAdapter.Insert`). Aby uzyskać więcej informacji, zobacz [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

 Aby zapisać dane z kolekcji obiektów, pętli kolekcji obiektów (na przykład pętli dla następnego), a wysyłania wartości dla każdego obiektu w bazie danych przy użyciu jednej z TableAdapter DBDirect — metody.

 Domyślnie DBDirect — metody są tworzone na obiekt TableAdapter, które mogą być uruchamiane bezpośrednio w bazie danych. Te metody można wywołać bezpośrednio i nie wymagają <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> obiektów do uzgodnienia zmiany w celu wysyłania aktualizacji do bazy danych.

> [!NOTE]
>  Podczas konfiguracji TableAdapter, główne zapytanie musi umożliwi zebranie informacji dla DBDirect — metody ma zostać utworzony. Na przykład jeśli TableAdapter jest skonfigurowany do zapytania danych z tabeli, która nie ma kolumny klucza podstawowego zdefiniowane, nie generuje ona DBDirect — metody.

|TableAdapter DBDirect — metoda|Opis|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Dodaje nowe rekordy do bazy danych i umożliwia przekazywanie w poszczególnych kolumn wartości jako parametrów metody.|
|`TableAdapter.Update`|Aktualizuje istniejące rekordy w bazie danych. `Update` Metoda przyjmuje wartości oryginalnej i nowych kolumn jako parametry metody. Oryginalne wartości są używane do lokalizowania rekordzie oryginalnym, a nowe wartości są używane do zaktualizowania rekordu.<br /><br /> `TableAdapter.Update` Metody służy również do uzgodnienia zmiany w zestawie danych w bazie danych, wykonując <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, lub tablicę <xref:System.Data.DataRow>określane jako parametry metody.|
|`TableAdapter.Delete`|Usuwa istniejące rekordy z bazy danych na podstawie oryginalnej wartości kolumny przekazane jako parametry metody.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Aby zapisać nowe rekordy z obiektu do bazy danych

-   Utwórz rekordy przez przekazanie wartości do `TableAdapter.Insert` metody.

     Poniższy przykład tworzy nowy rekord klienta `Customers` tabeli przez przekazanie wartości w `currentCustomer` do obiektu `TableAdapter.Insert` metody.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Aby zaktualizować istniejące rekordy z obiektu do bazy danych

-   Modyfikowania rekordów przez wywołanie metody `TableAdapter.Update` metody, przekazując nowe wartości w celu zaktualizowania rekordu, przekazując oryginalne wartości można znaleźć rekordu.

    > [!NOTE]
    >  Obiekt musi być oryginalnych wartości w celu przekazania ich do `Update` metody. W tym przykładzie użyto właściwości z `orig` prefiksu do przechowywania wartości początkowe.

     Poniższy przykład aktualizacji istniejącego rekordu w `Customers` tabeli przez przekazanie nowych i oryginalnych wartości w `Customer` do obiektu `TableAdapter.Update` metody.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

### <a name="to-delete-existing-records-from-a-database"></a>Aby usunąć istniejące rekordy z bazy danych

-   Usuwanie rekordów przez wywołanie metody `TableAdapter.Delete` — metoda i przekazywanie oryginalne wartości można znaleźć rekordu.

    > [!NOTE]
    >  Obiekt musi być oryginalnych wartości w celu przekazania ich do `Delete` metody. W tym przykładzie użyto właściwości z `orig` prefiksu do przechowywania wartości początkowe.

     Poniższy przykład usuwa rekord na podstawie `Customers` tabeli przez przekazanie oryginalnych wartości w `Customer` do obiektu `TableAdapter.Delete` metody.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework
 Musi mieć uprawnienia do wykonania wybranego INSERT, UPDATE lub DELETE w tabeli w bazie danych.

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)