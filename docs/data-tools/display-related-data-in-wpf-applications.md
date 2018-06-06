---
title: Wyświetlanie powiązanych danych w aplikacjach WPF
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 38c25cc1631529895a11af566298ce22930a2e6a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746549"
---
# <a name="display-related-data-in-wpf-applications"></a>Wyświetlanie powiązanych danych w aplikacjach WPF
W niektórych aplikacjach można pracować z danymi, które pochodzą z wielu tabel lub jednostek, które są powiązane ze sobą w relacji nadrzędny podrzędny. Na przykład można wyświetlić siatkę, który wyświetla klientów z `Customers` tabeli. Po wybraniu określonego klienta innego siatce są wyświetlane zlecenia dla tego klienta z powiązanego `Orders` tabeli.

Możesz utworzyć formantów powiązanych z danymi, które wyświetlanie powiązanych danych przez przeciąganie elementów z **źródeł danych** okna Projektanta WPF.

## <a name="to-create-controls-that-display-related-records"></a>Aby utworzyć formanty, które wyświetlają powiązanych rekordów

1. Na **danych** menu, kliknij przycisk **Pokaż źródeł danych** otworzyć **źródeł danych** okna.

2. Kliknij przycisk **Dodaj nowe źródło danych**i wykonaj **konfiguracji źródła danych** kreatora.

3. Otwórz projektanta WPF i upewnij się, że projektant zawiera kontener, który jest prawidłowy miejsca docelowego dla elementów w **źródeł danych** okna.

     Aby uzyskać więcej informacji na temat prawidłowy miejsc docelowych, zobacz [kontrolki powiązania WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

4. W **źródeł danych** okna, rozwiń węzeł, który reprezentuje tabeli nadrzędnej lub obiekt w relacji. Tabela nadrzędna lub obiekt znajduje się na "jeden" w relacji jeden do wielu.

5. Przeciągnij z węzła nadrzędnego (lub wszystkie elementy w węźle nadrzędnym) **źródeł danych** okna na prawidłową miejsca docelowego w projektancie.

     Program Visual Studio generuje XAML tworzący nowe formanty powiązane z danymi dla każdego elementu, który przeciągania. XAML dodaje również nowe <xref:System.Windows.Data.CollectionViewSource> dla tabeli nadrzędnej lub obiekt, aby zasoby miejsca docelowego. Dla niektórych źródeł danych programu Visual Studio generuje kod, aby załadować dane do tabeli nadrzędnej lub obiektu. Aby uzyskać więcej informacji, zobacz [kontrolki powiązania WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. W **źródeł danych** okna, zlokalizuj podrzędnych tabeli lub obiektu. Tabele podrzędne pokrewnych i obiektów są wyświetlane jako węzły można rozwijać w dolnej części listy węzła nadrzędnego danych.

7. Przeciągnij węzeł podrzędny (lub wszystkie elementy w węźle podrzędnym) z **źródeł danych** okna na prawidłową miejsca docelowego w projektancie.

     Program Visual Studio generuje XAML, która tworzy nowe formanty powiązane z danymi dla każdego z elementów przeciąganych. XAML dodaje również nowe <xref:System.Windows.Data.CollectionViewSource> obiektu do zasobów obiektu docelowego upuszczania lub tabeli podrzędnej. Nowy <xref:System.Windows.Data.CollectionViewSource> jest powiązana z właściwością tabeli nadrzędnej lub obiekt, który właśnie został przeciągnięty do projektanta. Dla niektórych źródeł danych programu Visual Studio generuje kod, aby załadować dane do tabeli podrzędnej lub obiektu.

     Na poniższym rysunku pokazano pokrewny **zamówień** spis **klientów** tabeli w elemencie dataset w **źródeł danych** okna.

     ![Relacja przedstawiający okno źródeł danych](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>Zobacz także

- [Powiązanie formantów WPF z danymi w Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Tworzenie tabel wyszukiwania w aplikacjach WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)