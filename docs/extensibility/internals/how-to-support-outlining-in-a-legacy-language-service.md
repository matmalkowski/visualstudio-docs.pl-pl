---
title: "Porady: Obsługa konspekt w starsza wersja usługi języka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa57b0d09cb8422a9dde1f70306d2f3808b0384e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Porady: Obsługa konspekt w starsza wersja usługi języka
Tworzenie konspektu służy do rozwiń lub Zwiń różnych regionach tekstu. Sposób tworzenia konspektu służy może być określony inaczej w różnych językach. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](../../ide/outlining.md).  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej o nowy sposób, aby zaimplementować zwijania, zobacz [wskazówki: Tworzenie konspektu](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
 Poniżej pokazano, jak obsługiwać tego polecenia dla usługi języka.  
  
### <a name="to-support-outlining"></a>Do obsługi, obramowanie  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> na obiekt usługi języka.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> dla bieżącego zwijania obiektu sesji można dodać nowych konspektu regionów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Gdy użytkownik wybierze **Zwiń do definicji** na **Tworzenie konspektu** menu, wywołania IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> w usłudze języka.  
  
 Gdy ta metoda jest wywoływana, IDE przekazuje w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> kursor (wskaźnik do buforu tekstu) i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (wskaźnik do bieżącej sesji zwijania).  
  
 Możesz wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> metodę dla wielu regionach konspektu przez określenie tych regionów, w `rgOutlnReg` parametru. `rgOutlnReg` Jest parametr <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> struktury. Ten proces pozwala określić różne charakterystyki ukryte regionu, takich jak czy rozwinięte lub zwinięte danego regionu.  
  
> [!NOTE]
>  Należy rozważnie ukrycie znaki nowego wiersza. Ukryty tekst powinien być rozszerzany także od początku pierwszego wiersza do ostatniego znaku ostatni wiersz w sekcji, pozostawiając widoczne ostatni znak nowego wiersza.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: zapewniają obsługę tekstu ukrytego w starsza wersja usługi języka](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Instrukcje: zapewnianie rozszerzonej obsługi zwijania w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)