---
title: Model usługi języka starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 943f0f013045e3082af3069ed4d45aaed1096869
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131592"
---
# <a name="model-of-a-legacy-language-service"></a>Model usługi języka starsza wersja
Usługa języka definiuje elementy i funkcje w określonym języku i służy do zapewnienia edytor z użyciem informacji specyficznych dla danego języka. Na przykład edytor musi znać elementów i słów kluczowych języka aby zapewnić obsługę kolorowanie składni.  
  
 Usługa języka ściśle współpracuje z buforu tekstu zarządzane przez Edytor i widok, który zawiera edytor. Microsoft IntelliSense **szybka podpowiedź** opcja jest przykład funkcji udostępnianych przez usługę języka.  
  
## <a name="a-minimal-language-service"></a>Usługa języka minimalnego  
 Najbardziej podstawowa usługa języka zawiera dwa następujące obiekty:  
  
-   *Usługi języka* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejsu. Usługa języka zawiera informacje na temat języka, w tym nazwę, rozszerzenia nazw plików, Menedżera okien kodu i colorizer.  
  
-   *Colorizer* implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejsu.  
  
 Następujący rysunek koncepcyjny pokazuje modelu usługi podstawowy język.  
  
 ![Grafika przedstawiająca usługi Model języka](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Podstawowy język modelu usług  
  
 Hosty okno dokumentu *widok dokumentu* edytora, w tym przypadku [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] core edytora. Widok dokumentu i bufor tekstowy są własnością edytora. Te obiekty pracować z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] za pomocą okna Dokument specjalistycznych o nazwie *okna kodu*. W oknie kod znajduje się w <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiekt, który jest tworzony i kontrolowane przez IDE.  
  
 Podczas ładowania pliku z rozszerzeniem danego Edytor lokalizuje usługi języka skojarzony z tym rozszerzeniem i przekazuje do niego okna kodu przez wywołanie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metody. Zwraca usługi języka *Menedżera okien kodu*, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interfejsu.  
  
 Poniższa tabela zawiera omówienie obiektów w modelu.  
  
|Składnik|Obiekt|Funkcja|  
|---------------|------------|--------------|  
|Bufor tekstowy|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Unicode odczytu/zapisu strumienia tekstu. Istnieje możliwość tekstu użyć innego kodowania.|  
|W oknie kodu|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Okno dokumentu, który zawiera co najmniej jeden widok tekstu. Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest w trybie interfejsu wielu dokumentów (MDI) w oknie Kod jest formularz podrzędny MDI.|  
|Wyświetlanie tekstu|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Okno, które umożliwia użytkownikowi Nawigacja i wyświetlanie tekstu przy użyciu klawiatury i myszy. Widoku tekstu jest wyświetlana użytkownikowi jako edytora. Korzystania z widoków tekst okna edytora zwykłej, w oknie danych wyjściowych i w oknie bezpośrednim. Ponadto można skonfigurować co najmniej jeden widok tekstu w ramach okna kodu.|  
|Menedżera tekstu|Zarządzane przez <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> usługi, z którego można uzyskać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> wskaźnika|Składnik, który zachowuje wspólne informacje współużytkowane przez wszystkie elementy opisane wcześniej.|  
|Usługa języka|Implementacja zależnych; implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Obiekt zawierający informacje specyficzne dla języka wyróżnianie składni, uzupełnianie i pasujących nawiasów klamrowych edytora.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dane dokumentu i widok dokumentu w edytorach niestandardowych](../../extensibility/document-data-and-document-view-in-custom-editors.md)