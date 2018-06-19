---
title: Praca z zestawami danych w aplikacjach warstwowych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f97e0d4c0cd16fd2bc7cc8bf140a59a800a254ac
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31926118"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Praca z zestawami danych w aplikacjach warstwowych

*Aplikacje warstwowe —* są skoncentrowane na dane aplikacji, które są podzielone na kilka logicznych warstw (lub *warstw*). Innymi słowy aplikacji warstwowych jest aplikacja, która jest podzielony na wiele projektów z warstwą dostępu do danych, warstwy logiki biznesowej, a warstwą prezentacji każdego własnego projektu. Aby uzyskać więcej informacji, zobacz [N-warstwowa danych aplikacji — omówienie](../data-tools/n-tier-data-applications-overview.md).

Typizowane zbiory danych zostały rozszerzone, aby klasy TableAdapters i danych mogą być generowane w projektach dyskretnych. Zapewnia możliwość szybkiego oddzielne warstwy aplikacji i generowanie aplikacji warstwowych.

Obsługa N-warstwowa w typizowanych zbiorach danych umożliwia iteracyjne projektowanie architektura n warstwowa projektu. Eliminuje konieczność ręcznie podzielić kod na więcej niż jednym projekcie. Uruchamiane projektowania Warstwa danych przy użyciu **Projektant obiektów Dataset**. Jeśli wszystko jest gotowa do sporządzenia architektura projektowi wielowarstwowej, ustaw **projektu DataSet** właściwości zestawu danych do generowania klasy dataset w oddzielny projekt.

## <a name="reference"></a>Tematy pomocy

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Zobacz także

- [Omówienie aplikacji warstwowych](../data-tools/n-tier-data-applications-overview.md)
- [Wskazówki: Tworzenie aplikacji warstwowych](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Dodawanie kodu do adapterów TableAdapter w aplikacjach n-warstwowych](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Dodawanie kodu do zestawów danych w aplikacjach n-warstwowych](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Dodawanie walidacji do n-warstwowego zestawu danych](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Rozdzielanie zestawów danych i adapterów TableAdapter do różnych projektów](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md)
- [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Tworzenie i konfigurowanie TableAdapters](../data-tools/create-and-configure-tableadapters.md)
- [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)