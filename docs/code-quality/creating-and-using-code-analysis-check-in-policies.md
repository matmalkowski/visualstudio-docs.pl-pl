---
title: "Tworzenie i używanie zasad ewidencjonowania analizy kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b7187ef8d3342ad050c66debf939e9c6a6213957
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2018
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Tworzenie zasad ewidencjonowania analizy kodu i korzystanie z nich
Korzystając z kontroli wersji typu Team Foundation (TFVC), można utworzyć zasad analizy kodu zaewidencjonowania programu .NET Framework i projektów natywnych (C/C++) kodu w projekcie zespołowym. Zasady analizy kodu zaewidencjonowania służy do sterowania i poprawianie jakości kodu, który jest sprawdzany w bazie kodu.  
  
 Zasady przekazuje podczas lokalnej kompilacji jest aktualny i analizy kodu zostało uruchomione na najnowszych plików źródłowych. Co najmniej reguł analizy kodu, które są włączone w projekcie kodu musi zawierać te same zasady, jak te, które są zdefiniowane w zespół projektu zasad ewidencjonowania. Reguły, które zostały określone jako błędy w ustawieniach projektu zespołowego musi być także określona jako błędy w projekcie kodu  
  
> [!IMPORTANT]
>  Nie można zastosować zasad ewidencjonowania analizy kodu w projektach witryny sieci web. Można stosować do projektów aplikacji sieci web.  
  
 Tworzenie zasad ewidencjonowania analizy kodu za pomocą ustawienia projektu zespołowego z [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]. Zasady ewidencjonowania są określone i wymuszane dla projektu zespołowego, ale działa analizy kodu są konfigurowane i uruchamiania dla projektów poszczególnych kodu na komputerach rozwoju lokalnego. W tej sekcji opisano sposób określania zasad ewidencjonowania analizy kodu dla projektu zespołowego i implementowania niestandardowych zasad analizy kodu dla kodu zarządzanego.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Tworzenie lub aktualizowanie standardowych zasad zaewidencjonowania analizy kodu](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Wyjaśniono również używane do ustawiania i modyfikowania zasad analizy kodu dla projektu zespołowego.  
  
 [Wdrażanie niestandardowych zasad ewidencjonowania analizy kodu dla zarządzanego kodu](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Przedstawiono kroki, które używają do tworzenia niestandardowego zestawu reguł dla zasad ewidencjonowania projektu zespołowego i synchronizowanie projekty kodu projektu zespołowego z zasadami ewidencjonowania.  
  
 [Zgodność wersji dla zasad zaewidencjonowania analizy kodu](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Wyjaśniono kod analizy zaewidencjonowania problemy ze zgodnością między wersjami [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)].  
  
 [Instrukcje: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Wyjaśniono, jak dodać słów i tokenów do słownik, który odwołuje się do nazw reguł analizy kodu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Doskonalenie jakości kodu za pomocą zasad zaewidencjonowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)