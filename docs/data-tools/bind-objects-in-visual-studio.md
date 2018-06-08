---
title: Powiązanie obiektów w programie Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a8b86f7159e1e8c8e54c7045709d61b5f6fa7d60
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844709"
---
# <a name="bind-objects-in-visual-studio"></a>Powiązanie obiektów w programie Visual Studio
Program Visual Studio udostępnia czasu projektowania narzędzi do pracy z obiektami niestandardowych jako źródło danych w aplikacji. Jeśli chcesz przechowywać dane z bazy danych w obiekcie powiązanemu z kontrolek interfejsu użytkownika, zalecane podejście jest użycie programu Entity Framework do generowania klasy lub klas. Programu Entity Framework auto generuje wszystkich umożliwiającego śledzenie zmian kodu, co oznacza, że zmiany wprowadzone w lokalnych obiektów automatycznie są zachowywane w bazie danych w przypadku wywołania AcceptChanges w obiekcie DbSet. Aby uzyskać więcej informacji, zobacz [dokumentację programu Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
>  Podejścia do powiązania obiektu w tym artykule należy rozważyć tylko, jeśli aplikacja jest już oparta na zestawów danych. Można również użyć tych sposobów Jeśli już znasz z zestawami danych, a dane, które będą przetwarzać tabelarycznych i nie jest zbyt złożony lub zbyt duży. Przykład nawet prostszy, dotyczące ładowania danych bezpośrednio do obiektów z wykorzystaniem DataReader i ręczne aktualizowanie interfejsu użytkownika bez wiązania z danymi, zobacz [tworzenia prostej aplikacji danych przy użyciu pakietu ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Wymagania dotyczące obiektów
 Jedynym wymaganiem dla niestandardowych obiektów do pracy z danymi narzędzi projektowania w programie Visual Studio jest, że obiekt wymaga co najmniej jedną właściwość publiczną.

 Ogólnie rzecz biorąc niestandardowe obiekty nie wymagają żadnych określonych interfejsów, konstruktorów ani atrybutów, które mają działać jako źródło danych dla aplikacji. Jednak jeśli chcesz przeciągnąć obiekt z **źródeł danych** okna do powierzchni projektu, aby utworzyć formant powiązany z danymi i jeśli obiekt implementuje <xref:System.ComponentModel.ITypedList> lub <xref:System.ComponentModel.IListSource> interfejsu, obiekt musi mieć domyślnego Konstruktor. W przeciwnym razie program Visual Studio nie może utworzyć wystąpienia obiektu źródła danych i wyświetla komunikaty o błędach, gdy użytkownik przeciąga element powierzchnię projektu.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Przykłady użycia niestandardowych obiektów jako źródła danych
 Gdy istnieją niezliczonych metody implementacji logiki aplikacji, podczas pracy z obiektami jako źródła danych, bazy danych dla bazy danych SQL są kilka standardowych operacji, które można uprościć przy użyciu obiektów TableAdapter generowanych przez program Visual Studio. Ta strona wyjaśniono, jak wdrożyć te standardowe procesy przy użyciu TableAdapters. Nie ma ona jako przewodnik tworzenia niestandardowych obiektów. Na przykład będzie zazwyczaj wykonaj następujące operacje standardowe niezależnie od konkretnej implementacji obiektów lub logiki aplikacji:

-   Ładowanie danych do obiektów (zazwyczaj z bazy danych).

-   Tworzenie typu kolekcji obiektów.

-   Dodawanie obiektów do i usuwanie obiektów z kolekcji.

-   Dane obiektu są wyświetlane użytkownikom w formularzu.

-   Zmiana/edytowanie danych w obiekcie.

-   Zapisywanie danych z obiektów w bazie danych.

### <a name="load-data-into-objects"></a>Ładowanie danych do obiektów
 Na przykład ładowania danych do obiektów przy użyciu TableAdapters. Domyślnie TableAdapters są tworzone dwa typy metod pobierania danych z bazy danych i wypełnić tabel danych.

-   `TableAdapter.Fill` Metody wypełnia istniejącej tabeli danych z danymi zwracanymi.

-   `TableAdapter.GetData` Metoda zwraca nową tabelę danych zawierają dane.

 Najprostszym sposobem załadować niestandardowych obiektów danych jest wywołać `TableAdapter.GetData` — metoda, za pomocą kolekcji wierszy w tabeli zwracanych danych w pętli i wypełnić każdego obiektu z wartości w każdym wierszu. Można utworzyć `GetData` metodę zwracającą tabelę danych wypełnione dla dowolnego zapytania dodane do TableAdapter.

> [!NOTE]
>  Visual Studio nazw zapytań TableAdapter `Fill` i `GetData` domyślnie, ale można zmienić nazwy na dowolną nazwę prawidłowej metody.

 Poniższy przykład przedstawia sposób pętli wierszy w tabeli danych i wypełnić obiektu z danych:

 [!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Tworzenie typu kolekcji obiektów
 Można utworzyć klasy kolekcji dla obiektów, lub użyj typu kolekcje, które są automatycznie udostępniane przez [BindingSource — składnik](/dotnet/framework/winforms/controls/bindingsource-component).

 Podczas tworzenia kolekcji niestandardowej klasy dla obiektów, zalecamy, aby dziedziczyć z <xref:System.ComponentModel.BindingList%601>. Ta klasa ogólna zapewnia funkcje do administrowania kolekcji, a także możliwość pozyskiwania zdarzenia, które wysyłania powiadomień do infrastruktury powiązanie danych w formularzach systemu Windows.

 Kolekcja automatycznie generowane w <xref:System.Windows.Forms.BindingSource> używa <xref:System.ComponentModel.BindingList%601> dla jego typu kolekcji. Jeśli aplikacja nie wymaga dodatkowych funkcji, można zachować kolekcji w ciągu <xref:System.Windows.Forms.BindingSource>. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.BindingSource.List%2A> właściwość <xref:System.Windows.Forms.BindingSource> klasy.

> [!NOTE]
>  Jeśli kolekcja wymaga funkcji nie udostępnia podstawową implementację <xref:System.ComponentModel.BindingList%601>, należy utworzyć kolekcję niestandardową, w razie potrzeby można dodać do tej klasy.

 Poniższy kod przedstawia sposób tworzenia klasy kolekcji jednoznacznie `Order` obiektów:

 [!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Dodawanie do kolekcji obiektów
 Dodać obiekty do kolekcji, wywołując `Add` metody klasy kolekcji niestandardowej lub z <xref:System.Windows.Forms.BindingSource>.


> [!NOTE]
>  `Add` — Metoda jest dostarczany automatycznie kolekcji niestandardowych, gdy dziedziczyć z <xref:System.ComponentModel.BindingList%601>.

 Poniższy kod przedstawia sposób dodawania obiektów typu kolekcji w <xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

 Poniższy kod przedstawia sposób dodawania obiektów typu kolekcji, która dziedziczy <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
>  W tym przykładzie `Orders` kolekcji jest właściwością `Customer` obiektu.

 [!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Usuwanie obiektów z kolekcji
 Usuwanie obiektów z kolekcji, wywołując `Remove` lub `RemoveAt` metody klasy kolekcji niestandardowej lub z <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
>  `Remove` i `RemoveAt` kolekcji niestandardowych automatycznie udostępniono metody, gdy dziedziczyć z <xref:System.ComponentModel.BindingList%601>.

 Poniższy kod przedstawia sposób zlokalizować i usuwania obiektów z typu kolekcji w <xref:System.Windows.Forms.BindingSource> z <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> metody:

 [!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Wyświetl dane obiektu dla użytkowników
 Do wyświetlania danych w obiektach do użytkowników, Utwórz obiekt źródła danych przy użyciu **konfiguracji źródła danych** kreatora, a następnie przeciągnij na formularzu z indywidualne właściwości lub cały obiekt **źródeł danych**okna.

### <a name="modify-the-data-in-objects"></a>Modyfikowanie danych w obiektach
 Aby edytować dane w niestandardowych obiektów, które są powiązane z danymi do formantów formularzy systemu Windows, po prostu edytować danych w formancie powiązane (lub bezpośrednio w właściwości obiektu). Powiązanie danych architektura aktualizuje dane w obiekcie.

 Jeśli aplikacja wymaga śledzenia zmian i stopniowych obu proponowanych zmian do ich oryginalnych wartości, należy zaimplementować tę funkcję w modelu obiektu. Przykłady tego, jak tabele danych śledzenie pracy proponowanych, zobacz <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, i <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Zapisywanie danych w obiektach w bazie danych
 Zapisywanie danych w bazie danych przez przekazanie wartości z obiektu do TableAdapter DBDirect — metody.

 Program Visual Studio tworzy DBDirect — metody, które mogą być wykonywane bezpośrednio w bazie danych. Te metody nie wymagają obiektów DataSet lub DataTable.

|TableAdapter DBDirect — metoda|Opis|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Dodaje nowe rekordy w bazie danych, co umożliwia przekazywanie wartości poszczególnych kolumn jako parametry metody.|
|`TableAdapter.Update`|Aktualizuje istniejące rekordy w bazie danych. Metoda aktualizacji przyjmuje wartości oryginalnej i nowych kolumn jako parametry metody. Oryginalne wartości są używane do lokalizowania rekordzie oryginalnym, a nowe wartości są używane do zaktualizowania rekordu.<br /><br /> `TableAdapter.Update` Metody służy również do uzgodnienia zmiany w zestawie danych w bazie danych, wykonując <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, tablica lub <xref:System.Data.DataRow>określane jako parametry metody.|
|`TableAdapter.Delete`|Usuwa istniejące rekordy z bazy danych na podstawie oryginalnej wartości kolumny przekazane jako parametry metody.|

 Aby zapisać dane z kolekcji obiektów, pętli kolekcji obiektów (np. przy użyciu pętli dla dalej). Wyślij wartości dla każdego obiektu w bazie danych za pomocą TableAdapter DBDirect — metody.

 Poniższy przykład przedstawia użycie `TableAdapter.Insert` DBDirect metody w celu dodania nowego klienta bezpośrednio do bazy danych:

 [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Zobacz także

- [Powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)