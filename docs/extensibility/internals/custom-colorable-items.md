---
title: Niestandardowe elementy Colorable | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 78c4823e3644dc755cef518dcbbba5f42c7aebc1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="custom-colorable-items"></a>Niestandardowe elementy Colorable
Lista typów można zastąpić oznaczanie kolorami, na przykład słowa kluczowe i komentarze, implementując niestandardowe elementy colorable jako część usługi języka.  
  
## <a name="user-settings-of-colorable-items"></a>Ustawienia użytkownika Colorable elementów  
 Można wyświetlić **czcionki i kolory** okno dialogowe, wybierając **opcje** na **narzędzia** menu, a następnie wybierając **czcionki i kolory** w obszarze **środowiska**. Po wybraniu wyświetlania, takich jak **Edytor tekstu** lub **okno polecenia**, **wyświetlania elementów** pole listy zawiera wszystkie elementy colorable dla tego ekranu. Możesz wyświetlić i zmienić czcionkę, rozmiar, kolor pierwszego planu i kolor tła dla każdego elementu colorable. Wybrane opcje są przechowywane w pamięci podręcznej w rejestrze i nazwa elementu colorable z niego.  
  
## <a name="presentation-of-colorable-items"></a>Prezentacja Colorable elementów  
 Ponieważ IDE obsługuje zastąpienia użytkownika colorable elementów **czcionki i kolory** okno dialogowe, należy tylko podać każdego niestandardowego elementu colorable z nazwą. Ta nazwa jest wyświetlana w **wyświetlania elementów** listy. Colorable elementy wyświetlane w kolejności alfabetycznej. Grupować elementy colorable niestandardowe usługi języka, możesz rozpocząć każdej nazwie nazwę języka, na przykład **NewLanguage — komentarz** i **NewLanguage — słowo kluczowe**.  
  
> [!CAUTION]
>  Nazwa języka należy uwzględnić w nazwie elementu colorable w celu uniknięcia konfliktów z już istniejącymi nazwami colorable elementu. Jeśli zmienisz nazwę jednego z elementów colorable podczas tworzenia, należy zresetować pamięci podręcznej, który został utworzony przy pierwszym uruchomieniu korzystał colorable elementów. Możesz przywrócić eksperymentalne pamięci podręcznej za pomocą narzędzia CreateExpInstance, który jest instalowany z programu Visual Studio SDK, zwykle w katalogu  
>   
>  **C:\Program pliki (x86) \Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
>  Aby zresetować pamięć podręczną, należy wywołać `CreateExpInstance /Reset`. Aby uzyskać więcej informacji o CreateExpInstance, zobacz [CreateExpInstance narzędzie](../../extensibility/internals/createexpinstance-utility.md).  
  
 Pierwszy element na liście elementów colorable nigdy nie jest wywoływany. Pierwszy element odpowiada indeks elementu colorable 0, a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawsze dostarcza domyślne kolory tekstu i atrybuty dla tego elementu. Najprostszym sposobem zajmowanie się ten element, której nie istniały odwołania jest przydzielenie elementu colorable symbolu zastępczego na liście jako pierwszy element.  
  
## <a name="implementing-custom-colorable-items"></a>Implementowanie niestandardowych elementów Colorable  
  
1.  Definiowanie, co kolorowane w określonym języku, na przykład słów kluczowych, Operator i identyfikator.  
  
2.  Utwórz wyliczenie te elementy colorable.  
  
3.  Skojarz typy tokenów zwrócony z analizatora lub skanera z wartości wyliczenia.  
  
     Na przykład wartości reprezentujących typy tokenów, może być takie same wartości w wyliczeniu niestandardowe elementy colorable.  
  
4.  W implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody w Twojej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> obiektów, wypełnienie listy atrybuty wartości z wyliczenia niestandardowe elementy colorable odpowiadający typy tokenów zwrócony z analizatora lub skanera.  
  
5.  W tej samej klasy, która implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfejsu, implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfejsu i dwie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6.  Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> interfejsu.  
  
7.  Do obsługi wartości 24-bitowego lub wysoki kolorów, również należy wdrożyć <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsu.  
  
8.  W obiekt usługi języka, należy utworzyć listę zawierającą Twojej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> obiektów, dla każdego elementu colorable zidentyfikuje skanera lub analizatora.  
  
     Przy użyciu odpowiedniej wartości z wyliczenia niestandardowe elementy colorable można uzyskać dostępu do każdego elementu na liście. Użyj wartości wyliczenia jako indeks w liście. Pierwszy element na liście nigdy nie jest dostępne, ponieważ odpowiadający mu tekst domyślny styl [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawsze obsługuje samej siebie. Można zniwelować to przez wstawienie elementu colorable symbolu zastępczego na początku listy.  
  
9. W implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metoda zwraca liczbę elementów na liście elementów colorable niestandardowych.  
  
10. W implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metody zwrócić colorable żądany element z listy.  
  
 Przykład sposobu wdrażania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsów, temacie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## <a name="see-also"></a>Zobacz też  
 [Model usługi języka starsza wersja](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Kolorowania w edytorach niestandardowych](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Kolorowania w starsza wersja usługi języka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementowanie kolorowanie składni](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Instrukcje: korzystanie z wbudowanych elementów z możliwością kolorowania](../../extensibility/internals/how-to-use-built-in-colorable-items.md)