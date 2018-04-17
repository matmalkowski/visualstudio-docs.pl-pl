---
title: Korzystanie z reguł wydajności do analizowania danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f974a6aa2aff626a72aeefdb9dddfb76ec5e8396
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="using-performance-rules-to-analyze-data"></a>Korzystanie z reguł wydajności do analizowania danych
Ostrzeżenia wydajności z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania wskazują na problemy w profilowanych aplikacji, która może spowolnić działanie programu. Ostrzeżenia może również oznaczać, że może być konieczna zmiana metody kolekcji do zbierania danych bardziej użyteczne. Ostrzeżenia wydajności są generowane automatycznie podczas sesji profilowania. Ostrzeżenia są wyświetlane w **listy błędów** okna po otwarciu pliku danych profilowania w programie Visual Studio. Z **listy błędów** okna, można znaleźć kodu źródłowego problemu i można wyświetlić szczegółowe informacje o błędzie, takie jak informacje dotyczące sposobu rozwiązania problemu. Można również wyłączyć ostrzeżenia, w których nie jest konieczne.  
  
> [!NOTE]
>  Ostrzeżenia wydajności programu profilującego wygenerowanych przez dynamicznej analizy wykonywania programu i są niezależne od ostrzeżenia analizy kodu. Kod — analiza można również generować ostrzeżenia wydajności dla zarządzanego kodu na podstawie statycznej analizy kodu źródłowego. Aby uzyskać więcej informacji, zobacz [analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) i [ostrzeżeń dotyczących wydajności](../code-quality/performance-warnings.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: wyświetlanie ostrzeżeń dotyczących wydajności](../profiling/how-to-view-performance-warnings.md)  
 Zawiera informacje o sposobie otwierania **listy błędów** okna, aby wyświetlić ostrzeżenia wydajności profilera.  
  
 [Porady: Konfigurowanie zasad wydajności](../profiling/how-to-configure-performance-rules.md)  
 Zawiera informacje o sposobie włączyć ostrzeżeń dotyczących wydajności poszczególnych lub wyłączyć.  
  
 [Zasady wydajności — odwołanie](../profiling/performance-rules-reference.md)  
 Zawiera szczegółowe informacje dotyczące profilera ostrzeżeń dotyczących wydajności