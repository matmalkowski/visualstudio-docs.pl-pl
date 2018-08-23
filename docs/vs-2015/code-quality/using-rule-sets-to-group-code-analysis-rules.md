---
title: Korzystanie z zestawów reguł do grupowania reguł analizy kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ae7374ae6b713fe7fa1911cdcce3effa600482b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682304"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Korzystanie z zestawów reguł do grupowania reguł analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [przy użyciu zestawów reguł do grupowania reguł analizy kodu](https://docs.microsoft.com/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules).  
  
Podczas konfigurowania analizy kodu w programie [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], lub [!INCLUDE[vsPro](../includes/vspro-md.md)], można wybrać z listy wbudowanych Microsoft *zestawów reguł*. Zestaw reguł jest logicznym grupowaniem reguł analizy kodu, które identyfikują docelowe problemy i określone warunki. Na przykład można zastosować zestaw reguł, który jest przeznaczony do skanowania kodu w poszukiwaniu publicznie dostępne interfejsy API lub można zastosować zestaw reguł, który zawiera tylko minimalne zalecane reguły kodu. Można także zastosować zestaw reguł, który zawiera wszystkie reguły.  
  
 Można dostosować reguły ustawiona przez dodanie lub usunięcie reguł lub zmieniając reguły pojawią się w **lista błędów** okno jako ostrzeżenia lub błędy. Dostosowane zestawy reguł mogą spełnić potrzeby konkretnego środowiska do tworzenia oprogramowania. Po dostosowaniu zestawu reguł strona zestawu reguł dostarcza narzędzia do wyszukiwania i filtrowania pomocne w przetwarzaniu.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Uzyskaj praktyczne:** użyj narzędzi analizy kodu, aby określić niestandardową regułę ustawioną znajdowania i rozwiązywania problemów w prostej aplikacji .NET Framework.|-   [Wskazówki: Konfigurowanie i używanie niestandardowego zestawu reguł](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**Konfigurowanie analizy kodu dla projektu:** wybierz istniejący zestaw reguł dla projektu, witryny sieci Web lub rozwiązania.|-   [Porady: Konfigurowanie analizy kodu dla projektu kodu zarządzanego](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Porady: Konfigurowanie analizy kodu dla aplikacji sieci Web platformy ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Porady: określanie zestawów reguł dla wielu projektów w rozwiązaniu](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**Dostosuj zestaw reguł:** Określ reguły do zastosowania w projekcie.|-   [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**Zrozumienie wbudowane zestawy reguł:** Wyświetl reguły analizy kodu, które tworzą wbudowane zestawy reguł.|-   [Odwołanie do zestawu reguł analizy kodu](../code-quality/code-analysis-rule-set-reference.md)|  
|**Integracja analizy kodu z Team Foundation Server:** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] warunkowo zasady umożliwiają zespołom programistycznym na upewnienie się, że wszystkie ewidencje kodu spełniają wspólny zestaw standardów analizy kodu.|-   [Porady: synchronizowanie zestawów reguł projektu kodu z zasadami ewidencjonowania projektu zespołowego](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|



