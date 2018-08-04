---
title: Dostosowywanie kodu Windows za pomocą starszej wersji interfejsu API | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 454d58a48abafe9b23f8a812e5d40b9fc6477b50
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499357"
---
# <a name="customize-code-windows-by-using-the-legacy-api"></a>Dostosowywanie kodu systemu windows przy użyciu starszej wersji interfejsu API
Okno kodu jest obiekt okna dokumentu, który obsługuje jeden lub więcej widoków tekstu. Dokładne funkcje okna kodu, zależą od usługi skojarzone języka. W trybie interfejsu wielu dokumentów (MDI) w oknie Kod jest podrzędna ramka MDI.  
  
 Kod systemu windows są kontrolowane przez usługi języka oraz każdej usługi w języka wprowadzić swój własny Menedżer okna kodu. Dzięki temu usługa językowa dodać własną zakończeń do okna kodu, takich jak faliste linie, kolorowanie i nie tylko. Aby uzyskać więcej informacji o tym, jak można utworzyć okna core, zobacz [wystąpienia podstawowy edytor przy użyciu starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
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
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Utwórz wystąpienie podstawowy edytor przy użyciu starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Wyświetl theText dostępu przy użyciu starszej wersji interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)