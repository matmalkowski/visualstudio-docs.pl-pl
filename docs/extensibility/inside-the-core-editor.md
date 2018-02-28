---
title: W edytorze Core | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e4612f5779d6177d58cef7f087ef6e11bbe4ebd9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="inside-the-core-editor"></a>W edytorze Core
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Edytor core to zestaw kilka składników, które umożliwiają modyfikowanie i zapytania informacji tekstowych. Jeśli dostosowano Edytor core za pomocą starszej wersji interfejsu API, mogą nadal używać tych dostosowania, które zostaną przesłane za pośrednictwem karty edytora. Jest to zalecane, jednak dostosować własne dostosowania do edytora nowego interfejsu API.  
  
 Niektóre ważne kwestie związane z edytora podstawowe kwestie:  
  
-   Bufor tekstowy  
  
-   Wyświetlanie tekstu  
  
-   W oknie kodu  
  
-   Znacznikach tekstu  
  
-   Menedżera tekstu  
  
-   Integracja z usługami języka  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie wystąpień Edytor Core przy użyciu interfejsu API starsza wersja](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Zawiera instrukcje krok po kroku dotyczące sposobu używania <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> można utworzyć wystąpienia podstawowego edytora.  
  
 [Dostęp do buforu tekstu przy użyciu interfejsu API starsza wersja](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 W tym artykule omówiono rolę buforu tekstu w edytorze core, wyjaśnia skojarzone systemów, które umożliwiają dostęp do buforu i zawiera listę interfejsy implementowane przez obiekt buforu tekstu, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Zdarzenia buforu tekstu w interfejsie API starsza wersja](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Lista interfejsów, które są używane dla powiadomień o zdarzeniach buforu tekstu.  
  
 [Porady: rejestrowanie zdarzeń buforu tekstu przy użyciu interfejsu API starsza wersja](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Opisuje sposób poinformowania zdarzenia buforu tekstu.  
  
 [Za pomocą Menedżera tekstu do monitorowania ustawień globalnych](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Omówiono sposób Menedżera tekstu jest używany do udostępniania informacji preferencji globalnych podstawowe składniki edytora i jak otrzymywać powiadomienia o zdarzeniach Menedżera tekstu.  
  
 [Uzyskiwanie dostępu do theText widoku przy użyciu interfejsu API starsza wersja](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Zawiera opis roli widoku tekstu w edytorze rdzeni i wyświetla interfejsy implementowane przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiektu.  
  
 [Dostosowywanie kodu systemu Windows przy użyciu interfejsu API starsza wersja](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Zawiera informacje o jak okno kodu zostanie użyty do umieszczenia widoku tekstu, w tym artykule omówiono, jak kod Menedżera okien służy do zapewnienia dekoracje do okna Kod i zapewnia powiadomienia o nowych widoków.  
  
 [Zmiana ustawień widoku przy użyciu interfejsu API starsza wersja](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Instrukcje krok po kroku dotyczące wymusić ustawienia widoku i Usuń ustawienia wymuszone.  
  
 [Usługi językowe i Edytor Core](../extensibility/language-services-and-the-core-editor.md)  
 W tym artykule opisano tworzenie wystąpienia usługi języka aby dekoracje kod sterowania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wskazówki: Tworzenie edytora rdzeni i rejestrowania edytora typu pliku](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Instrukcje krok po kroku dotyczące uruchamiania edytora core z kodu zarządzanego.  
  
 [Rozwijany pasek](../extensibility/drop-down-bar.md)  
 Omówiono sposób pasek listy rozwijanej jest używana w oknie kodu i opisuje interfejsy, które są używane podczas implementowania pasek listy rozwijanej.  
  
 [Przy użyciu znaczników tekstu przy użyciu interfejsu API starsza wersja](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Wyjaśnia pojęcie znacznikach tekstu i sposób ich użycia w edytorze core, a lista interfejsów, które są używane do dostępu i zarządzanie znacznikach tekstu.  
  
 [Porady: Dodawanie znaczników tekstu standardowego](../extensibility/how-to-add-standard-text-markers.md)  
 Instrukcje krok po kroku dotyczące tworzenia znacznika tekstu i Dodawanie polecenia niestandardowego do menu skrótów.  
  
 [Porady: Tworzenie niestandardowego tekstu znaczników](../extensibility/how-to-create-custom-text-markers.md)  
 Instrukcje krok po kroku dotyczące tworzenia znacznik niestandardowy tekst i udostępniają typ znacznika jako usługa.