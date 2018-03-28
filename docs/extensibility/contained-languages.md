---
title: Języki zawarte | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7ec180689f4dadfb60832259ddee51a05f336fda
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="contained-languages"></a>Języki zawarte

*Języki zawarte* języków, które są zawarte w innych językach. Na przykład HTML w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] strony mogą zawierać [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] skryptów. Architektura podwójnego języka jest wymagana do zapewnienia funkcji IntelliSense, kolorowania i inne funkcje edycji HTML i język skryptowy edytora plików aspx.

## <a name="implementation"></a>Implementacja

Interfejs najważniejszych, należy wdrożyć zawartych w niej języków jest <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejsu. Ten interfejs jest wdrażany za pomocą dowolnego języka, która może znajdować się wewnątrz podstawowy język. Go zapewnia dostęp do usługi języka colorizer filtru widoku tekstu i identyfikator języka głównej usługi. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> Umożliwia tworzenie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejsu. Poniższe kroki pokazują, jak zaimplementować zawartych w niej języka:

1.  Użyj `QueryService()` uzyskać języka identyfikator usługi i identyfikator interfejsu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2.  Aby utworzyć <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejsu, należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> metody. Przekaż <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu, co najmniej jeden [elementu identyfikatorów](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfejsu.

3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Interfejs, który jest obiektem koordynatora buforu tekstu, udostępnia podstawowe usługi, które są wymagane do mapowania lokalizacji w podstawowym pliku do buforu dodatkowej języka.

     Na przykład w pliku .aspx pojedynczy plik podstawowy zawiera ASP, HTML i kod, który jest zawarty. Jednak dodatkowej buforu obejmuje tylko zawartych w niej kod wraz z żadnych definicji klas, aby dodatkowej buforu plik prawidłowy kod. Koordynator buforu obsługuje pracy koordynacji edycji z buforu do drugiego.

4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Metodę, która jest podstawowy język, informuje koordynatora buforu tekst w swoim buforze jest mapowany na odpowiedni tekst w buforze dodatkowej.

     Język przekazywany w tablicy <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> struktury, która obecnie zawiera tylko podstawowym i pomocniczym zakres.

5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> — Metoda i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> metody podać mapowanie podstawowej do dodatkowej buforu i na odwrót.