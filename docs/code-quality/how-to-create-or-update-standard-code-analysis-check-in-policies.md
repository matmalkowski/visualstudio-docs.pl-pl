---
title: 'Porady: tworzenie lub aktualizowanie standardowych zasad ewidencjonowania analizy kodu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4897ec080bf5d268db6ac229785ac0b642753bc0
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Porady: tworzenie lub aktualizowanie standardowych zasad ewidencjonowania analizy kodu

Możesz wymagać uruchomić analizy kodu dla wszystkich projektów kodu w projekcie zespołowym przy użyciu zasad analizy kodu zaewidencjonowania. Wymagających analizy kodu może poprawić jakość kodu, który jest sprawdzany w bazie kodu.

> [!NOTE]
> Ta funkcja jest dostępna tylko w przypadku korzystania z programu Team Foundation Server.

Zasad ewidencjonowania analizy kodu są ustawiane w ustawieniach projektu zespołowego i stosowane do każdego projektu kodu w projekcie zespołowym. Uruchamia analizy kodu są skonfigurowane do projektów kodu w pliku projektu (.xxproj) dla projektu kodu. Uruchamia analizy kodu są wykonywane na komputerze lokalnym. Po włączeniu zasad analizy kodu zaewidencjonowania, muszą być skompilowane pliki w projekcie kodu, które mają zostać zaewidencjonowane po ich ostatniej modyfikacji i analizy kodu, w którym, zawiera co najmniej reguł w ustawieniach projektu zespołowego musi zostać wykonana na komputerze gdzie c zmiany zostały wprowadzone.

- Dla kodu zarządzanego, ustawić zasady ewidencjonowania, określając *zestaw reguł* zawierającą podzbiór reguł analizy kodu.

- Dla kodu C/C++, Visual Studio 2017 wersji 15.6 i starszych wersjach zasad ewidencjonowania wymaga, że są uruchomione wszystkie reguły analizy kodu. Można dodać przed procesora dyrektywy Aby wyłączyć określone zasady dla projektów poszczególnych kodu w projekcie zespołowym. W 15.7 i nowszych można użyć **/ analyze: zestaw reguł** Aby określić, które reguł do uruchomienia. Aby uzyskać więcej informacji, zobacz [przy użyciu zestawów reguł do określania reguł C++ do uruchomienia](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Po określeniu zasad ewidencjonowania dla zarządzanego kodu członków zespołu można synchronizować swoje ustawienia analizy kodu dla projektów kodu w ustawieniach zasad projektu zespołowego.

### <a name="to-open-the-check-in-policy-editor"></a>Aby otworzyć Edytor zasad ewidencjonowania

1. W programie Team Explorer, kliknij prawym przyciskiem myszy nazwę projektu zespołowego, wskaż pozycję **ustawienia projektu zespołowego**, a następnie kliknij przycisk **kontroli źródła**.

1. W **kontroli źródła** okno dialogowe, wybierz opcję **zasad ewidencjonowania** kartę.

1. Wykonaj jedną z następujących czynności:

    - Kliknij przycisk **Dodaj** Aby utworzyć nowe zasady ewidencjonowania.

    - Kliknij dwukrotnie istniejące **analizy kodu** elementu **typ zasad** listy, aby zmienić zasady.

### <a name="to-set-policy-options"></a>Aby ustawić opcje zasad

Wybierz lub wyczyść następujące opcje:

    |Opcja|Opis|
    |------------|-----------------|
    |**Wymuś zaewidencjonowanie obejmowało tylko pliki, które są częścią bieżącego rozwiązania.**|Kod — analiza można uruchomić tylko na plików określonych w plikach konfiguracji rozwiązania i projektu. Ta zasada gwarantuje analizy całego kodu, który jest częścią rozwiązania.|
    |**Wymuszanie analiza kodu C/C++ (/ analyze)**|Wymaga się, że wszystkie projekty języka C lub C++ zostać skompilowane z / analyze — opcja kompilatora do uruchamiania analizy kodu przed ich mogą zostać zaewidencjonowane.|
    |**Wymuszanie analizy kodu dla zarządzanego kodu**|Wymaga wszystkich projektów zarządzanych przeprowadzanie analizy kodu i kompilacji przed ich mogą zostać zaewidencjonowane.|

### <a name="to-specify-a-managed-rule-set"></a>Aby określić zestaw reguł zarządzanych

- Z **Uruchom ten zestaw reguł** listy, użyj jednej z następujących metod:

    - Wybierz zestaw standardowych reguł firmy Microsoft.

    - Aby wybrać niestandardowego zestawu reguł, kliknij przycisk  **\<wybierz zestaw reguł z kontroli źródła... >**, a następnie wpisz ścieżkę kontroli wersji dla zestawu reguł w przeglądarce kontroli źródła. Składnia ścieżki kontroli wersji jest następująca:

    - **$/** `TeamProjectName` **/** `VersionControlPath`

    - Aby uzyskać więcej informacji o sposobie tworzenia i wdrażania niestandardowych zasad ewidencjonowania reguły, zobacz [zasady niestandardowe wykonania zaewidencjonowania dla kodu zarządzanego](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Zobacz także

[Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie z nich](../code-quality/creating-and-using-code-analysis-check-in-policies.md)