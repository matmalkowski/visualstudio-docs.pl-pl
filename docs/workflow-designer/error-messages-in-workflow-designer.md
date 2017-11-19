---
title: "Komunikaty o błędach w Projektancie przepływów pracy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: ef4e1883fd6f72ab0937f4b6502c6bad086eb68f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="error-messages-in-workflow-designer"></a>Komunikaty o błędach w Projektancie przepływów pracy
W tym temacie opisano typy komunikatów o błędach, które mogą wystąpić podczas pracy z [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
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