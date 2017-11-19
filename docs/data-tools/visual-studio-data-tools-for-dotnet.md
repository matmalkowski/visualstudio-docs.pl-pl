---
title: Visual Studio tools danych dla platformy .NET | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 6b48b16d33c62c2d0ca96eb1d55ce22682458029
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio tools danych dla platformy .NET
Visual Studio i .NET Framework razem zapewniają szeroką gamę interfejsu API oraz obsługę łączenie z bazami danych, modelowania danych w pamięci i wyświetlanie danych w interfejsie użytkownika narzędzia. Klasy .NET Framework, które zapewniają funkcje dostępu do danych są określane jako [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx.aspx). ADO.NET, wraz z danymi, narzędzia programu Visual Studio był pierwotnie przeznaczony głównie do obsługi relacyjnych baz danych i XML. Te dni wielu dostawców bazy danych NoSQL, lub osób trzecich, oferują dostawcy ADO.NET.  
  
[Oprogramowanie .NET core](https://www.dotnetfoundation.org/netcore) obsługuje ADO.NET, z wyjątkiem zestawów danych i powiązanych typów. Jeśli są przeznaczonych dla platformy .NET Core i wymagają warstwy mapowania relacyjnego obiektu (ORM), użyj [Entity Framework Core](https://docs.microsoft.com/ef/core/).  
  
Na poniższym diagramie przedstawiono uproszczony widok podstawowej architektury:  
  
![Architektura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata Diagram architektury ADO.NET")  
  
Typowy przepływ pracy jest to:  
  
1.  Zainstaluj rozwoju lub testowej bazy danych na komputerze lokalnym. Zobacz [instalowanie systemów bazy danych, narzędzia i próbki](../data-tools/installing-database-systems-tools-and-samples.md). Jeśli używasz usługi Azure danych, ten krok nie jest konieczne.  
  
2.  Testuj połączenie bazy danych (lub usługa lub pliku lokalnego) w programie Visual Studio. Zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
3.  (Opcjonalnie) Użyj narzędzi, aby wygenerować i skonfigurować nowy model. Modele oparte na platformie Entity Framework są domyślnego zalecenia dla nowych aplikacji. Model, niezależnie od jednej z nich, jest źródło danych, która aplikacja współdziała z. Model logicznie znajduje się pomiędzy bazy danych lub usług i aplikacji.  Zobacz [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md).  
  
4.  Przeciągnij źródła danych z **źródeł danych** okna na formularze systemu Windows, ASP.NET lub Windows Presentation Foundation powierzchnię projektu do generowania kodu wiązania danych wyświetlanych danych użytkownika w taki sposób, który określisz. Zobacz [powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
5.  Dodaj niestandardowy kod dla czynności, takich jak reguły biznesowe, wyszukiwanie i sprawdzanie poprawności danych, lub aby skorzystać z funkcji niestandardowych, który ujawnia podstawowej bazy danych.  
  
Można pominąć krok 3 i programowania aplikacji .NET w celu wydawania poleceń, bezpośrednio do bazy danych, a nie za pomocą modelu. W takim przypadku można znaleźć odpowiednią dokumentacją: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx.aspx). Należy pamiętać, że nadal służy Kreator konfiguracji źródła danych i projektantów do generowania kodu wiązania danych podczas wypełniania obiektów w pamięci, a następnie utworzyć powiązania danych kontrolek interfejsu użytkownika do tych obiektów.
  
## <a name="see-also"></a>Zobacz także
[Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)