---
title: "Interfejsy usługi starszej wersji języka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 925b504d8cba4813631d4f8ba6f7dbd9750f5eae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-interfaces"></a>Interfejsy usługi starszej wersji języka
Dla określonego języka programowania jednocześnie może istnieć tylko jedno wystąpienie usługi języka. Jednak usługa jeden język może obsługiwać więcej niż jeden z nich.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kojarzy z dowolnego edytora określonego usługi języka. Dlatego w przypadku żądania operacji usługi języka, należy zidentyfikować odpowiedniego edytora jako parametr.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Wspólnych interfejsów związanych z usługami języka  
 Edytor pobiera usługi języka, wywołując <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> na odpowiedni pakiet VSPackage. Identyfikator przekazano to wywołanie usługi identyfikuje żądanej usługi języka.  
  
 Interfejsy usługi języka core można wdrożyć na dowolnej liczbie osobnych klas. Jednak typowym podejściem jest implementować następujące interfejsy w jednej klasy:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock>(opcjonalnie)  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Interfejs musi zostać wdrożone na wszystkich usług języka. Zawiera informacje dotyczące usługi języka, takie jak nazwa zlokalizowanego języka rozszerzeń nazw plików, które są skojarzone z usługi języka oraz jak pobierać colorizer.  
  
## <a name="additional-language-service-interfaces"></a>Interfejsy usługi dodatkowych języków  
 Można podać inne interfejsy przy użyciu usługi języka. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]żąda oddzielnego wystąpienia te interfejsy, dla każdego wystąpienia buforu tekstowego. W związku z tym należy zaimplementować każdego z tych interfejsów we własnym obiekcie. W poniższej tabeli przedstawiono interfejsów, które wymagają jedno wystąpienie każdego wystąpienia buforu tekstu.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Zarządza skojarzenia okna kodu, takie jak pasek listy rozwijanej. Ten interfejs można uzyskać za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> metody. Istnieje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> na okna kodu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Kolorowania słów kluczowych języka i ograniczników. Ten interfejs można uzyskać za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>jest wywoływana w czasie malowania. Unikaj kolejkowego obliczeń wewnątrz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> lub wydajność może się pogorszyć.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Zawiera elementy ToolTip parametru IntelliSense. Gdy usługa języka rozpoznaje znak, który wskazuje danych metody powinny być wyświetlane, takie jak nawias otwierający wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodę, aby powiadomić tekst widok usługi języka jest gotowy wyświetlić etykietkę informacji parametru. Widok tekstu następnie wywołuje do usługi języka przez przy użyciu metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfejsu można pobrać informacji wymaganych do wyświetlenia wskazówki.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Udostępnia instrukcji IntelliSense. Kiedy usługa języka jest gotowy do wyświetlenia listy uzupełniania, wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody w widoku tekstu. Widok tekstu następnie wywołuje do usługi języka przez przy użyciu metod na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> obiektu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Umożliwia zmianę widoku tekstu przy użyciu programu obsługi poleceń. Klasy należy zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> również musi implementować interfejs <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Pobiera widoku tekstu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> obiektu badając <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiektu, która została przekazana do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody. Powinny istnieć jedna <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> obiekt dla każdego widoku.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Przechwytuje poleceń, że użytkownik wpisze w oknie kodu. Monitorowanie danych wyjściowych z Twojej <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementacji, aby podać informacje o niestandardowych ukończenia i wyświetlić modyfikacji<br /><br /> Aby przekazać z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekt widoku tekstu, wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie usługi języka starsza wersja](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Lista kontrolna: Tworzenie starsza wersja usługi języka](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)