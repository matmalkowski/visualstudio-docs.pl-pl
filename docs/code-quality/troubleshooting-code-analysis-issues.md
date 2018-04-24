---
title: Rozwiązywanie problemów związanych z analizą kodu
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9029c7be21fe02b9d6b1c4436658df74eb3c37f9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="troubleshooting-code-analysis-issues"></a>Rozwiązywanie problemów związanych z analizą kodu
Ten temat zawiera informacje dotyczące rozwiązywania problemów następujące analizy kodu programu Visual Studio.

-   [Zmiany w Visual Studio 2010 reguły zestawu są nie zostaną uwzględnione w poprzednich wersjach programu Visual Studio](#ChildRuleSetChangesInPreviousVersions)

##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Zmiany w Visual Studio 2010 reguły zestawu są nie zostaną uwzględnione w poprzednich wersjach programu Visual Studio
 Po utworzeniu zestawu reguł w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] zawierający zestaw reguł podrzędnych, zmiana zestawu reguł podrzędnych mogą nie zostać zastosowane w uruchamia analizy kodu na komputerach, które korzystają z wcześniejszych wersji programu Visual Studio. Aby rozwiązać ten problem, możesz wymusić ponowne zapisywanie adresów nadrzędnego zestawu reguł, który jest zestaw reguł, który zawiera zestaw reguł podrzędnych.

1.  Otwórz zestawu reguł nadrzędnego [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].

2.  Zmiany, takie jak dodawanie lub usuwanie reguły, a następnie Zapisz zestaw reguł.

3.  Otwórz ponownie zestaw reguł, cofnąć zmianę, a następnie zapisz ponownie zestaw reguł.

## <a name="see-also"></a>Zobacz też
 [Analiza jakości aplikacji](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md) [analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) [korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)