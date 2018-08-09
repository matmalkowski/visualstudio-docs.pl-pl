---
title: 'Porady: wyzwolenie zdarzenia po utracie fokusu przez Edytor | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af6abf503bec94cb45638b1e059f545f005cb318
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639659"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Porady: wyzwolenie zdarzenia po utracie fokusu przez Edytor
Czasami zachodzi konieczność wiadomo, kiedy redaktorem traci fokus ramki okna. Na przykład może być konieczne pobierania kodu z okna kodu, po edytor nie ma już fokusu w nim. Poniższa procedura zawiera kroki, które trzeba wykonać, aby otrzymać powiadomienie o Edytorze utraci fokus.  
  
## <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Aby wyzwolić zdarzenie w odpowiedzi na Edytor tracąc koncentracji  
  
1.  Monitorowanie zdarzeń dotyczących wyboru dzięki uzyskaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> obiektu z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> i przekazują je z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> obiektu.  
  
3.  W przypadku wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, poszukaj `elementid==SEID_WindowFrame`.  
  
4.  Test `varValueNew` parametr dwie rzeczy:  
  
    1.  Ramka okna, którego szukasz.  
  
    2.  Punkt, w którym program traci zaznaczenia do tej ramki okna.