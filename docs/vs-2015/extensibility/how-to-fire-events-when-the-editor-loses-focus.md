---
title: 'Porady: wyzwolenie zdarzenia po utracie fokusu przez Edytor | Dokumentacja firmy Microsoft'
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
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2462e41470b72c63f5c96a69d2776af2a640c372
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676702"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Porady: wyzwolenie zdarzenia po utracie fokusu przez Edytor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: Fire zdarzenia podczas edytora traci fokus](https://docs.microsoft.com/visualstudio/extensibility/how-to-fire-events-when-the-editor-loses-focus).  
  
Czasami zachodzi konieczność wiadomo, kiedy redaktorem traci fokus ramki okna. Na przykład może być konieczne pobierania kodu z okna kodu, po edytor nie ma już fokusu w nim. Poniższa procedura zawiera kroki, które trzeba wykonać, aby otrzymać powiadomienie o Edytorze utraci fokus.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Aby wyzwolić zdarzenie w odpowiedzi na Edytor tracąc koncentracji  
  
1.  Monitorowanie zdarzeń dotyczących wyboru dzięki uzyskaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> obiektu z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> i przekazują je z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> obiektu.  
  
3.  W przypadku wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, poszukaj `elementid==SEID_WindowFrame`.  
  
4.  Test `varValueNew` parametr dwie rzeczy:  
  
    1.  Ramka okna, którego szukasz.  
  
    2.  Punkt, w którym program traci zaznaczenia do tej ramki okna.

