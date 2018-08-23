---
title: Opinia dla użytkownika | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3462edb539822cd856cd7281566674b4ed0c4def
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683133"
---
# <a name="feedback-to-the-user"></a>Opinia dla użytkownika
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [informacje zwrotne dla użytkownika](https://docs.microsoft.com/visualstudio/extensibility/internals/feedback-to-the-user).  
  
W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE), wizualną opinię dotyczący możliwości opiera się na bieżące zaznaczenie i kontekst zaznaczenia globalnego użytkownika. W poniższej tabeli wymieniono funkcje, które są dostępne w kontekstach inną opcję.  
  
|Kontekst zaznaczenia|Dostępne funkcje|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Bieżący zestaw produktów|Specyficzne dla produktu|  
|Aktywnej hierarchii|Określonego typu hierarchii|  
|Element aktywnej hierarchii|Określonego typu elementu w hierarchii|  
|Aktywnego dokumentu|Określonego typu dokumentu|  
|Okno najwyższego poziomu interfejsu wielu dokumentów (MDI)|Określonego typu okno|  
|Bieżący kontekst zaznaczenia|Określone kontekst zaznaczenia|  
  
 Jeśli tylko urządzenia surface funkcjonalność, użytkownicy muszą i zapewnić spójne wybór i opinie kontekst środowiska można zmniejszyć złożoność w środowisku IDE. Przy każdym otwarciu okna w IDE, stosowane są następujące reguły:  
  
-   Jeśli okno zmienia kontekst zaznaczenia, informacje zwrotne dotyczące wyboru jest wyraźnie wskazane w oknie i dynamiczna Pomoc okna, jeśli wyświetlony, jest zaktualizowana w celu odzwierciedlenia bieżącego kontekstu.  
  
-   Jeśli okno zmienia kontekst zaznaczenia globalnego, wszystkich menu kontekstowych, okna aktywnej hierarchii i na pasku tytułu aplikacji są aktualizowane, tak aby odzwierciedlić bieżący kontekst.  
  
-   Okno powinno powierzchni właściwości dla bieżącego zaznaczenia w **właściwości** okna i, opcjonalnie, jeśli wyświetlony, **strony właściwości** okno dialogowe.  
  
-   Jeśli okno nie powierzchni właściwości lub zmienić kontekst zaznaczenia globalnego, informacje zwrotne dotyczące wyboru nie powinna pozostać w oknie, gdy nie jest już aktywnego okna w IDE.  
  
-   Wszystkie okna narzędzi specyficznych dla dokumentu stale powinny odzwierciedlać aktywnego dokumentu.  
  
-   Menu, paski narzędzi i paska tytułu aplikacji powinny odzwierciedlać okna klienta znajdujące się najwyżej interfejsu wielu dokumentów (MDI).  
  
 Na przykład po otwarciu widoku HTML w formularzu sieci Web w projekcie aplikacji sieci Web w języku Visual Basic i użytkownik wybierze `<td>` tagu, informacje są przekazywane w następujący sposób:  
  
-   Wybór jest wskazane w aktywnym oknie i zostaną uwzględnione w **właściwości** okna.  
  
-   Specyficzne dla dokumentu **przybornika** zostanie zaktualizowany w celu odzwierciedlenia aktywnego dokumentu.  
  
-   **Edytora** narzędzi i **tabeli** są wyświetlane w menu i na pasku tytułu aktualizowany w celu odzwierciedlenia okna formularza sieci Web.  
  
-   Okno aktywnej hierarchii, które jest zazwyczaj **Eksploratora rozwiązań**i jej aktualizacji paska tytułu, aby odzwierciedlić bieżący kontekst i kontekstowej **projektu** poleceń menu teraz je zastosować do aktywnego internetowego Projekt aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md)   
 [Hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md)

