---
title: "Porady: Użyj znacznikach tekstu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f5c5c2686bee9850da72c00e044952b15bed9c58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-text-markers"></a>Porady: Użyj znacznikach tekstu
Znacznikach tekstu może odnosić się do edycji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> obiektu.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-apply-text-markers"></a>Aby zastosować znacznikach tekstu  
  
1.  Uzyskać wystąpienia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> klasy.  
  
    > [!NOTE]
    >  Edytor core automatycznie stosuje znaczniki tekstu standardowego do każdego dokumentu, który jest jego edycji, a nie należy jawnie stosowanie tekstu standardowego znaczników.  
  
2.  Uzyskać identyfikator znacznika typ znacznika są zainteresowani, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metody z `GUID` znacznika tekstu chcesz pracować.  
  
    > [!NOTE]
    >  Nie używaj `GUID` pakiet VSPackage lub usługa, która zapewnia znacznika tekstu.  
  
3.  Użyj Identyfikatora typu znacznik można uzyskać przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> metody jako parametr do wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metody lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> stosowaną w danym regionie tekstu znacznika tekstu.  
  
#### <a name="to-add-features-to-text-markers"></a>Aby dodać funkcje do znacznikach tekstu  
  
1.  Może być pożądane, aby dodać dodatkowe funkcje do tekstu znacznik, takich jak etykietki narzędzi, menu kontekstowe specjalnych lub obsługa specjalne okoliczności. Aby to zrobić:  
  
2.  Tworzenie, wdrażanie obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu.  
  
3.  W razie potrzeby dodatkowe funkcje zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> na ten sam obiekt, który implementuje interfejsy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejsu.  
  
4.  Przekaż <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfejs, który można utworzyć, do wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metody lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodę używaną do zastosowania w danym regionie tekstu znacznika tekstu.  
  
5.  Dodawanie obsługi menu kontekstowe w regionie znacznika tekstu jest niezbędne do utworzenia menu.  
  
     Aby uzyskać więcej informacji na temat sposobu tworzenia Zobacz menu kontekstowe [menu kontekstowe](../extensibility/context-menus.md).  
  
6.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Środowisko wywołuje metody interfejsów dostarczony <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> metody, lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metody zgodnie z potrzebami.  
  
## <a name="see-also"></a>Zobacz też  
 [Przy użyciu znaczników tekstu przy użyciu interfejsu API starsza wersja](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Porady: Dodawanie znaczników tekstu standardowego](../extensibility/how-to-add-standard-text-markers.md)   
 [Porady: Tworzenie niestandardowego tekstu znaczników](../extensibility/how-to-create-custom-text-markers.md)   
 [Porady: Implementowanie znaczników błąd](../extensibility/how-to-implement-error-markers.md)