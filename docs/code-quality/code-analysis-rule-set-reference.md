---
title: "Odwołanie zestawu reguł analizy kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0bc2b01641c6f6b333ef5323a60672818cc5e7b3
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2018
---
# <a name="code-analysis-rule-set-reference"></a>Odwołanie zestawu reguł analizy kodu

Po skonfigurowaniu analizy kodu dla kodu zarządzanego projektów programu Visual Studio jest wyświetlana lista wbudowanych *zestawów reguł*. Można użyć jednego z zestawów reguł standard lub zestawu reguł do wymagań projektu można dostosować.

## <a name="available-rule-sets"></a>Zestawy dostępne reguły

W poniższej tabeli przedstawiono domyślne zestawy reguł:

|||
|-|-|
|[Zestaw reguł Wszystkie reguły](../code-quality/all-rules-rule-set.md)|Ten zestaw reguł zawiera wszystkie reguły. Uruchomienie tego zestawu reguł może spowodować dużą liczbę ostrzeżeń. Użyj tego zestawu reguł do uzyskać kompleksowy przegląd wszystkich problemów w kodzie. To może pomóc w podjęciu decyzji, które reguły ściślejszych zestawów są najbardziej odpowiednie do uruchamiania dla projektów.|
|[Zestaw podstawowych reguł poprawności dla kodu zarządzanego](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Te reguły dotyczą błędów logicznych i typowych pomyłek popełnianych przy używaniu framework interfejsów API. Należy dołączyć ten zestaw, aby rozszerzyć listę ostrzeżeń zgłaszanych przez minimalny reguł zalecanych reguł.|
|[Zestaw podstawowych reguł wytycznych projektowych dla kodu zarządzanego](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Te reguły dotyczą wymuszania najlepszych rozwiązań, aby kod był łatwy do zrozumienia i użycia. Obejmują tej reguły, jeśli projekt zawiera kod biblioteki lub jeśli chcesz wymusić najlepsze rozwiązania dotyczące kodu łatwego w utrzymaniu.|
|[Zestaw rozszerzonych reguł poprawności dla kodu zarządzanego](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Te reguły rozszerzają podstawowe reguły poprawności w celu zmaksymalizowania wykorzystania błędów użycia logiki i framework, które są zgłaszane. Dodatkowy nacisk jest kładziony na określone scenariusze, takie jak aplikacje COM interop i przenośnych. Należy rozważyć dołączenie tego zestawu, jeśli jeden z tych scenariuszy dotyczy projektu lub w celu znalezienia dodatkowych problemów w projekcie reguł.|
|[Zestaw rozszerzonych reguł wytycznych projektowych dla kodu zarządzanego](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Te reguły rozszerzają reguły wskazówek dotyczących projektowania podstawowych, aby zmaksymalizować zgłaszanych problemów użytecznością i utrzymaniem. Dodatkowy nacisk jest kładziony na wskazówki dotyczące nazewnictwa. Należy rozważyć dołączenie tego zestawu, jeśli projekt zawiera kod biblioteki lub jeśli chcesz wymuszenia najwyższych standardów dotyczące pisania kodu za reguł.|
|[Zestaw reguł globalizacji dla kodu zarządzanego](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Te reguły dotyczą problemów, które uniemożliwiają danych w aplikacji poprawne wyświetlanie, gdy są używane w różnych językach, ustawień regionalnych i kultur. Obejmują tej reguły, jeśli aplikacja jest lokalizowana lub globalizowana.|
|[Zarządzane Minimum reguły dla zarządzanego kodu](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Te reguły dotyczą najpoważniejszych problemów w kodzie, dla których analiza kodu jest najbardziej dokładna. Te reguły są niewielka liczba i są przeznaczone do uruchamiania tylko w ograniczonym wersje programu Visual Studio. Użyj elementu MinimumRecommendedRules.ruleset w innych wersjach programu Visual Studio.|
|[Zarządzany zalecany zestaw reguł dla kodu zarządzanego](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Te reguły dotyczą najpoważniejszych problemów w kodzie, w tym potencjalnych luk w zabezpieczeniach, awarii aplikacji i inne ważne błędy logiki i projektowania. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów.|
|[Mieszany minimalny zestaw reguł](../code-quality/mixed-minimum-rules-rule-set.md)|Te reguły dotyczą najpoważniejszych problemów w projektach C++ obsługujących środowisko uruchomieniowe języka wspólnego, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów C++ obsługujących środowisko uruchomieniowe języka wspólnego.|
|[Mieszany zalecany zestaw reguł](../code-quality/mixed-recommended-rules-rule-set.md)|Te reguły dotyczą najczęstszych i najpoważniejszych problemów w projektach C++ obsługujących środowisko uruchomieniowe języka wspólnego, w tym potencjalnych luk w zabezpieczeniach, awarii aplikacji i inne ważne błędy logiki i projektowania. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów C++ obsługujących środowisko uruchomieniowe języka wspólnego. |
|[Natywny minimalny zestaw reguł](../code-quality/native-minimum-rules-rule-set.md)|Te reguły dotyczą najpoważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.|
|[Natywny zalecany zestaw reguł](../code-quality/native-recommended-rules-rule-set.md)|Te reguły dotyczą najczęstszych i najpoważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych. |
|[Zestaw reguł zabezpieczeń dla kodu zarządzanego](../code-quality/security-rules-rule-set-for-managed-code.md)|Ten zestaw reguł zawiera wszystkie reguły zabezpieczeń firmy Microsoft. Obejmują tej reguły, aby zmaksymalizować liczbę zgłaszanych potencjalnych problemów zabezpieczeń.|
