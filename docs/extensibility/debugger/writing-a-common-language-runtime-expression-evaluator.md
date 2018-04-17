---
title: Pisanie wspólnej ewaluatora wyrażenia środowiska uruchomieniowego języka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ff2189bd80d2c5bbbc5253763e2ba07ef917d19
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Pisanie wspólnej ewaluatora wyrażenia środowiska uruchomieniowego języka
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ewaluator wyrażeń (EE) jest częścią aparat debugowania (DE), która obsługuje składni i semantykę języka programowania, wytworzonego kodu debugowany. W kontekście języka programowania, można obliczyć wyniku wyrażenia. Na przykład w przypadku niektórych języków wyrażenia "A + B" oznacza "suma A i B." W innych językach to samo wyrażenie może oznaczać "A lub b" W związku z tym oddzielnej EE musi być napisana dla każdego języka programowania, które generuje kod obiektu debugowanego w środowisku IDE programu Visual Studio.  
  
 Niektóre aspekty pakiet debugowania programu Visual Studio należy interpretować kod w kontekście języka programowania. Na przykład podczas wykonywania zatrzymany w punkcie przerwania, wszystkie wyrażenia, które użytkownik ma wpisane w **czujki** okna musi być obliczane i wyświetlane. Ponadto użytkownik może zmienić wartość zmiennej lokalnej przez wpisanie wyrażenia do **czujki** okna lub do **Immediate** okna.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Środowisko uruchomieniowe języka wspólnego i ocenianie wyrażeń](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Wyjaśniono, że podczas zastrzeżonych język programowania są integracji środowiska IDE programu Visual Studio, zapisywanie EE stanie obliczenia wyrażenia w kontekście zastrzeżonych języka umożliwia kompilacji na język pośredni firmy Microsoft (MSIL) bez pisania aparat debugowania.  
  
 [Architektura ewaluatora wyrażeń](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Omówiono sposób implementuje wymaganych interfejsów EE i Wywołaj wspólnego języka środowiska uruchomieniowego symbol dostawcy i interfejsy integratora.  
  
 [Rejestrowanie ewaluatora wyrażeń](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Zawiera informacje o tym, że EE musi zarejestrować się jako fabrykę klas środowiska CLR i środowiska wykonawcze programu Visual Studio.  
  
 [Implementowanie ewaluatora wyrażeń](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 W tym artykule opisano, jak proces obliczenia wyrażenia obejmuje aparat debugowania (DE), dostawca symbolu (SP) obiektu wiążącego i ewaluatora wyrażenia (EE).  
  
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)  
 W tym artykule opisano, jak to zrobić, gdy wstrzymuje wykonywanie, pakiet debugowania wywołuje DE, aby uzyskać listę zmiennych lokalnych i argumentów.  
  
 [Ocenianie wyrażenia okna wyrażeń kontrolnych](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Dokumenty, jak pakiet debugowania programu Visual Studio wywołuje DE, aby określić bieżącą wartość każde wyrażenie na liście czujki.  
  
 [Zmienianie wartości zmiennej lokalnej](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Wyjaśnia, w zmiana wartości lokalnej, każdego wiersza w oknie zmienne lokalne ma skojarzony obiekt, który zawiera nazwę, typ i bieżącą wartość zmiennej lokalnej.  
  
 [Implementowanie wizualizatorów typu i przeglądarek niestandardowych](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Wyjaśnia, które interfejs musi realizowane przez który składnik do obsługi wizualizatorach typu i niestandardowych przeglądarki.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)