---
title: 'Porady: rejestrowanie zdarzeń buforu tekstu przy użyciu starszej wersji interfejsu API | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ffe8362f26a55fdb6a9fe236782965a2062ed69
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639936"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Porady: rejestrowanie zdarzeń buforu tekstu przy użyciu starszej wersji interfejsu API
Jeśli uzyskujesz dostęp do buforu tekstowego przy użyciu starszej wersji interfejsu API, należy zarejestrować dla zdarzenia buforu tekstu, jak pokazano w poniższej procedurze.  
  
## <a name="to-advise-text-buffer-events"></a>Aby importowali zdarzenia buforu tekstu  
  
1.  Ze wskaźnika do jednego z interfejsów na <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, wywołaj `QueryInterface` dla wskaźnika do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Wywołaj <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> metody i przekaż identyfikator interfejsu zdarzenia, dla których chcesz zarejestrować.  
  
     Na przykład, jeśli chcesz zarejestrować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, należy przekazać w interfejsie identyfikator IID_IVsTextLinesEvents.  
  
     Bufor tekstowy zwraca wskaźnik do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfejs dla obiektu punktu połączenia.  
  
3.  Za pomocą tego wskaźnika, wywołaj <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> metody, przekazując wskaźnik do implementacji interfejsu zdarzenia, dla którego chcesz zarejestrować, na przykład `IVsTextLinesEvents` interfejsu.  
  
     Środowisko zwraca plik cookie, który można następnie przestawaj słuchać zdarzeń przez wywołanie metody <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> metody.  
  
## <a name="see-also"></a>Zobacz także  
 [Zdarzenia buforu tekstu w starszej wersji interfejsu API](../extensibility/text-buffer-events-in-the-legacy-api.md)