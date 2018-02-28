---
title: "Uzyskiwanie dostępu do warstwy tekstu przy użyciu interfejsu API starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8a5f7a80e8d594f3c9e62ecd2047cc1116948d2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Uzyskiwanie dostępu do warstwy tekstu przy użyciu interfejsu API starsza wersja
Warstwa tekstu hermetyzuje zwykle aspektów układu tekstu. Na przykład warstwy "Funkcja w pojedynczych" Ukrywa tekst przed i po funkcja zawierająca karetki (punktu wstawiania).  
  
 Warstwa tekstu znajduje się pomiędzy buforu a widokiem i modyfikuje sposób widoku widzi zawartości buforu.  
  
## <a name="text-layer-information"></a>Informacje tekstowe warstwy  
 Na poniższej liście opisano, jak działa warstwy tekstu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Tekst w warstwie tekst można adorned kolorowanie składni i znaczników.  
  
-   Obecnie nie można wdrożyć własne warstwy.  
  
-   Przedstawia warstwy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, która jest pochodną <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>. Bufor tekstowy się również jest implementowany jako warstwy, co umożliwia wyświetlanie radzenia sobie polymorphically z warstwy podstawowej.  
  
-   Dowolna liczba warstw może znajdować się między widokiem a buforu. Każda warstwa dotyczy tylko warstwy poniżej, a widok dotyczy przede wszystkim z warstwą najwyższy. (W widoku ma pewne informacje o buforu).  
  
-   Warstwa może mieć wpływ na tylko warstwy, które są poniżej. Nie może to wpłynąć na warstwy powyżej poza pochodzących standardowych zdarzeń.  
  
-   W edytorze tekstu ukrytego, syntetycznych tekst i zawijanie są zaimplementowane jako warstwy. Można zaimplementować tekstu ukrytego i syntetycznych bez poprzez bezpośrednią interakcję z warstwy. Aby uzyskać więcej informacji, zobacz [konspekt w starsza wersja usługi języka](../extensibility/internals/outlining-in-a-legacy-language-service.md) i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Każda warstwa tekst ma swój własny lokalny system współrzędnych, udostępnianym przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interfejsu. Warstwa zawijanie wierszy, na przykład może zawierać dwa wiersze podczas podstawowej buforu tekstu może zawierać tylko jeden wiersz.  
  
-   Widok komunikuje się z warstwy za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interfejsu. Ten interfejs umożliwia uzgodnienia wyświetlanie współrzędnych z buforu współrzędnych.  
  
-   Wszelkie warstwy, takie jak warstwy syntetycznych tekstu, od którego pochodzi tekst podać lokalnego wdrożenia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>.  
  
-   Oprócz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, musi implementować warstwy tekstu <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> i wyzwalać zdarzeń w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kolorowania w edytorach niestandardowych](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Przy użyciu znaczników tekstu przy użyciu interfejsu API starsza wersja](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Dostosowywanie menu i formanty edytora przy użyciu interfejsu API starsza wersja](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)