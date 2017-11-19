---
title: "Analiza kodu dla zarządzanego kodu — omówienie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eebc25b344e603cb66546db6d9179067d5995496
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="code-analysis-for-managed-code-overview"></a>Analiza kodu dla zarządzanego kodu — Omówienie
Analiza kodu dla kodu zarządzanego analizuje zarządzanych zestawów i raportuje informacje o zestawy, takie jak naruszenia programowania i reguły projektowania określonymi w wytycznych projektowych programu Microsoft .NET Framework.  
  
 Narzędzie do analizy reprezentuje kontroli, którą wykonuje jako komunikaty ostrzegawcze podczas analizy. Komunikaty ostrzegawcze identyfikację problemów odpowiednich programowania i projektowania oraz, jeśli jest to możliwe, dostawy informacji na temat sposobu rozwiązania problemu.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)  
 Deweloper można wykonać analizy kodu w projekcie automatycznie lub uruchomić ją ręcznie.  
  
 Aby uruchomić kod — analiza za każdym razem w przypadku kompilowania projektu, zaznacz **Włącz analizę kodu podczas kompilacji (definiuje stała CODE_ANALYSIS)** na stronie właściwości projektu. Aby uzyskać więcej informacji, zobacz [porady: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Do ręczne przeprowadzanie analizy kodu w projekcie, na **Analizuj** menu, kliknij przycisk **Uruchom analizę kodu na***ProjectName*. Aby uzyskać więcej informacji, zobacz [porady: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## <a name="rule-sets"></a>Zestawy reguł  
 Reguły analizy kodu dla zarządzanego kodu są podzielone na *zestawów reguł*. Można użyć jednego z zestawów reguł standard Microsoft lub można utworzyć niestandardowego zestawu reguł do spełnienia konkretna potrzeba użycia. Aby uzyskać więcej informacji, zobacz [przy użyciu zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## <a name="in-source-suppression"></a>W pomijanie źródła  
 Często jest przydatne do wskazywania ostrzeżenie nie dotyczy. Informuje deweloperów oraz inne osoby, które może przejrzeć kod później, że ostrzeżenie został zbadana i następnie pominięte lub ignorowane.  
  
 W źródłowej pomijanie ostrzeżeń jest implementowane za pośrednictwem atrybutów niestandardowych. Aby wyłączyć ostrzeżenia, Dodaj atrybut `SuppressMessage` do kodu źródłowego, jak pokazano w poniższym przykładzie:  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 Aby uzyskać więcej informacji, zobacz [Pomiń ostrzeżenia przy użyciu atrybutu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Uruchom jako część zasad ewidencjonowania analizy kodu  
 Jako organizacji można wymagać, że wszystkie zaewidencjonowania spełniają określone zasady. W szczególności chcesz upewnij się, że należy wykonać te zasady:  
  
-   Nie było żadnych błędów kompilacji w kodzie zostały zaewidencjonowane.  
  
-   Kod — analiza został uruchomiony jako część ostatniej kompilacji.  
  
 Można to zrobić, określając zasady ewidencjonowania. Aby uzyskać więcej informacji, zobacz [udoskonalanie jakości kodu z zasadami ewidencjowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Integracja kompilacji Team  
 Zintegrowane funkcje systemu kompilacji służy do uruchamiania narzędzia analizy jako część procesu kompilacji. Aby uzyskać więcej informacji, zobacz [kompilowania aplikacji](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Porady: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)