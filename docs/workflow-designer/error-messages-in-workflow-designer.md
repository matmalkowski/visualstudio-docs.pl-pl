---
title: Komunikaty o błędach w Projektancie przepływów pracy
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c644922f240cd07c47e68e65432289c68bbe318
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="error-messages-in-workflow-designer"></a>Komunikaty o błędach w Projektancie przepływów pracy

W tym temacie opisano typy komunikatów o błędach, które mogą wystąpić podczas pracy z projektanta przepływów pracy systemu Windows.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Sytuacje, w których występują błędy w Projektancie przepływów pracy

Błędy w Projektancie przepływów pracy wystąpić w następujących sytuacjach:

1.  Istnieje błąd w wyrażeniu.

2.  Ograniczenia sprawdzania poprawności działania nie zostały spełnione.

3.  Wystąpiły błędy w pliku XAML, które powodują działanie, aby nie można załadować.

4.  Wystąpiły błędy w pliku XAML, które powodują uruchomienie przepływu pracy nie można załadować.

Nieprawidłowy wyrażeń i ograniczenia walidacji niezadowolony nie powodują uruchomienie przepływu pracy nie można utworzyć. Tworzenie przepływu pracy zakończy się powodzeniem, ale <xref:System.Activities.InvalidWorkflowException> jest zgłaszany w czasie wykonywania. Jeśli wystąpią błędy w pliku XAML, kompilacja kończy się niepowodzeniem.

W programie Visual Studio, gdy przepływ pracy został załadowany, jego błędy są wyświetlane w **listy błędów**. Aby przejść do działania, który jest źródłem błąd, kliknij dwukrotnie ten błąd w **listy błędów**.

### <a name="expression-errors"></a>Błędy wyrażenia
 Nieprawidłowe wyrażenie jest oznaczona czerwone koło z białym znakiem wykrzyknika, obok wyrażenia. Ustawiając kursor nad ikonę Wyświetla etykietki narzędzia, opisujący przyczynę błędu. W programie Visual Studio kliknij przycisk wyrażenia, aby wyświetlić wiersz podkreśla źródła błędu. Ustawiając kursor nad Wyświetla linie tekst etykietki narzędzia, opisujący przyczynę błędu.

### <a name="activity-validation-errors"></a>Błędy sprawdzania poprawności działania
 Gdy ograniczenia sprawdzania poprawności działania nie zostały spełnione, w prawym górnym rogu działania pojawi się czerwone kółko z białym znakiem wykrzyknika. Ustawiając kursor nad ikonę Wyświetla etykietki narzędzia, opisujący przyczynę błędu.

### <a name="xaml-load-errors"></a>Błędy ładowania XAML
 Gdy działanie nie można załadować, z tekstem "działania nie można załadować z powodu błędów w kodzie XAML" wyświetlony. Ten błąd zazwyczaj występuje, gdy nie można rozpoznać typu działania. Nieprawidłowe działanie mogą zostać usunięte w projektancie, wybierając czerwonym prostokątem i usunięcie go.

### <a name="workflow-load-errors"></a>Błędy ładowania przepływu pracy
 Gdy przepływ pracy nie można załadować, tekst "Projektanta przepływów pracy napotkał problemy z danym dokumentem" pojawia się na powierzchni projektowej oraz informacje o wyjątku, który spowodował błąd przepływu pracy do załadowania. Ten błąd zazwyczaj występuje, gdy nie można przeanalizować pliku XAML.