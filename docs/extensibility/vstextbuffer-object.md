---
title: Obiekt VSTextBuffer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 643bd434e058a24cc17936d9ab2f333489b8aa5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="vstextbuffer-object"></a>Obiekt VSTextBuffer
Obiekt buforu tekstu reprezentuje strumień tekst Unicode, który jest zwykle skojarzone z plikiem. A <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiektu można użyć poza kontekstem edytora podstawowe, jak w przypadku kreatora.  
  
 W poniższej tabeli przedstawiono interfejsy `VSTextBuffer`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Iolecommandtarget —](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Standardowy interfejs OLE. Wykorzystywana głównie do obsługi w buforze Cofnij/Ponów.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Standardowy interfejs OLE.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umożliwia tworzenie związki akcje (to znaczy akcje, które są pogrupowane w jednostce pojedynczego Cofnij/ponów).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Włącza trwałość danych dokumentu zarządzanych przez bufor tekstowy.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Udostępnia podstawowe usługi; używane przez wielu klientów.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Służy do wyszukiwania w buforze.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Umożliwia odczytywanie i zapisywanie funkcji przy użyciu dwuwymiarowe współrzędne. Dziedziczy `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Umożliwia odczytywanie i zapisywanie funkcji przy użyciu współrzędnych jednowymiarowa. Dziedziczy `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Zapewnia szybkie, zorientowanych strumieniowo, sekwencyjnych dostęp do tekstu w buforze.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Zapewnia dostęp do ogólnej kolekcji właściwości. Najważniejsze właściwości jest nazwa lub krótkiej nazwy buforu. Losowe dane można przechowywać w buforze z tym interfejsem, tworząc identyfikator GUID i używać go jako klucza.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Obsługuje punkty połączenia dla zdarzeń.|  
  
## <a name="remarks"></a>Uwagi  
 `VSTextBuffer` Zwykle są wyszukiwane przy `QueryInterface` wywołać `IVsTextBuffer`. Aby uzyskać więcej informacji, zobacz [buforu tekstu](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Edytowanie danych](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)