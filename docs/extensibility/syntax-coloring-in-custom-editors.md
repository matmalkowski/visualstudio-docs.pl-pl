---
title: Kolorowania w edytorach niestandardowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18e087e82754244b7abda530f733a6047447f4a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139464"
---
# <a name="syntax-coloring-in-custom-editors"></a>Kolorowania w edytorach niestandardowych
Visual Studio SDK środowiska edytora, w tym edytorze core używanie usług języka Aby zidentyfikować określone elementy syntaktycznych i wyświetlić je z określonego kolorów dla widoku danego dokumentu.

## <a name="colorization-requirements"></a>Wymagania dotyczące kolorowania
 Wszystkie edytory implementacja usługi języka colorizer musi:

1.  Użyj implementacja obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> do zarządzania tekst, który ma być kolorowane i implementacja obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zapewnienie dokument widok tekstu.

2.  Uzyskać interfejsu z usługą konkretnego języka badając pakiet VSPackage dostawcy usług przy użyciu identyfikatora GUID identyfikujący usługi języków.

3.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody wdrażania obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>. Ta metoda kojarzy usługi języka z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pakiet VSPackage używa do zarządzania tekst, który ma być kolorowane implementacji.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Użycie edytora Core Colorizer usługi języka
 Gdy usługi języka za pomocą colorizer są uzyskiwane przez wystąpienie edytora core, analizy i renderowanie tekstu przez colorizer usługi języka odbywa się automatycznie bez żadnych dalszych interwencji ze strony użytkownika.

 IDE sposób niewidoczny dla użytkownika:

-   Wywołuje colorizer zgodnie z potrzebami, aby przeanalizować i analizować tekstu, ponieważ dodane lub zmodyfikowane w implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.

-   Zapewnia, że wyświetlana dostarczonych przez widok dokumentów dostarczonych przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> implementacji jest aktualizowane i odowieżany, korzystając z informacji zwrócony przez colorizer.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Użycie edytora-core Colorizer usługi języka
 Edytor dodatkowe wystąpienia można również użyć usługi kolorowania składni usługi języka, ale jawnie musi pobrać i zastosować colorizer usługi i odświeżenia ich widoki samodzielnie.

 Aby to zrobić, Edytor-core musi:

1.  Uzyskaj obiekt colorizer usługi języka (które implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). Pakiet VSPackage robi to poprzez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody w interfejsie usługi języka.

2.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metoda żądania kolorowane określonego zakres tekstu.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Metoda zwraca tablicę wartości, po jednej dla każdej litery w tekście span trwa pokolorowane. Identyfikuje również zakres tekstu jako określonego typu elementu colorable, takiego jak komentarza, słowo kluczowe lub typ danych.

3.  Skorzystaj z informacji kolorowania zwrócony przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> do odświeżenia i wyświetl jego tekstu.

> [!NOTE]
> Oprócz przy użyciu usługi języka colorizer, pakiet VSPackage można używać mechanizmu ogólnego przeznaczenia tekstu kolorowania zestawu SDK środowiska Visual Studio. Aby uzyskać więcej informacji na ten mechanizm, zobacz [przy użyciu czcionek i kolorów](../extensibility/using-fonts-and-colors.md).

## <a name="see-also"></a>Zobacz też

- [Kolorowanie składni w starszej wersji usługi językowej](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementowanie kolorowania składni](../extensibility/internals/implementing-syntax-coloring.md)
- [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [Niestandardowe elementy z możliwością kolorowania](../extensibility/internals/custom-colorable-items.md)