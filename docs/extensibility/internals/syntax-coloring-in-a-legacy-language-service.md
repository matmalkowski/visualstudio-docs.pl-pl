---
title: Kolorowania w usłudze języka starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 172f06f4e30f1320b6e17332cb2b54af91f7ed01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Kolorowania w starsza wersja usługi języka

Program Visual Studio przy użyciu usługi kolorowanie zidentyfikować elementy języka i wyświetlić je z określonego kolorów w edytorze.

## <a name="colorizer-model"></a>Colorizer Model
 Implementuje usługi języka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs, który jest następnie używany przez edytory. Ta implementacja jest oddzielny obiekt usługi języka, jak pokazano na poniższej ilustracji:

 ![Grafika SVC Colorizer](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
>  Kolorowania usługi jest niezależna od ogólne mechanizm Visual Studio Kolorowanie tekstu. Aby uzyskać więcej informacji na temat ogólnych [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] mechanizm obsługi oznaczanie kolorami, zobacz [przy użyciu czcionek i kolorów](../../extensibility/using-fonts-and-colors.md).

 Oprócz colorizer usługa języka może dostarczyć niestandardowe colorable elementy, które są używane przez edytor, podaje niestandardowe elementy colorable reklamami. Można to zrobić z zastosowaniem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfejsu na ten sam obiekt, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejsu. Zwraca liczbę niestandardowych elementów colorable, gdy Edytor wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> — metoda która zwraca pojedynczy element colorable niestandardowych podczas wywołania edytor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> — metoda.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Metoda zwraca obiekt, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfejsu. Jeśli usługa języka obsługuje koloru 24-bitowego lub wysokiej wartości, musi on implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsu na ten sam obiekt jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfejsu.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>Jak pakiet VSPackage używa Colorizer usługi języka

1.  Pakiet VSPackage musi pobrać usługę odpowiedni język, który wymaga usługi języka pakiet VSPackage wykonywać następujące czynności:

    1.  Użyj implementacja obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejsu, aby uzyskać tekst, który ma być pokolorowane.

         Tekst jest zwykle wyświetlany przy użyciu obiektu implementującego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfejsu.

    2.  Pobierz usługi języka badając dostawcę usługi w pakiecie VSPackage usługi języka identyfikator GUID. Usługi językowe są identyfikowane w rejestrze przez rozszerzenie pliku.

    3.  Skojarz usługi języka z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> przez wywołanie jego <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody.

2.  Pakiet VSPackage można teraz uzyskać i użyj obiektu colorizer w następujący sposób:

    > [!NOTE]
    > VSPackages, które za pomocą edytora core, nie trzeba uzyskać języka, obiekty colorizer usługi jawnie. Jak wystąpienie edytora core uzyskuje usługi odpowiedni język, wykonuje wszystkie zadania kolorowania pokazano poniżej.

    1.  Uzyskaj obiekt colorizer usługi języka, który implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> interfejsów, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody dla usługi języka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> obiektu.

    2.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę, aby uzyskać informacje colorizer dla określonego zakresu tekstu.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Zwraca tablicę wartości, po jednej dla każdego znaku w zakres tekstu jest pokolorowane. Wartości są indeksów do listy elementów colorable domyślnej listy colorable elementu obsługiwane przez Edytor rdzeni lub listę niestandardowego elementu colorable obsługiwanego przez sama usługa języka.

    3.  Skorzystaj z informacji kolorowania zwrócony przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodę w celu wyświetlenia zaznaczonego tekstu.

> [!NOTE]
>  Oprócz używania colorizer usługi języka, pakiet VSPackage można również użyć ogólnego przeznaczenia Visual Studio tekstu kolorowania mechanizmu. Aby uzyskać więcej informacji na temat ten mechanizm, zobacz [przy użyciu czcionek i kolorów](../../extensibility/using-fonts-and-colors.md).

## <a name="in-this-section"></a>W tej sekcji
 [Implementowanie kolorowania składni](../../extensibility/internals/implementing-syntax-coloring.md) Discusses jak edytor dostęp do usługi języka kolorowanie składni i jakie usługi języka musi implementować do obsługi kolorowanie składni.

 [Porady: użycie wbudowanych elementów Colorable](../../extensibility/internals/how-to-use-built-in-colorable-items.md) pokazano, jak użyć wbudowanych elementów colorable z usługi języka.

 [Niestandardowe elementy Colorable](../../extensibility/internals/custom-colorable-items.md) omówiono sposób implementować niestandardowe elementy colorable.

## <a name="see-also"></a>Zobacz też

- [Używanie czcionek i kolorów](../../extensibility/using-fonts-and-colors.md)