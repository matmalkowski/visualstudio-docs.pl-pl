---
title: "Określanie stanu polecenia za pomocą zestawów międzyoperacyjnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3cde6ae841271622e0d538d679991288c111095e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>Określanie stanu polecenia przy użyciu zestawy międzyoperacyjne
Pakiet VSPackage musi zachować informacje o stanie poleceń, które może obsługiwać. Środowisko nie może określić, kiedy polecenie przetwarzanych w ramach VSPackage staje się włączone lub wyłączone. Jest odpowiedzialny za VSPackage do informowania o stanach polecenia środowiska, na przykład stan ogólne polecenia takie jak **Wytnij**, **kopiowania**, i **Wklej**.  
  
## <a name="status-notification-sources"></a>Stan powiadomienia źródeł  
 Środowisko otrzymuje informacji o poleceniach za pośrednictwem VSPackages <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę, która jest częścią implementacji pakiet VSPackage z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Wywołania środowiska <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody pakiet VSPackage w obszarze dwa warunki:  
  
-   Gdy użytkownik otwiera menu głównego lub menu kontekstowego (na przykład przez kliknięcie prawym przyciskiem myszy), wykonuje środowiska <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody na wszystkie polecenia tego menu, aby określić ich stan.  
  
-   Gdy pakiet VSPackage żąda, że środowisko zaktualizować bieżącego interfejsu użytkownika (UI). Dzieje się tak jak polecenia, które są widoczne dla użytkownika, takich jak **Wytnij**, **kopiowania**, i **Wklej** grupowanie na standardowym pasku narzędzi, stają się włączone i wyłączone w odpowiedź z akcjami tworzenia i kontekstu użytkownika.  
  
 Ponieważ powłoki obsługuje wiele VSPackages, wydajność powłoki zbyt czy zmniejsza, jeśli wymaga ona sondowanie każdy pakiet VSPackage do określenia stanu polecenia. Zamiast tego VSPackage aktywnie powiadomić środowiska po zmianie jego interfejsie użytkownika w momencie zmiany. Aby uzyskać więcej informacji o powiadomienie o aktualizacji, zobacz [Aktualizowanie interfejsu użytkownika](../../extensibility/updating-the-user-interface.md).  
  
## <a name="status-notification-failure"></a>Niepowodzenie powiadomień stanu  
 Błąd VSPackage do powiadamiania o zmianie stanu polecenia środowiska można umieścić interfejsu użytkownika w stanie niespójnym. Należy pamiętać, że wszelkie polecenia menu menu lub kontekstu można umieścić na pasku narzędzi przez użytkownika. W związku z tym Aktualizowanie interfejsu użytkownika tylko wtedy, gdy zostanie otwarte menu menu lub kontekstu nie jest wystarczająca.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak VSPackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementacja](../../extensibility/internals/command-implementation.md)