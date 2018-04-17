---
title: Zestawów reguł analizy kodu w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 04/02/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8db113ef3e86fce0a3359a98a7641c47b67ae0c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Zestawy reguł używany do grupowania reguł analizy kodu

Podczas konfigurowania analizy kodu w programie Visual Studio, można wybrać z listy wbudowanych *zestawów reguł*. Zestaw reguł ma zastosowanie do projektu i jest grupą kodu reguł analizy, które identyfikują docelowe problemy i określonych warunków dla tego projektu. Na przykład można zastosować zestaw reguł przeznaczony do skanowania pod kątem publicznie dostępnych interfejsach API kodu lub jedynie minimalnej zalecane reguły kodu. Można także zastosować dla zestawu reguł, który zawiera wszystkie reguły.

Można dostosować reguły ustawioną przez dodanie lub usunięcie zasady lub zmieniając wag reguły są wyświetlane jako ostrzeżeń lub błędów w **listy błędów**. Dostosowane zestawy reguł mogą spełnić potrzeby konkretnego środowiska do tworzenia oprogramowania. Podczas dostosowywania zestawu reguł, Edytor zestaw reguł zawiera wyszukiwania i filtrowania narzędzia pomocne w procesie.

## <a name="rule-set-format"></a>Format zestawu reguł

Zestaw reguł jest określona w formacie XML w *.ruleset* pliku. Zasady, które składają się z Identyfikatora i *akcji*, są pogrupowane według Identyfikatora analizator i przestrzeni nazw w pliku.

Zawartość XML *.ruleset* pliku wygląda podobnie do następującej:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> Możliwe jest łatwiejsze [Edytuj zestaw reguł](../code-quality/working-in-the-code-analysis-rule-set-editor.md) w graficznym **Edytor ustawić reguły** niż ręcznie.

Dla zestawu dla projektu określono za pomocą reguł `CodeAnalysisRuleSet` właściwość w pliku projektu programu Visual Studio. Na przykład:

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>Zobacz także

- [Informacje o zestawie reguł analizy kodu](../code-quality/rule-set-reference.md)
