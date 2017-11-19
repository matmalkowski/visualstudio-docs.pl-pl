---
title: "Opinie użytkownikowi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ffc6ecc620f57f0cc1e4dd8baf02f1bd1b17d53b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="feedback-to-the-user"></a>Opinię do użytkownika
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) wizualne dotyczące funkcjonalność dostępna jest oparta na bieżące zaznaczenie i kontekst zaznaczenia globalnego użytkownika. W poniższej tabeli wymieniono funkcje, które są dostępne w wybór różnych kontekstach.  
  
|Kontekst zaznaczenia|Funkcje dostępne|  
|-----------------------|-----------------------------|  
|IDE|Globalne|  
|Bieżący zestaw produktu|Specyficzne dla produktu|  
|Aktywnej hierarchii|Określonego typu hierarchii|  
|Element aktywnej hierarchii|Określonego typu elementu w hierarchii|  
|Dokument aktywny|Określonego typu dokumentu|  
|Okno znajdujące się najwyżej interfejsu wielu dokumentów (MDI)|Określonego typu okno|  
|Bieżący kontekst zaznaczenia|Kontekst zaznaczenia określonych|  
  
 Jeśli tylko powierzchnią funkcji, użytkownicy muszą i zapewnić spójne wybór i opinie kontekstu środowiska można zmniejszyć złożoność w IDE. Przy każdym otwarciu okna w środowisku IDE obowiązują następujące reguły:  
  
-   Jeśli okno zmienia jego kontekst zaznaczenia, wybór opinii jest wyraźnie wskazane w oknie, a w oknie Pomoc dynamiczna, jeśli pokazano, zostało zaktualizowane do uwzględnienia w bieżącym kontekście.  
  
-   Jeśli okno zmienia kontekst zaznaczenia globalnych, wszystkie zależne od kontekstu menu, okna aktywnej hierarchii i na pasku tytułu aplikacji są aktualizowane do uwzględnienia w bieżącym kontekście.  
  
-   Okno powinien powierzchni właściwości dla bieżącego zaznaczenia w **właściwości** okna i, opcjonalnie, jeśli pokazano, **strony właściwości** okno dialogowe.  
  
-   Jeśli okno nie powierzchni właściwości lub zmienić kontekst zaznaczenia globalnych, wybór opinii nie powinny pozostać w oknie, gdy nie jest już aktywne okno w środowisku IDE.  
  
-   Wszystkie okna narzędzi specyficznych dla dokumentu stale powinien odzwierciedlać aktywny dokument.  
  
-   Menu i pasków narzędzi na pasku tytułu aplikacji odzwierciedlały okno klienta znajdujące się najwyżej interfejsu wielu dokumentów (MDI).  
  
 Na przykład po otwarciu widoku HTML formularza sieci Web wewnątrz projektu aplikacji sieci Web Visual Basic, a użytkownik wybierze `<td>` tag, opinii znajduje się w następujący sposób:  
  
-   Wybór jest wskazane w aktywnym oknie i zostaną uwzględnione w **właściwości** okna.  
  
-   Dokument specyficzne **przybornika** jest aktualizowana w celu odzwierciedlenia aktywny dokument.  
  
-   **Edytor** narzędzi i **tabeli** są wyświetlane menu i paska tytułu aktualizuje, aby odzwierciedlić okna formularza sieci Web.  
  
-   W oknie aktywnej hierarchii, która jest zazwyczaj **Eksploratora rozwiązań**i jej aktualizacji paska tytułu, aby uwzględnić w bieżącym kontekście oraz kontekstowa **projektu** polecenia menu teraz stosowane do aktywnego sieci Web Projekt aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybór i waluty w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md)   
 [Wybieranie i hierarchie](../../extensibility/internals/hierarchies-and-selection.md)