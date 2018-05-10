---
title: Visual Studio tools danych dla platformy .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 2b7fc572541e0c2f0f5aa04c6e676d1e2913ff9f
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio tools danych dla platformy .NET

Visual Studio i .NET Framework razem zapewniają szeroką gamę interfejsu API oraz obsługę łączenie z bazami danych, modelowania danych w pamięci i wyświetlanie danych w interfejsie użytkownika narzędzia. Klasy .NET Framework, które zapewniają funkcje dostępu do danych są określane jako [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, wraz z danymi, narzędzia programu Visual Studio została zaprojektowana głównie w celu obsługi relacyjnych baz danych i XML. Te dni wielu dostawców bazy danych NoSQL, lub osób trzecich, oferują dostawcy ADO.NET.

[Oprogramowanie .NET core](/dotnet/core/) obsługuje ADO.NET, z wyjątkiem zestawów danych i powiązanych typów. Jeśli są przeznaczonych dla platformy .NET Core i wymagają warstwy mapowania relacyjnego obiektu (ORM), użyj [Entity Framework Core](/ef/core/).

Na poniższym diagramie przedstawiono uproszczony widok podstawowej architektury:

![Architektura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Typowy przepływ pracy

Typowy przepływ pracy jest to:

1. Zainstaluj rozwoju lub testowej bazy danych na komputerze lokalnym. Zobacz [instalowanie systemów bazy danych, narzędzia i próbki](../data-tools/installing-database-systems-tools-and-samples.md). Jeśli używasz usługi Azure danych, ten krok nie jest konieczne.

2. Testuj połączenie bazy danych (lub usługa lub pliku lokalnego) w programie Visual Studio. Zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).

3. (Opcjonalnie) Użyj narzędzi, aby wygenerować i skonfigurować nowy model. Modele oparte na platformie Entity Framework są domyślnego zalecenia dla nowych aplikacji. Model, niezależnie od jednej z nich, jest źródło danych, która aplikacja współdziała z. Model logicznie znajduje się pomiędzy bazy danych lub usług i aplikacji. Zobacz [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md).

4. Przeciągnij źródła danych z **źródeł danych** okna na formularze systemu Windows, ASP.NET lub Windows Presentation Foundation powierzchnię projektu do generowania kodu wiązania danych wyświetlanych danych użytkownika w taki sposób, który określisz. Zobacz [powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Dodaj niestandardowy kod dla czynności, takich jak reguły biznesowe, wyszukiwanie i sprawdzanie poprawności danych, lub aby skorzystać z funkcji niestandardowych, który ujawnia podstawowej bazy danych.

Można pominąć krok 3 i programowania aplikacji .NET w celu wydawania poleceń, bezpośrednio do bazy danych, a nie za pomocą modelu. W takim przypadku można znaleźć odpowiednią dokumentacją: [ADO.NET](/dotnet/framework/data/adonet/index). Należy pamiętać, że nadal służy Kreator konfiguracji źródła danych i projektantów do generowania kodu wiązania danych podczas wypełniania obiektów w pamięci, a następnie utworzyć powiązania danych kontrolek interfejsu użytkownika do tych obiektów.

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)