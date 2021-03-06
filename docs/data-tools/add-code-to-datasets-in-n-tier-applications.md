---
title: Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e4c5fbbbe878e14c6c88c872ece2b3d492e3ea7c
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844036"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych
Można rozszerzyć funkcjonalności zestawu danych, tworząc plik częściowej klasy dla zestawu danych i dodawanie kodu do niego (zamiast Dodawanie kodu do *DatasetName*. Plik Dataset.Designer). Klasy częściowe Włącz kod dla określonej klasy podzielony między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial) lub [klasy częściowe i metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Kod, który definiuje zestaw danych jest generowany za każdym razem, gdy zmian do definicji zestawu danych (w typizowany zestaw danych). Ten kod jest również generowany po wprowadzeniu zmian podczas wykonywania żadnych kreatora, który modyfikuje konfigurację zestawu danych. Aby zapobiec kodu usuwane podczas ponownego generowania zestawu danych, należy dodać kodu do pliku częściowej klasy zestawu danych.

Domyślnie po oddzieleniu zestawu danych i kod TableAdapter, wynik jest plik odrębny klasy w każdym projekcie. Oryginalny projekt zawiera plik o nazwie *DatasetName.Designer.vb* (lub *DatasetName.Designer.cs*) zawierający kod TableAdapter. Projekt, który jest oznaczany **projektu Dataset** właściwość istnieje plik o nazwie *DatasetName.DataSet.Designer.vb* (lub *DatasetName.DataSet.Designer.cs*) . Ten plik zawiera kod zestawu danych.

> [!NOTE]
>  Po oddzieleniu zestawów danych i TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące klasy częściowe dataset w projekcie nie będą przenoszone automatycznie. Istniejący zestaw danych klasy częściowe należy przenieść ręcznie do projektu dataset.

> [!NOTE]
>  Podczas sprawdzania poprawności kodu musi zostać dodany, typizowanego obiektu dataset udostępnia funkcje generowania <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> procedury obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [Dodawanie walidacji do warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Aby dodać kod do zestawów danych w aplikacjach warstwowych

1.  Znajdź projekt, który zawiera *XSD* pliku.

2.  Wybierz **XSD** plik, aby otworzyć zestawu danych.

3.  Kliknij prawym przyciskiem myszy tabelę danych, do której chcesz dodać kod (nazwa tabeli w pasku tytułu), a następnie wybierz **kod widoku**.

     Klasy częściowe zostanie utworzona i zostanie otwarty w edytorze kodu.

4.  Dodaj kod wewnątrz deklaracji klasy częściowej.

     W poniższym przykładzie przedstawiono umożliwiające dodawanie kodu do CustomersDataTable w NorthwindDataSet:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```
    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Zobacz także

- [Omówienie aplikacji warstwowych](../data-tools/n-tier-data-applications-overview.md)
- [Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Tworzenie i konfigurowanie adapterów TableAdapter](create-and-configure-tableadapters.md)
- [Hierarchiczna aktualizacja — Przegląd](hierarchical-update.md)
- [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)