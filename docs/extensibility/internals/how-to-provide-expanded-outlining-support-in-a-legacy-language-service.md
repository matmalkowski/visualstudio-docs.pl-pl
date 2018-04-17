---
title: Podaj określająca zakres wsparcia w usłudze języka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6467a1e3386daedc4a67aa420c06cf01187b8d22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>Porady: Podaj rozszerzona obsługa zwijania w starsza wersja usługi języka
Dostępne są dwie opcje do rozszerzania zwijania obsługę języka poza obsługi **Zwiń definicji** polecenia. Możesz dodać regionów kontrolowane przez Edytor konspektu i dodawanie regionów konspektu kontrolowane przez klienta.  
  
## <a name="adding-editor-controlled-outline-regions"></a>Dodawanie regionów kontrolowane przez Edytor konspektu  
 Użyj tej metody, aby Tworzenie konspektu regionu, a następnie zezwolić edytora do obsługi czy region jest rozwinięty, zwinięte i tak dalej. Dwie opcje zapewniające obsługę zwijania ta opcja jest najmniej niezawodny. Dla tej opcji, Utwórz nowy region konspektu w danym okresie określony tekst przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>. Po utworzeniu tego regionu jego zachowanie jest kontrolowana przez edytor. Użyj poniższej procedury do zaimplementowania konspektu kontrolowane przez Edytor regionów.  
  
#### <a name="to-implement-an-editor-controlled-outline-region"></a>Aby zaimplementować region kontrolowane przez Edytor konspektu  
  
1.  Wywołanie `QueryService` dla <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>  
  
     Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, przekazując wskaźnika buforu danego tekstu. Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiektu dla buforu.  
  
3.  Wywołanie <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> dla wskaźnika do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>.  
  
4.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> można dodać jeden lub więcej nowych konspektu regionów naraz.  
  
     Ta metoda służy do określenia zakresu tekstu do konturu, czy usunąć lub zachowane istniejących regionów konspektu i czy region konspektu jest rozwinięte lub zwinięte domyślnie.  
  
## <a name="adding-client-controlled-outline-regions"></a>Dodawanie regionów konspektu kontrolowane przez klienta  
 Użyj tej metody do implementacji kontrolowane przez klienta (lub inteligentne) określająca zakres, takiego jak używany przez [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] usługi języka. Usługa języka, który zarządza własną zwijania monitoruje zawartości buforu tekstu, aby zniszczyć stary regionów konspektu, gdy staje się nieprawidłowy i utworzyć nowe regiony konspektu zgodnie z potrzebami.  
  
#### <a name="to-implement-a-client-controlled-outline-region"></a>Aby zaimplementować region konspektu kontrolowane przez klienta  
  
1.  Wywołanie `QueryService` dla <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>. Zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, przekazując wskaźnika buforu danego tekstu. Określa, czy sesja ukryty tekst, który jest już istnieje dla buforu.  
  
3.  Jeśli sesja tekst, który jest już istnieje, a następnie trzeba utworzyć jedną i wskaźnika do istniejącej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiekt jest zwracany. This, wskaźnik umożliwia wyliczyć i tworzenie konspektu regionów. W przeciwnym razie wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> do utworzenia sesji ukrytego tekstu dla buforu. Wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> obiekt jest zwracany.  
  
    > [!NOTE]
    >  Podczas wywoływania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, można określić klienta tekstu ukrytego (to znaczy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> obiektu). Ten klient powiadamia użytkownika, gdy tekstu ukrytego lub konspektu region jest rozwinięte lub zwinięte przez użytkownika.  
  
4.  Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> struktury) parametru: Określ wartość <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> w `iType` członkiem <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury wskazująca tworzysz region konspektu zamiast ukryte regionu. Określ, czy region jest kontrolowane przez klienta lub kontrolowanych przez Edytor w `dwBehavior` członkiem <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Inteligentne implementacji zwijania może zawierać różnych regionach konspektu kontrolowane przez Edytor i klienta. Podaj tekst transparentu, który jest wyświetlany, gdy obszar konspektu jest zwinięte, takie jak "...", w `pszBanner` członkiem <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> struktury. Tekst transparentu domyślny edytor dla regionu ukryte jest "...".