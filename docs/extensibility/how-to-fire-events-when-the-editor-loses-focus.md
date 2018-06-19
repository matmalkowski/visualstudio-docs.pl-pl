---
title: 'Porady: wyzwalać zdarzeń, gdy Edytor traci fokus | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: bbdcf30443bc548fd8d182db301cbc7119d8ceae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127047"
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