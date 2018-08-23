---
title: Dostosowywanie kodu Windows za pomocą starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7738ef02b7f26e78197ca974fdc03b60c157799f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681617"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Dostosowywanie kodu Windows za pomocą starszej wersji interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Dostosowywanie Windows kodu za pomocą starszej wersji interfejsu API](https://docs.microsoft.com/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api).  
  
Okno kodu jest obiekt okna dokumentu, który obsługuje jeden lub więcej widoków tekstu. Dokładne funkcje okna kodu, zależą od usługi skojarzone języka. W trybie interfejsu wielu dokumentów (MDI) w oknie Kod jest podrzędna ramka MDI.  
  
 Kod systemu windows są kontrolowane przez usługi języka oraz każdej usługi w języka wprowadzić swój własny Menedżer okna kodu. Dzięki temu usługa językowa dodać własną zakończeń do okna kodu, takich jak faliste linie, kolorowanie i nie tylko. Aby uzyskać więcej informacji o tym, jak można utworzyć okna core, zobacz [wystąpienia Core edytora za pomocą starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Okno kodu jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiekt widoku tekstu i wszelkie zakończeń ulokowany w obiekcie. Podczas tworzenia okna kodu podczas konkretyzacji, rdzenia edytora, można dołączyć usługi języka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> do okna kodu, tak jak przedstawiono na poniższej ilustracji.  
  
 ![Grafika CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow")  
W oknie kodu  
  
 Usługa językowa implementuje Menedżera okien kodu i jest odpowiedzialny za zarządzanie zakończeń, takie jak pasek listy rozwijanej. Kod wywołuje okno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metody podczas inicjowania okna kodu. Po wykonaniu tego wywołania usługi językowej można dodać pasek listy rozwijanej lub przycisku (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) do okna kodu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 `Customizing Code Windows by Using the Legacy API`  
 Opis sposobu dostosowywania kodu systemu windows za pomocą starszej wersji interfejsu API.  
  
 [Instrukcje: hostowanie redaktorem w innym edytorze](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Wyjaśnia, jak hostować drugi edytora w oknie edytora.  
  
 [Porady: wyzwolenie zdarzenia po utracie fokusu przez Edytor](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Wyjaśnia, jak dołączyć widok dokumentu do obiektu danych dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Utworzenie wystąpienia podstawowy edytor za pomocą starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Dostęp do theText widoku przy użyciu starszej wersji interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

