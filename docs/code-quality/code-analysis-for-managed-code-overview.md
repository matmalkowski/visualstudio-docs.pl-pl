---
title: Analiza kodu dla kodu zarządzanego w programie Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b7b992dadb703cf1c4f73830324e9934d7525645
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920460"
---
# <a name="overview-of-code-analysis-for-managed-code"></a>Omówienie analizy kodu dla zarządzanego kodu

Visual Studio 2017 analizuje kodu zarządzanego na dwa sposoby: z starszych *FxCop* analizy statycznej zarządzanych zestawów i z platformą kompilatora .NET *analizatorów*. W tym temacie omówiono FxCop statycznej analizy kodu. Aby dowiedzieć się więcej na temat analizowania kodu za pomocą analizatorów platformy kompilatora .NET, zobacz [analizatorów omówienie Roslyn](../code-quality/roslyn-analyzers-overview.md).

Analiza kodu dla kodu zarządzanego analizuje zarządzanych zestawów i raportuje informacje o zestawy, takie jak naruszenia programowania i reguły projektowania określonymi w wytycznych projektowych programu Microsoft .NET Framework.

Narzędzie do analizy reprezentuje kontroli, którą wykonuje jako komunikaty ostrzegawcze podczas analizy. Komunikaty ostrzegawcze identyfikację problemów odpowiednich programowania i projektowania oraz, jeśli jest to możliwe, dostawy informacji na temat sposobu rozwiązania problemu.

## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)

Ręcznie lub automatycznie, można uruchomić analizy kodu w projekcie.

Aby uruchomić kod — analiza za każdym razem w przypadku kompilowania projektu, zaznacz **Włącz analizę kodu podczas kompilacji** na stronie właściwości projektu. Aby uzyskać więcej informacji, zobacz [porady: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Aby ręczne przeprowadzanie analizy kodu w projekcie, na pasku menu wybierz **Analizuj** > **uruchamiania analizy kodu** > **Uruchom analizę kodu na \<projektu >**.

## <a name="rule-sets"></a>Zestawy reguł

Reguły analizy kodu dla zarządzanego kodu są podzielone na [zestawów reguł](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Można użyć jednej z zestawów reguł standardowe firmy Microsoft, lub możesz [Tworzenie niestandardowego zestawu reguł](../code-quality/how-to-create-a-custom-rule-set.md) do zrealizowania konkretna potrzeba użycia.

## <a name="suppress-warnings"></a>Pomijanie ostrzeżeń

Często jest przydatne do wskazywania ostrzeżenie nie dotyczy. Informuje deweloperów oraz inne osoby, które może przejrzeć kod później, że ostrzeżenie został zbadana i następnie pominięte lub ignorowane.

Pomijanie w źródła ostrzeżeń jest implementowane za pośrednictwem atrybutów niestandardowych. Aby wyłączyć ostrzeżenia, Dodaj atrybut `SuppressMessage` do kodu źródłowego, jak pokazano w poniższym przykładzie:

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Aby uzyskać więcej informacji, zobacz [tłumienie ostrzeżeń](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Jeśli migrujesz projektu do programu Visual Studio 2017 może nagle być skierowany z dużą liczbą ostrzeżenia analizy kodu. Jeśli nie są gotowe do napraw ostrzeżenia i chcesz stać się wydajni od razu, możesz *linii bazowej* stanu analizy projektu. Z **Analizuj** menu, wybierz opcję **Uruchom analizę kodu i Pomiń aktywne problemy**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Uruchom jako część zasad ewidencjonowania analizy kodu

Jako organizacji można wymagać, że wszystkie zaewidencjonowania spełniają określone zasady. W szczególności chcesz upewnij się, że należy wykonać te zasady:

- Nie ma żadnych błędów kompilacji w kodzie zostały zaewidencjonowane.

- Kod — analiza jest uruchomiony jako część ostatniej kompilacji.

Można to zrobić, określając zasady ewidencjonowania. Aby uzyskać więcej informacji, zobacz [udoskonalanie jakości kodu z zasadami ewidencjowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integracja kompilacji Team

Zintegrowane funkcje systemu kompilacji służy do uruchamiania narzędzia analizy jako część procesu kompilacji. Aby uzyskać więcej informacji, zobacz [kompilacji i wydania (VSTS)](/vsts/build-release/index).

## <a name="see-also"></a>Zobacz także

- [Omówienie analizatorów Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Porady: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
