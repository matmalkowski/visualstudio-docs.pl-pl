---
title: Rozwijany pasek | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7058c0b93cd0ff4afb2a13b625cd7ef034b03699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="drop-down-bar"></a>Rozwijany pasek
Pasek listy rozwijanej jest dostępne w górnej części okna kodu i zawiera dwie listy rozwijanej.  
  
## <a name="drop-down-bar-interfaces"></a>Rozwijany pasek interfejsów  
 W [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], na przykład pasek lista rozwijana zawiera listami [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] elementów i [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] elementy członkowskie funkcje, jak pokazano na poniższej ilustracji.  
  
 ![Usuń &#45; dół paski](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Rozwijany pasek  
  
 Podczas implementowania pasek listy rozwijanej, istnieją cztery interfejsów podstawowe znaczenie:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementuje ten interfejs do wstawiania zawartości paska listy rozwijanej. Każdej kombinacji z listy rozwijanej mogą zawierać tekst ozdobne lub zwykły tekst (pogrubienie, podkreślenie lub kursywa), mogą mieć kolorowanie czcionki tekstu okna lub wygaszone limit czcionki kolorowania i opcjonalnie można podać małej mapy bitowej obok elementu listy rozwijanej. Podobnie jak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfejsu, bitmapy znajdują się na listach obrazów. Każda kombinacja listy rozwijanej może mieć listy inny obraz; Jednak każdy listy obrazów musi zawierać obrazy o tej samej wysokości. Ponadto przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> metody, można zapewnić etykietkę narzędzia dla każdej kombinacji.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Wywołać tego interfejsu, aby utworzyć lub zniszczyć pasek listy rozwijanej dla okna kodu. Ten interfejs mogą służyć do określenia, czy pasek listy rozwijanej jest już dołączony do okna kodu przez wywołanie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metody. Wywołanie <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Wywołanie interfejsu do bezpośredniego komunikowania się z listy rozwijanej paska. Ten interfejs umożliwia wymusić odświeżenie listy rozwijanej paska zawartość lub zmień wybrany w jednym z pola listy.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Jeśli zarejestrowano `ShowDropdownBarOption` w klucz rejestru usługi języka następnie Menedżera okna Kod należy monitorować to zdarzenie do synchronizacji z preferencje użytkownika dotyczące tego, czy powinien być wyświetlany pasek listy rozwijanej. Jeśli ta opcja nie zostanie zarejestrowany w klucz usługi języka, a następnie opcję, aby wyświetlić lub ukryć pasek listy rozwijanej jest wyłączona na **opcje** menu.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Dołączanie pasek listy rozwijanej do okna kodu  
 Aby dołączyć pasek listy rozwijanej do okna kodu podczas jego tworzenia, usługa języka należy dołączyć do listy rozwijanej pasek kiedy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metoda jest wywoływana. Jeśli wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metody wskazuje, że pasek listy rozwijanej jeszcze nie istnieje, a następnie wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Aby uzyskać dostęp do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> interfejsu, należy wywołać <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> wskaźnika zwrócony podczas Twojej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implementacji został dołączony.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie kodu systemu Windows przy użyciu interfejsu API starsza wersja](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Obsługa paska nawigacyjnego w starszej wersji usługi językowej](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)