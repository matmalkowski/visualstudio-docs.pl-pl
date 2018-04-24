---
title: Wybrane połączenie używa dostawcy nieobsługiwanej bazy danych
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2f4d2ce764f4824fdcff897c1dab542a53f80e0f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Wybrane połączenie używa dostawcy nieobsługiwanej bazy danych

Ten komunikat jest wyświetlany, gdy przeciągnij elementy, które nie korzystają z dostawcy danych programu .NET Framework dla programu SQL Server z **Eksploratora serwera**/**Eksploratora bazy danych** na [LINQ do SQL Narzędzia programu Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Obsługuje tylko połączenia danych, które używają dostawcy programu .NET Framework dla programu SQL Server. Tylko połączenia programu Microsoft SQL Server lub plik bazy danych programu Microsoft SQL Server są prawidłowe.

Aby rozwiązać ten problem, należy dodać tylko elementy z połączenia danych, które używają dostawcy danych programu .NET Framework dla programu SQL Server do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

## <a name="see-also"></a>Zobacz także

- <xref:System.Data.SqlClient>
- [Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
