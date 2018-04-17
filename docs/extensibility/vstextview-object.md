---
title: Obiekt VSTextView | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5be89d01a668fd05e70e73e31ffaf3742317c272
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="vstextview-object"></a>Obiekt VSTextView
Widok tekstu jest oknem, które umożliwia użytkownikom wyświetlić i edytować tekst Unicode buforu tekstowego. Widok jest zasadniczo większość użytkowników zapoznaj się, jak edytor. Ponieważ widok jest oddzielony od buforu różnych warstw tekst (Zawijanie, zwijania tekstu i tak dalej), widok nie gwarantuje to dokładnie reprezentację tekstu w buforze. Aby uzyskać więcej informacji na temat widoku tekstu, zobacz [dostęp do theText widoku przy użyciu interfejsu API starsza wersja](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 W poniższej tabeli przedstawiono interfejsów w <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiektu.  
  
|Interface|Opis|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umożliwia tworzenie złożonego akcje (to znaczy akcje, które są pogrupowane w jednostce pojedynczego Cofnij/ponów).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Zapewnia podstawowe metody do zarządzania i dostęp do widoku. `IVsTextView` nie jest wątku bezpieczne.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Tworzy i którymi zarządza okienko okna.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Współdziała z warstwy tekstu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Wykonuje operacje w widoku z innego wątku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie danych](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Obiekt VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Uzyskiwanie dostępu do theText widoku przy użyciu interfejsu API starsza wersja](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)