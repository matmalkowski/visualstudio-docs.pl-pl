---
title: "Typ wizualizatora i podglądu niestandardowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80798887beee6116b3a93b5d8ec86b14269b5475
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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