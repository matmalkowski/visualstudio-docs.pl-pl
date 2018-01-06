---
title: "Porady: rejestrowanie zdarzeń buforu tekstu przy użyciu interfejsu API starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 94f2e781c316f3891fdef0c324d54fa2f9742222
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Porady: rejestrowanie zdarzeń buforu tekstu przy użyciu interfejsu API starsza wersja
Jeśli uzyskują dostęp do buforu tekstu przy użyciu starszej wersji interfejsu API, należy zarejestrować dla zdarzenia buforu tekstu, jak pokazano w poniższej procedurze.  
  
### <a name="to-advise-text-buffer-events"></a>Powiadomienie zdarzenia buforu tekstu  
  
1.  Ze wskaźnika do jednego z interfejsów na <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, wywołaj `QueryInterface` dla wskaźnika do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> — metoda i przekaż identyfikator interfejsu zdarzeń, dla których chcesz zarejestrować.  
  
     Na przykład, jeśli chcesz zarejestrować dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, następnie przekazać w interfejsie identyfikator IID_IVsTextLinesEvents.  
  
     Bufor tekstowy zwraca wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejsu dla obiektu punktu połączenia.  
  
3.  Przy użyciu tego wskaźnika, wywołaj <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> metody, przekazując wskaźnik do implementacji interfejsu zdarzenia, dla którego chcesz zarejestrować, na przykład `IVsTextLinesEvents` interfejsu.  
  
     Środowisko zwraca pliku cookie, który można następnie zatrzymać nasłuchuje zdarzeń przez wywołanie metody <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia buforu tekstu w interfejsie API starsza wersja](../extensibility/text-buffer-events-in-the-legacy-api.md)