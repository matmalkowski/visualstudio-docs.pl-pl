---
title: Dostosowywanie kodu systemu Windows przy użyciu interfejsu API starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8284985003415ef3e723fe735e64481c3666180a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Dostosowywanie kodu systemu Windows przy użyciu interfejsu API starsza wersja
Okno kodu jest obiekt okno dokumentu, który obsługuje co najmniej jeden widok tekstu. Dokładne funkcje okna kodu są zależne od usługi skojarzone języka. W trybie interfejsu wielu dokumentów (MDI) w oknie Kod jest ramki podrzędnych MDI.  
  
 Kod systemu windows są kontrolowane przez usługi języka i każdej usługi języka umożliwia Menedżera okien własny kod. Dzięki temu usługa języka dodać własne skojarzenia do okna kodu, takie jak zygzaki, kolorowania i inne. Aby uzyskać więcej informacji o sposobie tworzenia okna core, zobacz [uruchamianiu Core edytora za pomocą interfejsu API starszych](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Okno Kod jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiekt widoku tekstu i wszelkie skojarzenia ulokowany w obiekcie. Podczas tworzenia okna kodu podczas tworzenia Twojej wystąpienia podstawowego edytora, można dołączyć usługi języka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> do okna Kod jest tak jak pokazano na poniższej ilustracji.  
  
 ![CodeWindow — grafika](../extensibility/media/vscodewindow.gif "vscodewindow")  
W oknie kodu  
  
 Usługa języka implementuje Menedżera okien kodu i jest odpowiedzialny za zarządzanie elementy dodatkowe, takie jak pasek listy rozwijanej. Kod wywołuje okno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metody podczas inicjowania okna kodu. Gdy to wywołanie usługi języka można dodać pasek listy rozwijanej lub przycisk (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) do okna kodu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 `Customizing Code Windows by Using the Legacy API`  
 Opis sposobu dostosowywania kodu systemu windows za pomocą starszej wersji interfejsu API.  
  
 [Porady: hostowanie edytora w innym edytorze](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Wyjaśniono, jak udostępniać drugi edytora w oknie edytora.  
  
 [Porady: wyzwalać zdarzeń, gdy Edytor traci fokus](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Wyjaśniono, jak dołączyć widok dokumentu na obiekt danych dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Tworzenie wystąpień Edytor Core przy użyciu interfejsu API starsza wersja](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Uzyskiwanie dostępu do theText widoku przy użyciu interfejsu API starsza wersja](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)