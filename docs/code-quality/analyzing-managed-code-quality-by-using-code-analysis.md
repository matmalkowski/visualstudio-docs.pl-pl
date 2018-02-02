---
title: "Analiza jakości zarządzanego kodu za pomocą analizy kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 2008ac649302d87cc2d45274de3fdb1981aa571d
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2018
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analiza jakości zarządzanego kodu za pomocą analizy kodu
Narzędzi analizy kodu w programie Visual Studio służy do odnajdywania potencjalnych problemów w kodzie, takich jak dostęp do danych niezabezpieczone, naruszeń użycia i problemy związane z projektem. Kod — analiza działa na .NET Framework, natywnego (C i C++) i bazy danych aplikacji. Analiza kodu dla kodu zarządzanego organizuje reguły w *zestawów reguł* kierowanych określonego kodowania problemy.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Typowe zadania|Zawartość pomocnicza|  
|------------------|------------------------|  
|**Pobierz przećwiczenia:** podstawy analizy kodu modyfikując wady prostej aplikacji .NET Framework.|-   [Wskazówki: Analizowanie zarządzanego kodu pod względem wad kodu](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Konfigurowanie analizy kodu dla projektu:** reguły dla zarządzanego kodu są podzielone na zestawów reguł, które odnoszą się do określonych obszarów, takich jak zabezpieczeń i projektowania. Można użyć jednej z firmy Microsoft, standardowe reguły Ustawia lub Utwórz swój własny.|-   [Analiza kodu dla kodu zarządzanego ― omówienie](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Tłumienie ostrzeżeń przy użyciu atrybutu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Przeprowadzanie analizy kodu:** można określić analizy kodu automatycznego wykonywania zawsze konfiguracji projektu jest wbudowana i analizy kodu można uruchomić ręcznie na projekt.|-   [Porady: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Porady: ręczne przeprowadzanie analizy kodu](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analizowanie wyników analizy kodu:** kod analizy ostrzeżenia i błędy są wyświetlane w oknie analizy kodu. Można wybrać pojawi się ostrzeżenie lub błąd tytuł, aby wyświetlić dodatkowe informacje na temat tego ostrzeżenia, a do wyświetlenia i zaznacz wiersz kodu źródłowego uruchamiająca reguły. Można wybrać identyfikator ostrzeżenia, aby wyświetlić szczegółowe informacje w bibliotece MSDN, który zawiera informacje i przykłady sposobu rozwiązania problemu.|-   [Porady: wyświetlanie defektów kodu zarządzanego](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Analiza kodu dla zarządzanego kodu — ostrzeżenia](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Ostrzeżenia dzięki CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Metody anonimowe i analiza kodu](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Integracja analizy kodu z cyklem życia z programowanie:** zasady ewidencjonowania w [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] zespoły deweloperów Włącz, aby upewnić się, że wszystkie kodu zaewidencjonowania spełnia wspólny zbiór standardów analizy kodu. Tworzenie elementu roboczego dla naruszeniem reguł analizy kodu jest proste procedury, które można wykonywać w oknie Lista błędów.|-   [Udoskonalanie jakości kodu z zasadami ewidencjonowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Porady: synchronizowanie zestawu reguł projektu kodu z zasadami ewidencjonowania projektu zespołowego](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Porady: Tworzenie elementu roboczego dla defektu kodu zarządzanego](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|