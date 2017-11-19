---
title: "Tworzenie i używanie zasad ewidencjonowania analizy kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b16b7e9f4dba55babfc7ad2ad90affe0ca93c508
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Tworzenie zasad ewidencjonowania analizy kodu i korzystanie z nich
Korzystając z kontroli wersji typu Team Foundation (TFVC), można utworzyć zasad analizy kodu zaewidencjonowania programu .NET Framework i projektów natywnych (C/C++) kodu w projekcie zespołowym. Zasady analizy kodu zaewidencjonowania służy do sterowania i poprawianie jakości kodu, który jest sprawdzany w bazie kodu.  
  
 Zasady przekazuje podczas lokalnej kompilacji jest aktualny i analizy kodu zostało uruchomione na najnowszych plików źródłowych. Co najmniej reguł analizy kodu, które są włączone w projekcie kodu musi zawierać te same zasady, jak te, które są zdefiniowane w zespół projektu zasad ewidencjonowania. Reguły, które zostały określone jako błędy w ustawieniach projektu zespołowego musi być także określona jako błędy w projekcie kodu  
  
> [!IMPORTANT]
>  Nie można zastosować zasad ewidencjonowania analizy kodu w projektach witryny sieci web. Można stosować do projektów aplikacji sieci web.  
  
 Tworzenie zasad ewidencjonowania analizy kodu za pomocą ustawienia projektu zespołowego z [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]. Zasady ewidencjonowania są określone i wymuszane dla projektu zespołowego, ale działa analizy kodu są konfigurowane i uruchamiania dla projektów poszczególnych kodu na komputerach rozwoju lokalnego. W tej sekcji opisano sposób określania zasad ewidencjonowania analizy kodu dla projektu zespołowego i implementowania niestandardowych zasad analizy kodu dla kodu zarządzanego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Tworzenie lub aktualizowanie standardowych zasad analizy kodu zaewidencjonowania](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Wyjaśniono również używane do ustawiania i modyfikowania zasad analizy kodu dla projektu zespołowego.  
  
 [Wdrażanie niestandardowych zasad ewidencjonowania analizy kodu dla zarządzanego kodu](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Przedstawiono kroki, które używają do tworzenia niestandardowego zestawu reguł dla zasad ewidencjonowania projektu zespołowego i synchronizowanie projekty kodu projektu zespołowego z zasadami ewidencjonowania.  
  
 [Kompatybilność wersji dla zasad ewidencjonowania analizy kodu](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Wyjaśniono kod analizy zaewidencjonowania problemy ze zgodnością między wersjami [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)].  
  
 [Porady: dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Wyjaśniono, jak dodać słów i tokenów do słownik, który odwołuje się do nazw reguł analizy kodu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Określają i wymuszają bramki jakości](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Udoskonalanie jakości kodu z zasadami ewidencjonowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)