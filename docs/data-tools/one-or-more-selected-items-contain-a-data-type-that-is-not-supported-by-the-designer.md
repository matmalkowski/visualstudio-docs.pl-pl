---
title: Co najmniej jeden wybrany element zawiera typ danych, który nie jest obsługiwany przez projektanta | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 966adc7a4114c54479c0ad8c52a604e0fb5d3380
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Co najmniej jeden wybrany element zawiera typ danych, który nie jest obsługiwany przez projektanta
Co najmniej jeden z elementów przeciągnięte z **Eksploratora serwera**/**Eksploratora bazy danych** na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] zawiera dane typu, który nie jest obsługiwany przez [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] na przykład [Typy danych zdefiniowane przez użytkownika CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Utwórz widok, w którym jest oparty na żądaną tabeli i nie zawiera nieobsługiwany typ danych.  
  
2.  Przeciągnij widoku z **Eksploratora serwera**/**Eksploratora bazy danych** do projektanta.  
  
## <a name="see-also"></a>Zobacz także
[Komunikaty narzędzia Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)