---
title: 'Porady: Konfigurowanie analizy kodu dla projektu zarządzanego kodu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 46d41b09f0f6639195613c8a4d9a08f952c79525
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
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

    - Definiowanie niestandardowego zestawu reguł. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych zestawów reguł](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Konfigurowanie niestandardowego zestawu reguł i korzystanie z niego](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
- [Instrukcje: Konfigurowanie analizy kodu dla aplikacji internetowej ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)