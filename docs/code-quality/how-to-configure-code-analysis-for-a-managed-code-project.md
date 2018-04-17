---
title: Konfigurowanie analizy kodu w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 04/04/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 177aba466d89c88c898ea1273240d18a8b1f0f4f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Porady: konfigurowanie analizy kodu dla projektu zarządzanego kodu

W programie Visual Studio, można wybrać z listy analizy kodu *zestawów reguł* do zastosowania do projektu zarządzanego kodu. Domyślny zestaw reguł jest *reguł zalecanych Minimum Microsoft*. Można stosować inną regułę ustawiony jako projekt lub do wszystkich projektów w rozwiązaniu.

> [!TIP]
> Aby uzyskać informacje o sposobie konfigurowania zestawu reguł dla aplikacji sieci Web ASP.NET, zobacz [porady: Konfigurowanie analizy kodu dla aplikacji sieci Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Aby skonfigurować zestaw reguł dla projektu .NET Framework

1. Otwórz **analizy kodu** kartę na stronach właściwości projektu. Można to zrobić w jeden z następujących sposobów:

   - W **Eksploratora rozwiązań**, wybierz projekt. Na pasku menu wybierz **Analizuj** > **Konfigurowanie analizy kodu** > **dla \<projectname >**.

   - Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**, a następnie wybierz **analizy kodu** kartę.

1. W **konfiguracji** i **platformy** listy, wybierz platformę kompilacji konfiguracji i obiekt docelowy.

1. Aby uruchomić kod — analiza za każdym razem, gdy projekt jest utworzony przy użyciu wybranej konfiguracji, wybierz **Włącz analizę kodu podczas kompilacji** pole wyboru. Można również uruchomić kod — analiza ręcznie, wybierając **Analizuj** > **uruchamiania analizy kodu** > **Uruchom analizę kodu na \<projectname >**.

1. Domyślnie analizy kodu nie raportuje ostrzeżenia z kodu, który jest automatycznie generowany przez zewnętrznych narzędzi. Aby wyświetlić ostrzeżenia z wygenerowanego kodu, wyczyść **Pomijaj wyniki z wygenerowanego kodu** pole wyboru.

    > [!NOTE]
    > Ta opcja nie odrzuca błędy analizy kodu i ostrzeżeń z wygenerowanego kodu podczas błędy i ostrzeżenia są wyświetlane w formularzach i szablony. Jednocześnie można wyświetlać i obsługa kodu źródłowego dla formularza lub szablonu, bez konieczności jego zastąpienie.

1. W **Uruchom ten zestaw reguł** listy, wykonaj jedną z następujących czynności:

    - Wybierz zestaw reguł, którego chcesz używać.

    - Wybierz  **\<Przeglądaj >** znaleźć zestaw istniejącej reguły niestandardowe, których nie ma na liście.

    - Zdefiniuj [niestandardowego zestawu reguł](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Określ zestawy reguł dla wielu projektów w rozwiązaniu

Domyślnie są przypisane projektów zarządzanych rozwiązania *reguł zalecanych Minimum Microsoft* zestawu reguł analizy kodu. Można zmienić zestawów reguł, które są przypisane do projektów rozwiązania w **właściwości** okno dialogowe dla rozwiązania.

1. Otwórz rozwiązanie w programie Visual Studio.

2. Na **Analizuj** menu, wybierz opcję **Konfigurowanie analizy kodu dla rozwiązania**.

3. Jeśli to konieczne, rozwiń węzeł **wspólne właściwości**, a następnie wybierz **ustawienia analizy kodu**.

4. Można określić zestawu reguł dla jednego lub więcej projektów:

    - Aby określić zestaw reguł dla pojedynczego projektu, wybierz nazwę projektu.

    - Aby określić zestaw reguł dla wielu projektów, przytrzymaj **Ctrl** i zaznacz nazwy projektu.

    - Aby określić wszystkie projekty w rozwiązaniu, przytrzymaj **Shift** i kliknij na liście projektu.

5. Wybierz **zestawu reguł** pole projektu, a następnie wybierz nazwę reguły, ustaw chcesz zastosować.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Konfigurowanie analizy kodu dla aplikacji internetowej ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)