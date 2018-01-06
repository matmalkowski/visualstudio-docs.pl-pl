---
title: 'Porady: Tworzenie lub aktualizowanie standardowych zasad analizy kodu zaewidencjonowania | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.policyeditor
helpviewer_keywords: code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d11a8c3169b019ac504ed98258d9281037eb1dd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Porady: tworzenie lub aktualizowanie standardowych zasad ewidencjonowania analizy kodu
Możesz wymagać uruchomić analizy kodu dla wszystkich projektów kodu w projekcie zespołowym przy użyciu zasad analizy kodu zaewidencjonowania. Wymagających analizy kodu może poprawić jakość kodu, który jest sprawdzany w bazie kodu.  
  
> [!NOTE]
>  Ta funkcja jest dostępna tylko w przypadku korzystania z programu Team Foundation Server.  
  
 Zasad ewidencjonowania analizy kodu są ustawiane w ustawieniach projektu zespołowego i stosowane do każdego projektu kodu w projekcie zespołowym. Uruchamia analizy kodu są skonfigurowane do projektów kodu w pliku projektu (.xxproj) dla projektu kodu. Uruchamia analizy kodu są wykonywane na komputerze lokalnym. Po włączeniu zasad analizy kodu zaewidencjonowania, muszą być skompilowane pliki w projekcie kodu, które mają zostać zaewidencjonowane po ich ostatniej modyfikacji i analizy kodu, w którym, zawiera co najmniej reguł w ustawieniach projektu zespołowego musi zostać wykonana na komputerze gdzie c zmiany zostały wprowadzone.  
  
-   Dla kodu zarządzanego, ustawić zasady ewidencjonowania, określając *zestaw reguł* zawierającą podzbiór reguł analizy kodu.  
  
-   Dla kodu C/C++ zasad ewidencjonowania wymaga, że są uruchomione wszystkie reguły analizy kodu. Można dodać przed procesora dyrektywy Aby wyłączyć określone zasady dla projektów poszczególnych kodu w projekcie zespołowym.  
  
 Po określeniu zasad ewidencjonowania dla zarządzanego kodu członków zespołu można synchronizować swoje ustawienia analizy kodu dla projektów kodu w ustawieniach zasad projektu zespołowego.  
  
### <a name="to-open-the-check-in-policy-editor"></a>Aby otworzyć Edytor zasad ewidencjonowania  
  
1.  W programie Team Explorer, kliknij prawym przyciskiem myszy nazwę projektu zespołowego, wskaż pozycję **ustawienia projektu zespołowego**, a następnie kliknij przycisk **kontroli źródła**.  
  
2.  W **kontroli źródła** okno dialogowe, wybierz opcję **zasad ewidencjonowania** kartę.  
  
3.  Wykonaj jedną z następujących czynności:  
  
    -   Kliknij przycisk **Dodaj** Aby utworzyć nowe zasady ewidencjonowania.  
  
    -   Kliknij dwukrotnie istniejące **analizy kodu** elementu **typ zasad** listy, aby zmienić zasady.  
  
### <a name="to-set-policy-options"></a>Aby ustawić opcje zasad  
  
-   Wybierz lub wyczyść następujące opcje:  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |**Wymuś zaewidencjonowanie obejmowało tylko pliki, które są częścią bieżącego rozwiązania.**|Kod — analiza można uruchomić tylko na plików określonych w plikach konfiguracji rozwiązania i projektu. Ta zasada gwarantuje analizy całego kodu, który jest częścią rozwiązania.|  
    |**Wymuszanie analiza kodu C/C++ (/ analyze)**|Wymaga się, że wszystkie projekty języka C lub C++ zostać skompilowane z / analyze — opcja kompilatora do uruchamiania analizy kodu przed ich mogą zostać zaewidencjonowane.|  
    |**Wymuszanie analizy kodu dla zarządzanego kodu**|Wymaga wszystkich projektów zarządzanych przeprowadzanie analizy kodu i kompilacji przed ich mogą zostać zaewidencjonowane.|  
  
-  
  
### <a name="to-specify-a-managed-rule-set"></a>Aby określić zestaw reguł zarządzanych  
  
-   Z **Uruchom ten zestaw reguł** listy, użyj jednej z następujących metod:  
  
    -   Wybierz zestaw standardowych reguł firmy Microsoft.  
  
    -   Aby wybrać niestandardowego zestawu reguł, kliknij przycisk  **\<wybierz zestaw reguł z kontroli źródła... >**, a następnie wpisz ścieżkę kontroli wersji dla zestawu reguł w przeglądarce kontroli źródła. Składnia ścieżki kontroli wersji jest następująca:  
  
    -   **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    -   Aby uzyskać więcej informacji o sposobie tworzenia i wdrażania niestandardowych zasad ewidencjonowania reguły, zobacz [zasady niestandardowe wykonania zaewidencjonowania dla kodu zarządzanego](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie z nich](../code-quality/creating-and-using-code-analysis-check-in-policies.md)