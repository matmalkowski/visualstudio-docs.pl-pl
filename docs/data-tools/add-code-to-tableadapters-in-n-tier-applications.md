---
title: Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e5a9aad4aaecb629f5860fadf56e35a55455be63
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844098"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych
Pozwala na poszerzanie funkcjonalności TableAdapter, tworząc plik częściowej klasy dla TableAdapter oraz dodawanie kodu do niego (zamiast Dodawanie kodu do *DatasetName.DataSet.Designer* pliku). Klasy częściowe Włącz kod dla określonej klasy podzielony między wiele plików fizycznych. Aby uzyskać więcej informacji, zobacz [częściowe](/dotnet/visual-basic/language-reference/modifiers/partial) lub [partial (typ)](/dotnet/csharp/language-reference/keywords/partial-type).

Kod, który definiuje TableAdapter jest generowany za każdym razem, gdy zmian w TableAdapter w zestawie danych. Ten kod jest również wygenerowany podczas wprowadzania zmian podczas wykonywania żadnych kreatora, który modyfikuje konfiguracji TableAdapter. Aby zapobiec usunięciu podczas ponownego generowania TableAdapter kodu, Dodaj kod do pliku częściowej klasy TableAdapter.

Domyślnie po oddzieleniu zestawu danych i kod TableAdapter, wynik jest plik odrębny klasy w każdym projekcie. Oryginalny projekt zawiera plik o nazwie *DatasetName.Designer.vb* (lub *DatasetName.Designer.cs*) zawierający kod TableAdapter. Projekt, który jest oznaczany **projektu Dataset** właściwość zawiera plik o nazwie *DatasetName.DataSet.Designer.vb* (lub *DatasetName.DataSet.Designer.cs*) który zawiera kod zestawu danych.

> [!NOTE]
>  Po oddzieleniu zestawów danych i TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące klasy częściowe dataset w projekcie nie zostaną automatycznie przeniesione. Istniejące klasy częściowy zestaw danych należy przenieść ręcznie do projektu dataset.

> [!NOTE]
> Zestaw danych udostępnia funkcje generowania <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging> procedury obsługi zdarzeń, gdy potrzebny jest sprawdzania poprawności. Aby uzyskać więcej informacji, zobacz [Dodawanie walidacji do warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Aby dodać kod użytkownika do TableAdapter w aplikacji warstwowych

1.  Znajdź projekt, który zawiera *XSD* pliku.

2.  Kliknij dwukrotnie *XSD* plik, aby otworzyć **Projektant obiektów Dataset**.

3.  Kliknij prawym przyciskiem myszy obiekt TableAdapter, który chcesz dodać kod, a następnie wybierz **kod widoku**.

     Klasy częściowe zostanie utworzona i zostanie otwarty w edytorze kodu.

4.  Dodaj kod wewnątrz deklaracji klasy częściowej.

5.  W poniższym przykładzie pokazano kod w celu dodania `CustomersTableAdapter` w `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Zobacz także

- [Omówienie aplikacji warstwowych](../data-tools/n-tier-data-applications-overview.md)
- [Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Tworzenie i konfigurowanie adapterów TableAdapter](create-and-configure-tableadapters.md)
- [Hierarchiczna aktualizacja — Przegląd](hierarchical-update.md)
