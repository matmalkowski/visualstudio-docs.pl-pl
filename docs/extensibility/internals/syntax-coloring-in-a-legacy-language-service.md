---
title: "Kolorowania w usłudze języka starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88af397feba9b06eabd73ec23dcf1204ebe755e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Kolorowania w starsza wersja usługi języka
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]przy użyciu usługi kolorowanie zidentyfikować elementy języka i wyświetlić je z określonego kolorów w edytorze.  
  
## <a name="colorizer-model"></a>Colorizer Model  
 Implementuje usługi języka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs, który jest następnie używany przez edytory. Ta implementacja jest oddzielny obiekt usługi języka, jak pokazano na poniższej ilustracji.  
  
 ![Grafika SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Proste colorizer modelu  
  
> [!NOTE]
>  Kolorowania usługi różni się od ogólnych [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mechanizm Kolorowanie tekstu. Aby uzyskać więcej informacji na temat ogólnych [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mechanizm obsługi oznaczanie kolorami, zobacz [przy użyciu czcionek i kolorów](../../extensibility/using-fonts-and-colors.md).  
  
 Oprócz colorizer usługi języka może dostarczyć niestandardowe colorable elementy, które są używane przez Edytor przez podaje niestandardowe elementy colorable reklamy. Można to zrobić z zastosowaniem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfejsu na ten sam obiekt, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejsu. Zwraca liczbę niestandardowych elementów colorable, gdy Edytor wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> — metoda która zwraca pojedynczy element colorable niestandardowych podczas wywołania edytor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> — metoda.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Metoda zwraca obiekt, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfejsu. Jeśli usługa języka obsługuje koloru 24-bitowego lub wysokiej wartości, musi on implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsu na ten sam obiekt jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfejsu.  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Jak pakiet VSPackage używa Colorizer usługi języka  
  
1.  Pakiet VSPackage musi pobrać usługę odpowiedni język, który wymaga usługi języka pakiet VSPackage wykonywać następujące czynności:  
  
    1.  Użyj implementacja obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejsu, aby uzyskać tekst, który ma być pokolorowane.  
  
         Tekst jest zwykle wyświetlany przy użyciu obiektu implementującego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu.  
  
    2.  Pobierz usługi języka badając dostawcę usługi w pakiecie VSPackage usługi języka identyfikator GUID. Usługi językowe są identyfikowane w rejestrze przez rozszerzenie pliku.  
  
    3.  Skojarz usługi języka z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> przez wywołanie jego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody.  
  
2.  Pakiet VSPackage można teraz uzyskać i użyj obiektu colorizer w następujący sposób:  
  
    > [!NOTE]
    >  Nie masz VSPackages, które za pomocą edytora core uzyskać języka, obiekty colorizer usługi jawnie. Jak wystąpienie edytora core uzyskuje usługi odpowiedni język, wykonuje wszystkie zadania kolorowania pokazano poniżej.  
  
    1.  Uzyskaj obiekt colorizer usługi języka, który implementuje `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer`, i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> interfejsów, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody dla usługi języka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> obiektu.  
  
    2.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę, aby uzyskać informacje colorizer dla określonego zakresu tekstu.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Zwraca tablicę wartości, po jednej dla każdego znaku w zakres tekstu jest pokolorowane. Wartości są indeksów do listy elementów colorable domyślnej listy colorable elementu obsługiwane przez Edytor rdzeni lub listę niestandardowego elementu colorable obsługiwanego przez sama usługa języka.  
  
    3.  Skorzystaj z informacji kolorowania zwrócony przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę w celu wyświetlenia zaznaczonego tekstu.  
  
> [!NOTE]
>  Oprócz używania colorizer usługi języka, pakiet VSPackage służy ogólnego przeznaczenia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tekstu kolorowania mechanizmu. Aby uzyskać więcej informacji na temat ten mechanizm, zobacz [przy użyciu czcionek i kolorów](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie kolorowanie składni](../../extensibility/internals/implementing-syntax-coloring.md)  
 W tym artykule omówiono, jak edytor uzyskuje dostęp do, kolorowanie składni i usługa języka musi wdrożenie do obsługi składni kolorowania usługi języka.  
  
 [Porady: używanie wbudowanych elementów Colorable](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Pokazuje, jak użyć wbudowanych elementów colorable z usługi języka.  
  
 [Niestandardowe elementy Colorable](../../extensibility/internals/custom-colorable-items.md)  
 W tym artykule omówiono implementowania niestandardowych elementów colorable.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie czcionek i kolorów](../../extensibility/using-fonts-and-colors.md)