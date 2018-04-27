---
title: Analiza kodu dla C/C++ — Omówienie
ms.date: 04/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ea576ba794350e6cee6b20f8ef9adb62f82a9c51
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="code-analysis-for-cc-overview"></a>Analiza kodu dla C/C++ — omówienie

Narzędzie do analizy kodu C/C++ zawiera informacje o możliwych wad kodu źródłowego C/C++. Typowe błędy kodowania zgłoszone przez narzędzie obejmują przepełnienia buforu, niezainicjowanej pamięci, wyłuskań wskaźnika o wartości null i przecieków pamięci i zasobów. Narzędzie można również uruchomić kontroli względem [C++ podstawowe wskazówki](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)

Narzędzie do analizy kodu jest w pełni zintegrowana w programie Visual Studio IDE.

Podczas procesu tworzenia ostrzeżenia dla kodu źródłowego generowane są wyświetlane na liście błędów. Można nawigować do kodu źródłowego, który spowodował ostrzeżenia i można wyświetlić dodatkowe informacje na temat przyczyny i możliwe rozwiązania problemu.

## <a name="command-line-support"></a>Obsługę wiersza polecenia

Można także użyć narzędzia analizy w wierszu polecenia, jak pokazano w poniższym przykładzie:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 wersji 15.7 i nowszych** można uruchomić narzędzie z wiersza polecenia z dowolnego systemu kompilacji, w tym CMake.

## <a name="pragma-support"></a>Obsługa #pragma

Można użyć `#pragma` dyrektywy Traktuj ostrzeżenia jako błędy; Włącz lub wyłącz ostrzeżenia i pomijanie ostrzeżeń dla poszczególnych wierszach kodu. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie właściwości analizy kodu dla projektów C/C++](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Obsługa adnotacji

Adnotacje poprawić analizy kodu. Adnotacje zawierają dodatkowe informacje o warunkach przed i po o parametrów funkcji i zwracanych typów. Aby uzyskać więcej informacji, zobacz [porady: Określanie dodatkowych informacji kodu za pomocą __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Uruchom narzędzie do analizy jako część zasad ewidencjonowania

Możesz wymagać, że wszystkie źródła kodu zaewidencjonowane spełniają określone zasady. W szczególności chcesz upewnij się, że krokiem ostatniej kompilacji lokalnego uruchomienia analizy. Aby uzyskać więcej informacji na temat włączania zasad analizy kodu zaewidencjonowania zobacz [tworzenie i przy użyciu zasad analizy kodu zaewidencjonowania](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Integracja kompilacji Team

Można użyć zintegrowane funkcje systemu kompilacji, aby uruchomić narzędzie do analizy kodu na potrzeby [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] proces kompilacji. Aby uzyskać więcej informacji, zobacz [kompilacji i wydania](/vsts/build-release/index).

## <a name="see-also"></a>Zobacz także

- [Szybki Start: Analiza kodu dla C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Wskazówki: Analizowanie kodu C++ pod względem wad](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Analiza kodu C/C++ — ostrzeżenia](code-analysis-for-c-cpp-warnings.md)
- [Korzystanie z kontrolerów podstawowych wytycznych dotyczących języka C++](using-the-cpp-core-guidelines-checkers.md)
- [C++ podstawowe wskazówki dotyczące sprawdzania odwołania](code-analysis-for-cpp-corecheck.md)
- [Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analiza jakości sterowników za pomocą narzędzi analizy kodu](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Analiza kodu dla sterowników ostrzeżenia](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
