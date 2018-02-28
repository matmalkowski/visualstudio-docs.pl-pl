---
title: "Języki zawarte | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bfdbc3d1c0e7bbc0b3dc712d9434ca1b49c6feca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="contained-languages"></a>Języki zawarte
*Języki zawarte* języków, które są zawarte w innych językach. Na przykład HTML w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] strony mogą zawierać [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] skryptów. Architektura podwójnego języka jest wymagana do zapewnienia funkcji IntelliSense, kolorowania i inne funkcje edycji HTML i język skryptowy edytora plików aspx.  
  
## <a name="implementation"></a>Implementacja  
 Interfejs najważniejszych, należy wdrożyć zawartych w niej języków jest <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejsu. Ten interfejs jest wdrażany za pomocą dowolnego języka, która może znajdować się wewnątrz podstawowy język. Go zapewnia dostęp do usługi języka colorizer filtru widoku tekstu i identyfikator języka głównej usługi. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> Umożliwia tworzenie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejsu. Poniższe kroki pokazują, jak zaimplementować zawartych w niej języka:  
  
1.  Użyj `QueryService()` uzyskać języka identyfikator usługi i identyfikator interfejsu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> metodę w celu utworzenia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejsu. Przekaż <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu, identyfikator elementu (co najmniej jednego <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>, <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>, lub <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>) i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfejsu.  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Interfejs, który jest obiektem koordynatora buforu tekstu, udostępnia podstawowe usługi, które są wymagane do mapowania lokalizacji w podstawowym pliku do buforu dodatkowej języka.  
  
     Na przykład w pliku .aspx pojedynczy plik podstawowy zawiera ASP, HTML i kod, który jest zawarty. Bufor dodatkowej zawiera jednak tylko zawartych w niej kod, wraz z żadnych definicji klas, aby dodatkowej buforu plik prawidłowy kod. Koordynator buforu obsługuje pracy koordynacji edycji z buforu do drugiego.  
  
4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Metodę, która jest podstawowy język, informuje koordynatora buforu tekst w swoim buforze jest mapowany na odpowiedni tekst w buforze dodatkowej.  
  
     Język przekazywany w tablicy <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> struktury, która obecnie zawiera tylko podstawowym i pomocniczym zakres.  
  
5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> — Metoda i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> metody podać mapowanie podstawowej do dodatkowej buforu i na odwrót.