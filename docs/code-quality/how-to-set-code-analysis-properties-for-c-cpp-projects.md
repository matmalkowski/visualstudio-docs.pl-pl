---
title: 'Porady: Ustawianie właściwości analizy kodu dla projektów C/C++ | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 89671da363d6079ad7a81dc41f1c6f82b713d32d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Porady: ustawianie właściwości analizy kodu dla projektów C/C++
Można skonfigurować reguły używane przez narzędzie do analizy kodu do analizowania kodu w każdej konfiguracji projektu. Ponadto można kierować analizy kodu w celu pominięcia ostrzeżenia z kodu, który został wygenerowany i dodany do projektu za pomocą narzędzia innych firm.  
  
## <a name="code-analysis-property-page"></a>Strona właściwości analizy kodu  
 **Analizy kodu** strony właściwości zawiera wszystkie ustawienia konfiguracji analizy kodu dla projektu. Aby otworzyć stronę właściwości analizy kodu dla projektu w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**. Następnie rozwiń węzeł **właściwości konfiguracji** i wybierz **analizy kodu** kartę.  
  
## <a name="project-configuration-and-platform"></a>Konfiguracja projektu i platforma  
 **Konfiguracji** listy i **platformy** listy umożliwiają zastosowanie ustawień analizy kodu różnych kombinacji konfiguracji i platformy inny projekt. Na przykład można kierować tworzy analizy kodu, aby zastosować jeden zestaw reguł do projektu do debugowania i inny zestaw w wersji kompilacji.  
  
## <a name="enabling-code-analysis"></a>Włączenie analizy kodu  
 Określenie, czy włączyć analizy kodu dla projektu, wybierając **Włącz kod — analiza C/C++ podczas kompilacji**. W połączeniu z **konfiguracji** listy, można na przykład zdecydujesz się wyłączyć analizy kodu dla kompilacji do debugowania i włącz go w wersji kompilacji.  
  
 Jeśli projekt zawiera kod zarządzany, możesz zdecydować, czy włączać lub wyłączać analizy kodu, wybierając **Włącz analizę kodu podczas kompilacji**.  
  
 Kod — analiza zaprojektowano w celu poprawy jakości kodu i uniknąć typowych problemów. Dlatego zastanów się, czy wyłączyć analizy kodu. Lepiej wyłączyć zestawy reguł lub poszczególnych reguł, które nie mają zastosowania do projektu.  
  
## <a name="generated-code"></a>Wygenerowany kod  
 Deweloperzy często narzędzia ułatwia szybkie opracowywanie aplikacji. Te narzędzia można wygenerować kodu, który zostanie dodany do projektu. Możesz wyświetlić naruszenia reguły, które wykrywa analizy kodu w wygenerowanym kodzie. Jednak nie można je wyświetlić, jeśli nie chcesz zachować kod.  
  
 **Pomijaj wyniki z wygenerowany kod** pole wyboru na **ogólne** strona właściwości umożliwia wybranie, czy mają być wyświetlane ostrzeżenia analizy kodu z kodu zarządzanego, który jest generowany przez narzędzie innej firmy .  
  
## <a name="rule-sets"></a>Zestawy reguł  
 Jeśli projekt zawiera kod zarządzany, możesz wybrać zasady do zastosowania w analizy kodu, wybierając zestaw z reguł **Uruchom ten zestaw reguł** listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Analiza kodu C/C++ — ostrzeżenia](../code-quality/code-analysis-for-c-cpp-warnings.md)