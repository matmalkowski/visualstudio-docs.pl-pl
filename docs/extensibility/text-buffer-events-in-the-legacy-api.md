---
title: Zdarzenia buforu tekstu w interfejsie API starszych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5118fe29463368bcca90e21830e1418d41c18339
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Zdarzenia buforu tekstu w interfejsie API starsza wersja
Obiekt buforu tekstu emituje szereg różnych zdarzeń, które pozwalają odpowiedzieć w różnych sytuacjach.  
  
 Jeśli używasz starszej wersji interfejsu API, powinien implementować następujące interfejsy Aby otrzymywać powiadomienia o zmianach buforu tekstu. Uwidacznia interfejsów do buforu tekstu przy użyciu `IConnectionPointContainer` zmiany interfejsu dla buforu tekstu, aby otrzymać powiadomienie o wiersz z buforu. Aby uzyskać więcej informacji, zobacz [porady: rejestrowanie zdarzeń buforu tekstu przy użyciu interfejsu API starszych](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). W przypadku liczby `IVsTextStreamEvents` lub `IVsTextLinesEvents` interfejsów, zmiany są zwracane w albo jednej lub dwu dimensional współrzędne, odpowiednio.  
  
## <a name="text-buffer-interfaces"></a>Interfejsy buforu tekstu  
 Poniżej przedstawiono interfejsy implementowane przez obiekt buforu tekstu.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umożliwia tworzenie złożonego akcje (to znaczy akcje, które są pogrupowane w jednostce pojedynczego Cofnij/ponów).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Włącza trwałość danych dokumentu zarządzanych przez bufor tekstowy.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Udostępnia podstawowe usługi; używane przez wielu klientów.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Umożliwia odczytywanie i zapisywanie funkcji przy użyciu dwuwymiarowe współrzędne. Dziedziczy `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Zapewnia szybkie, zorientowanych strumieniowo, sekwencyjnych dostęp do tekstu w buforze.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Umożliwia odczytywanie i zapisywanie funkcji przy użyciu współrzędnych jednowymiarowa. Dziedziczy `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Zapewnia dostęp do ogólnej kolekcji właściwości. Najważniejsze właściwości jest nazwa lub krótkiej nazwy buforu. Losowe dane można przechowywać w buforze z tym interfejsem, tworząc identyfikator GUID i używać go jako klucza.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Obsługuje punkty połączenia dla zdarzeń.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfejsy zdarzeń buforu tekstu  
 Poniżej przedstawiono interfejsy powiadamianie o zdarzeniach buforu tekstu.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Powiadamia klientów, gdy nowej usługi języka jest skojarzony z buforu tekstu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Powiadamia klientów po zainicjowaniu buforu tekstu i podczas wprowadzania zmian do danych w buforze tekstu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Powiadamia klientów o zmianach w podstawowej bufor tekstowy we współrzędnych jednowymiarowa.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Powiadamia klientów o zmianach w podstawowej buforu tekstu w dwuwymiarowe współrzędne.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Powiadamia klientów o zmianach danych użytkownika.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Powiadamia klientów o ostatniej gestu zatwierdzania do wyzwolenia zdarzenia i zapewnia zakres zmiany tekstu. `IVsPreliminaryTextChangeCommitEvents` Interfejsu nie jest uruchamiany w odpowiedzi na cofnąć ani ponowić poleceń. Zdarzenia wyzwalać tylko dla buforów, które mają menedżera cofania. `IVsPreliminaryTextChangeCommitEvents`jest uruchamiany przed inne zdarzenia, takie jak lista pretty, aby mieć pewność, że inne zdarzenia nie należy zmieniać tekst, aby zmiany zostały zastosowane. VSPackage należy monitorować, albo `IVsPreliminaryTextChangeCommitEvents` interfejsu lub `IVsFinalTextChangeCommitEvents` interfejsu, ale nie oba.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Powiadamia klientów o ostatniej gestu zatwierdzania do wyzwolenia zdarzenia i zapewnia zakres zmiany tekstu. `IVsFinalTextChangeCommitEvents` Interfejsu nie jest uruchamiany w odpowiedzi na cofnąć ani ponowić poleceń. Zdarzenia wyzwalać tylko dla buforów, które mają menedżera cofania. `IVsFinalTextChangeCommitEvents`jest przeznaczony do użytku tylko usługi języka lub inne obiekty, które mają pełną kontrolę nad edycji. VSPackage należy monitorować, albo `IVsPreliminaryTextChangeCommitEvents` interfejsu lub `IVsFinalTextChangeCommitEvents` interfejsu, ale nie oba.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do buforu tekstu przy użyciu interfejsu API starsza wersja](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Porady: rejestrowanie zdarzeń buforu tekstu przy użyciu interfejsu API starsza wersja](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)