---
title: Kod — analiza kodu dla kodu zarządzanego w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 8209e17985ef7f9924fc677b91b5cfe539977cb9
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="overview-of-code-analysis-for-managed-code"></a>Omówienie analizy kodu dla zarządzanego kodu

Visual Studio 2017 analizuje kodu zarządzanego na dwa sposoby: z starszych *FxCop* analizy statycznej zarządzanych zestawów i z platformą kompilatora .NET *analizatorów*. W tym temacie omówiono FxCop statycznej analizy kodu. Aby dowiedzieć się więcej na temat analizowania kodu za pomocą analizatorów platformy kompilatora .NET, zobacz [analizatorów omówienie Roslyn](../code-quality/roslyn-analyzers-overview.md).

Analiza kodu dla kodu zarządzanego analizuje zarządzanych zestawów i raportuje informacje o zestawy, takie jak naruszenia programowania i reguły projektowania określonymi w wytycznych projektowych programu Microsoft .NET Framework.

Narzędzie do analizy reprezentuje kontroli, którą wykonuje jako komunikaty ostrzegawcze podczas analizy. Komunikaty ostrzegawcze identyfikację problemów odpowiednich programowania i projektowania oraz, jeśli jest to możliwe, dostawy informacji na temat sposobu rozwiązania problemu.

## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)

Ręcznie lub automatycznie, można uruchomić analizy kodu w projekcie.

Aby uruchomić kod — analiza za każdym razem w przypadku kompilowania projektu, zaznacz **Włącz analizę kodu podczas kompilacji** na stronie właściwości projektu. Aby uzyskać więcej informacji, zobacz [porady: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Aby ręczne przeprowadzanie analizy kodu w projekcie, na pasku menu wybierz **Analizuj** > **uruchamiania analizy kodu** > **Uruchom analizę kodu na <project>** . Aby uzyskać więcej informacji, zobacz [porady: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Zestawy reguł

Reguły analizy kodu dla zarządzanego kodu są podzielone na *zestawów reguł*. Można użyć jednego z zestawów reguł standard Microsoft lub można utworzyć niestandardowego zestawu reguł do spełnienia konkretna potrzeba użycia. Aby uzyskać więcej informacji, zobacz [przy użyciu zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

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
> Jeśli migrujesz projektu do programu Visual Studio 2017 może nagle być skierowany utrudnione numerem ostrzeżenia analizy kodu. Jeśli nie jest gotowa na rozwiązanie ostrzeżeń, aby tymczasowo wyłączyć analizy kodu, otwieranie stron właściwości projektu (**projektu** > ***projektu* właściwości...** ) i przejdź do **analizy kodu** kartę. Anuluj wybór **Włącz analizę kodu podczas kompilacji**, a następnie ponownie skompiluj projekt. Alternatywnie można wybrać różne, mniejszym zestawu reguł jest w celu uruchomienia kodu. Pamiętaj, aby włączyć analizę kodu na powrót po osiągnięciu gotowości do napraw ostrzeżenia.

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
