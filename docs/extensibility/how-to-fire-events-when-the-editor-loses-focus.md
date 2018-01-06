---
title: "Porady: wyzwalać zdarzeń, gdy Edytor traci fokus | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bb20adf3950e87c37e2ca64bcd78913839f89d01
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Porady: wyzwalać zdarzeń, gdy Edytor traci fokus
Czasami zachodzi konieczność wiedzieć, kiedy edytora traci fokus na ramki okna. Na przykład może być konieczne pobierania kodu z okna Kod po edytor nie ma już fokusu w nim. Poniższa procedura zawiera kroki, które należy wykonać, aby otrzymać powiadomienie o Edytorze utraci fokus.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Zdarzenia w odpowiedzi na edytorze utraci fokus  
  
1.  Monitorowanie zdarzeń zaznaczenia, uzyskując <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> obiekt z <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> i przekazują je z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> obiektu.  
  
3.  W przypadku wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, wyszukaj `elementid==SEID_WindowFrame`.  
  
4.  Test `varValueNew` parametr dwie czynności:  
  
    1.  Ramka okna, którego szukasz.  
  
    2.  Punkt, w którym program utraci zaznaczenie do tej ramki okna.