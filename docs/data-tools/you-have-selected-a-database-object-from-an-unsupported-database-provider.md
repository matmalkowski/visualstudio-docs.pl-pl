---
title: Po wybraniu obiektu bazy danych od dostawcy nieobsługiwanej bazy danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5dfb475cdb1b63e4dfcaaebcda4b5d2dc3a7f070
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Po wybraniu obiektu bazy danych od dostawcy nieobsługiwanej bazy danych
Projektant obiektów relacyjnych obsługuje tylko dostawcy danych programu .NET Framework dla programu SQL Server (<xref:System.Data.SqlClient>). Mimo że można kliknąć **OK** i kontynuować pracę z obiektami od dostawców nieobsługiwanej bazy danych, może wystąpić nieoczekiwane zachowanie w czasie wykonywania.  
  
> [!NOTE]
>  Obsługiwane są tylko połączenia danych, które używają dostawcy danych programu .NET Framework dla programu SQL Server.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Kliknij przycisk **OK**.

   Projektowanie klas jednostek, które mapują na połączenie, które używa dostawcy nieobsługiwanej bazy danych można kontynuować. Mogą wystąpić nieoczekiwane zachowanie, gdy używasz nieobsługiwanej bazy danych dostawcy.  
  
     —lub—  
  
- Kliknij przycisk **anulować**.

   Akcja została zatrzymana. Utwórz lub użyj połączenie danych za pomocą dostawcy .NET Framework dla programu SQL Server.  
  
## <a name="see-also"></a>Zobacz także
[Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)