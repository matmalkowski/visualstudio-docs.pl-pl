---
title: Interfejs IDebugApplicationThreadEvents110 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aaf312b1730696b812172aeea175619e911d03a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadevents110-interface"></a>Interfejs IDebugApplicationThreadEvents110
Dodaje więcej zdarzeń wątku. Te zdarzenia są tylko lokalne. Oznacza to, że możesz uzyskać subskrypcję do nich tylko w trwa proces debugować, używa [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) powiadomienia i unadvise metod w obiektach wątku aplikacji PDM (obiekty, które implementują [IDebugApplicationThread Interfejs](../../winscript/reference/idebugapplicationthread-interface.md)). Występują one w wątku, które pochodzą.  
  
> [!IMPORTANT]
>  Interfejs jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugActivationThreadEvents110` Interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110:: OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Wywołanie do wątku przy użyciu wątku PDM przełączanie zostało uruchomione.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Wątek jest wznawiana z punktu przerwania i będzie aktywny ponownie.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Wątek jest wstrzymywania dla punktu przerwania i może obsłużyć wywołania, które wymagają wątku pełni zostanie zawieszona.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Wywołanie do wątku przy użyciu wątku PDM przełączanie zostało ukończone.|