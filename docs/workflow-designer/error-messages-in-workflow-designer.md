---
title: "Komunikaty o błędach w Projektancie przepływów pracy | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 748893d7e08ca72140fad31c4546f4166636b8de
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="error-messages-in-workflow-designer"></a>Komunikaty o błędach w Projektancie przepływów pracy
W tym temacie opisano typy komunikatów o błędach, które mogą wystąpić podczas pracy z projektanta przepływów pracy systemu Windows.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Sytuacje, w których występują błędy w Projektancie przepływów pracy
 Błędy w [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] wystąpić w następujących sytuacjach:

1.  Istnieje błąd w wyrażeniu.

2.  Ograniczenia sprawdzania poprawności działania nie zostały spełnione.

3.  Wystąpiły błędy w pliku XAML, które powodują działanie, aby nie można załadować.

4.  Wystąpiły błędy w pliku XAML, które powodują uruchomienie przepływu pracy nie można załadować.

 Nieprawidłowy wyrażeń i ograniczenia walidacji niezadowolony nie powodują uruchomienie przepływu pracy nie można utworzyć. Tworzenie przepływu pracy zakończy się powodzeniem, ale <xref:System.Activities.InvalidWorkflowException> jest zgłaszany w czasie wykonywania. Jeśli wystąpią błędy w pliku XAML, kompilacja kończy się niepowodzeniem.

 Wewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], gdy przepływ pracy został załadowany, jego błędy są wyświetlane w **listy błędów**. Aby przejść do działania, który jest źródłem błąd, kliknij dwukrotnie ten błąd w **listy błędów**.

### <a name="expression-errors"></a>Błędy wyrażenia
 Nieprawidłowe wyrażenie jest oznaczona czerwone koło z białym znakiem wykrzyknika, obok wyrażenia. Ustawiając kursor nad ikonę Wyświetla etykietki narzędzia, opisujący przyczynę błędu. Wewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], kliknij przycisk wyrażenia, aby wyświetlić wiersz podkreśla źródła błędu. Ustawiając kursor nad Wyświetla linie tekst etykietki narzędzia, opisujący przyczynę błędu.

### <a name="activity-validation-errors"></a>Błędy sprawdzania poprawności działania
 Gdy ograniczenia sprawdzania poprawności działania nie zostały spełnione, w prawym górnym rogu działania pojawi się czerwone kółko z białym znakiem wykrzyknika. Ustawiając kursor nad ikonę Wyświetla etykietki narzędzia, opisujący przyczynę błędu.

### <a name="xaml-load-errors"></a>Błędy ładowania XAML
 Gdy działanie nie można załadować, z tekstem "działania nie można załadować z powodu błędów w kodzie XAML" wyświetlony. Ten błąd zazwyczaj występuje, gdy nie można rozpoznać typu działania. Nieprawidłowe działanie mogą zostać usunięte w projektancie, wybierając czerwonym prostokątem i usunięcie go.

### <a name="workflow-load-errors"></a>Błędy ładowania przepływu pracy
 Gdy przepływ pracy nie można załadować, tekst "Projektanta przepływów pracy napotkał problemy z danym dokumentem" pojawia się na powierzchni projektowej oraz informacje o wyjątku, który spowodował błąd przepływu pracy do załadowania. Ten błąd zazwyczaj występuje, gdy nie można przeanalizować pliku XAML.