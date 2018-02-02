---
title: "Analiza kodu dla C/C++ — omówienie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2261921e4266f1b58ed31650ac1ff1bb7c028942
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="code-analysis-for-cc-overview"></a>Analiza kodu dla C/C++ — omówienie

Narzędzie do analizy kodu C/C++ informacje dla deweloperów o możliwych wady ich kodu źródłowego C/C++. Przepełnienia buforów, które nie zostały zainicjowane pamięci obejmują typowe błędy kodowania zgłoszone przez narzędzie, wyłuskań wskaźnika o wartości null i przecieków pamięci i zasobów.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)  
 Aby umożliwić fizycznych deweloperom korzystać z narzędzia do analizy, jego jest w pełni zintegrowana w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Podczas procesu tworzenia ostrzeżenia dla kodu źródłowego generowane są wyświetlane na liście błędów. Można nawigować do kodu źródłowego, który spowodował ostrzeżenia i można wyświetlić dodatkowe informacje na temat przyczyny i możliwe rozwiązania problemu.  
  
## <a name="pragma-support"></a>#pragma pomocy technicznej  
 Deweloperzy mogą używać `#pragma` dyrektywy Traktuj ostrzeżenia jako błędy; Włącz lub wyłącz ostrzeżenia i pomijanie ostrzeżeń dla poszczególnych wierszach kodu. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie właściwości analizy kodu dla projektów C/C++ ](how-to-set-code-analysis-properties-for-c-cpp-projects.md).  
  
## <a name="annotation-support"></a>Obsługa adnotacji  
 Adnotacje poprawić analizy kodu. Adnotacje zawierają dodatkowe informacje o warunkach przed i po o parametrów funkcji i zwracanych typów. Aby uzyskać więcej informacji, zobacz [porady: Określanie dodatkowych informacji kodu za pomocą __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Uruchom narzędzie do analizy jako część zasad ewidencjonowania  
 Możesz wymagać, że wszystkie źródła kodu zaewidencjonowane spełniają określone zasady. W szczególności chcesz upewnij się, że krokiem ostatniej kompilacji lokalnego uruchomienia analizy. Aby uzyskać więcej informacji na temat włączania zasad analizy kodu zaewidencjonowania zobacz [tworzenie i przy użyciu zasad analizy kodu zaewidencjonowania](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Integracja kompilacji Team  
 Można użyć zintegrowane funkcje systemu kompilacji, aby uruchomić narzędzie do analizy kodu na potrzeby [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] proces kompilacji. Aby uzyskać więcej informacji, zobacz [kompilacji i wydania](/vsts/build-release/index).  
  
## <a name="command-line-support"></a>Obsługa wiersza polecenia  
 Oprócz pełnej integracji środowiska programistycznego programiści mogą również wykorzystać narzędzie do analizy w wierszu polecenia, jak pokazano w poniższym przykładzie:  
  
 `C:\>cl /analyze Sample.cpp`

## <a name="see-also"></a>Zobacz także

[Analiza jakości sterowników za pomocą narzędzi analizy kodu](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)  
[Analiza kodu dla sterowników ostrzeżenia](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)