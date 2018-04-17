---
title: Typ wizualizatora i podglądu niestandardowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d419130cd93c6cc2f7dcff132fdafc8986bfd30a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="type-visualizer-and-custom-viewer"></a>Typ wizualizatora i podglądu niestandardowego
Wizualizator typu jest składnik, który wyświetla element danych bardzo określonego formatu. Ten format jest całkowicie zależy implementujący wizualizatora, użytkownik końcowy i innych firm dostawcą wizualizatorów.  
  
 Podglądu niestandardowego jest częścią ewaluatora wyrażenia niestandardowego, zawierający element danych bardzo określonego formatu. Ten format jest całkowicie zależy implementujący niestandardowe podglądu, co oznacza, że format jest maksymalnie implementujący programu expression evaluator (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Obsługa Wizualizatorach typu w Ewaluatorze wyrażeń  
 EE może obsługiwać wizualizatorach typu dzięki obsłudze zestaw interfejsów dostępne dla wizualizatorów: interfejsy, takich jak [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) i [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Należy jednak pamiętać, że EE nie jest odpowiedzialny za wdrażanie samego wizualizatora typu: EE projektanci wizualizatorów zewnętrzny dostęp do informacji o typie. Takie wizualizatorów może dostarczony wraz z EE i zainstalowane w odpowiednim miejscu w programie Visual Studio, dostarczone przez innego dostawcę innych firm lub nawet przez użytkownika końcowego.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Obsługa niestandardowych przeglądarki w Ewaluatorze wyrażeń  
 EE może również obsługiwać niestandardowe przeglądarki, w których EE, sama dostarcza kod do wyświetlania typu danych. Implementuje podglądu niestandardowego [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfejsu, która obsługuje wszystkie obowiązki dane wyświetlane w dowolnym formacie jest pożądany; Podgląd ma pełną kontrolę nad wyświetlaniem, a także zezwolić danych ma być zmodyfikowana. Jeśli produkt jest wysyłany żadnych niestandardowych przeglądarek dostarczanych przez EE mają EE.  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)   
 [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)