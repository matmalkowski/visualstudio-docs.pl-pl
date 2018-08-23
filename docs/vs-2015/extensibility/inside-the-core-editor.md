---
title: W edytorze podstawowych | Dokumentacja firmy Microsoft
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
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2d9ec83c700f9166dc6b73860547bcacd265a15
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678549"
---
# <a name="inside-the-core-editor"></a>W edytorze podstawowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [w edytorze podstawowych funkcji programu](https://docs.microsoft.com/visualstudio/extensibility/inside-the-core-editor).  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytorze podstawowych funkcji to zbiór kilka składników, które pozwalają na modyfikowanie i wykonywania zapytań względem informacji tekstowych. Jeśli dostosowano podstawowy edytor przy użyciu starszej wersji interfejsu API, można nadal używać tych dostosowania, które będą kierowane za pośrednictwem karty edytora. Jest to zalecane, jednak dostosować własne dostosowania do edytora nowego interfejsu API.  
  
 Niektórych ważnych aspektów podstawowy edytor kwestie:  
  
-   Bufor tekstowy  
  
-   Widok tekstu  
  
-   W oknie kodu  
  
-   Znaczniki tekstu  
  
-   Menedżer tekstu  
  
-   Integracja z usługami języka  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Utworzenie wystąpienia podstawowy edytor za pomocą starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Instrukcje krok po kroku dotyczące sposobu korzystania <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> do utworzenia wystąpienia podstawowego edytora.  
  
 [Dostęp do buforu tekstowego przy użyciu starszej wersji interfejsu API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 W tym artykule omówiono rolę buforu tekstu w edytorze podstawowych, wyjaśnia skojarzone systemów, które umożliwiają dostęp do buforu i zawiera listę interfejsów implementowanych przez obiekt buforu tekstu, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Zdarzenia buforu tekstu w starszej wersji interfejsu API](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Zawiera listę interfejsów, które są używane dla powiadomień o zdarzeniach buforu tekstu.  
  
 [Porady: rejestrowanie zdarzeń buforu tekstu przy użyciu starszej wersji interfejsu API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Opisuje sposób poinformowania zdarzenia buforu tekstu.  
  
 [Za pomocą Menedżera tekstu do monitorowania ustawień globalnych](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 W tym artykule omówiono sposób Menedżer tekstu jest używany do udostępniania informacji preferencji globalnych podstawowe składniki edytora i jak otrzymywać powiadomienia o zdarzeniach Menedżer tekstu.  
  
 [Dostęp do theText widoku przy użyciu starszej wersji interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 W tym artykule opisano rolę widoku tekstu w edytorze podstawowych i wyświetla interfejsy implementowane przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiektu.  
  
 [Dostosowywanie kodu Windows za pomocą starszej wersji interfejsu API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Zawiera informacje dotyczące sposobu okna kodu jest używane, aby ująć widoku tekstu, w tym artykule omówiono, jak Menedżer okien kod służy do zapewnienia dekoracje do okna kodu i zapewnia powiadomienia o nowych widoków.  
  
 [Zmienianie ustawień widoku za pomocą starszej wersji interfejsu API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Instrukcje krok po kroku dotyczące wymusić ustawienia wyświetlania i usuwania ustawień wymuszone.  
  
 [Usługi języka oraz podstawowy edytor](../extensibility/language-services-and-the-core-editor.md)  
 W tym artykule opisano tworzenie wystąpienia usługi języka w celu kontroli kodu dekoracje.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wskazówki: Tworzenie edytora podstawowych i rejestrowania typu pliku w edytorze](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Instrukcje krok po kroku dotyczące uruchamiania podstawowy edytor z kodu zarządzanego.  
  
 [Listę rozwijaną paska](../extensibility/drop-down-bar.md)  
 W tym artykule omówiono sposób pasek listy rozwijanej jest używana w oknie kodu i opisano interfejsy, które są używane podczas implementowania pasek listy rozwijanej.  
  
 [Znaczniki tekstu przy użyciu starszej wersji interfejsu API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Wyjaśnia pojęcie znaczników tekstu i jak są one używane w edytorze podstawowych i wyświetla listę interfejsów, które są używane do dostępu i zarządzania znaczników tekstu.  
  
 [Porady: Dodawanie znaczników standardowy tekst](../extensibility/how-to-add-standard-text-markers.md)  
 Instrukcje krok po kroku dotyczące tworzenia znacznika tekstu i Dodaj polecenie niestandardowe do menu skrótów.  
  
 [Porady: Tworzenie niestandardowego tekstu znaczników](../extensibility/how-to-create-custom-text-markers.md)  
 Instrukcje krok po kroku dotyczące tworzenia znacznika niestandardowego tekstu i podać typ znacznika jako usługa.

