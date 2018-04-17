---
title: 'Porady: Dodawanie znaczników tekstu standardowego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2fc5bf34c9b4200d8d7fef2d9f4a878ca604f886
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-standard-text-markers"></a>Porady: Dodawanie znaczników tekstu standardowego
Użyj poniższej procedury można utworzyć jedną z domyślnych typów znacznika tekstu dostarczane z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] core edytora.  
  
### <a name="to-create-a-text-marker"></a>Aby utworzyć znacznika tekstu  
  
1.  W zależności od tego, czy używany jest jeden lub dwa — wymiarów układu współrzędnych, wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metody lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodę w celu utworzenia nowego znacznika tekstu.  
  
     W wywołaniu tej metody, określ typ znacznika, zakres tekstu do utworzenia znacznika i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu. Ta metoda zwraca następnie wskaźnik do nowo utworzony tekstu znacznika. Typy znacznika są pobierane z <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> wyliczenia. Określ <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu, jeśli chcesz mieć świadomość znacznika zdarzenia.  
  
    > [!NOTE]
    >  Utwórz znacznikach tekstu w tylko głównym wątku interfejsu użytkownika. Edytor core zależy od zawartości buforu tekstu, aby utworzyć znacznikach tekstu i buforu tekstu nie jest bezpieczne dla wątków.  
  
## <a name="adding-a-custom-command"></a>Dodawanie poleceń niestandardowych  
 Implementowanie `IVsTextMarkerClient` interfejsu i udostępnia wskaźnik ze znacznikiem zwiększa zachowanie znacznik na kilka sposobów. Po pierwsze umożliwia zapewnienie porady znacznika sieci i można wykonać polecenia. To umożliwia także do otrzymywania powiadomień o zdarzeniach dla poszczególnych znaczników oraz umożliwia tworzenie menu kontekstowe niestandardowych w znacznika. Poniższa procedura umożliwia dodawanie polecenia niestandardowego do menu kontekstowego znacznika.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Aby dodać polecenia niestandardowych do menu kontekstowego  
  
1.  Przed wyświetleniem menu kontekstowego, środowisko wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> — metoda i przekazuje możesz wskaźnik do znacznika tekstu wpływ i liczby element polecenia w menu kontekstowym.  
  
     Na przykład zawierać polecenia specyficzne dla punktu przerwania w menu kontekstowym **Usuń punkt przerwania** za pośrednictwem **nowego punktu przerwania**wyświetlane na poniższym zrzucie ekranu.  
  
     ![Menu kontekstowe znacznika](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Przesłać tekst identyfikujący nazwę polecenia niestandardowych. Na przykład **Usuń punkt przerwania** może być polecenia niestandardowych, gdy środowisko nie już dostarczył go. Możesz również przesłać Określa, czy polecenie jest obsługiwane, dostępna i włączona i/lub przełącz — wyłączone. Środowisko używa tych informacji do wyświetlenia polecenia niestandardowych w menu kontekstowym w prawidłowy sposób.  
  
3.  Do wykonania polecenia, wywołania środowiska <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metoda przekazywania wskaźnik do znacznika tekstu i liczby wybrane z menu kontekstowego polecenie.  
  
     Dzięki tym informacjom tego wywołania można wykonać mówią, niezależnie od akcje znacznika tekstu polecenia niestandardowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przy użyciu znaczników tekstu przy użyciu interfejsu API starsza wersja](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Porady: Implementowanie znaczników błąd](../extensibility/how-to-implement-error-markers.md)   
 [Porady: Tworzenie niestandardowego tekstu znaczników](../extensibility/how-to-create-custom-text-markers.md)   
 [Porady: Użyj znacznikach tekstu](../extensibility/how-to-use-text-markers.md)