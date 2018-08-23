---
title: Typ wizualizatora i Przeglądarka niestandardowa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d347e7b18722aa8f8901abac3966150b3dca97cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42672246"
---
# <a name="type-visualizer-and-custom-viewer"></a>Wizualizator typów i przeglądarka niestandardowa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Wizualizator typów i Przeglądarka niestandardowa](https://docs.microsoft.com/visualstudio/extensibility/debugger/type-visualizer-and-custom-viewer).  
  
Wizualizator typów jest składnikiem, który wyświetla część danych w bardzo specyficznym formacie. Ten format jest całkowicie maksymalnie implementujący wizualizatora, użytkownik końcowy lub dostawcą wizualizatorów innych firm.  
  
 Przeglądarka niestandardowa jest częścią ewaluatora wyrażeń niestandardowych, które wyświetla część danych w formacie bardzo szczegółowych. Ten format jest całkowicie maksymalnie implementujący niestandardowe podglądu, co oznacza, że format jest maksymalnie implementujący programu expression evaluator (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Obsługa Wizualizatorów typu w ewaluatora wyrażeń  
 EE może obsługiwać wizualizatorów typu dzięki obsłudze zbiór interfejsów, które są dostępne do wizualizatorów: interfejsy, takie jak [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) i [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Należy jednak pamiętać, że EE nie jest odpowiedzialne za wykonanie Wizualizator typów, sama: EE jedynie zezwala na zewnętrzne wizualizatorów dostęp do informacji o typie. Takie wizualizatorów może dostarczany wraz z EE i zainstalowane w odpowiednim miejscu w programie Visual Studio, dostarczone przez innego dostawcę innych firm lub nawet przez użytkownika końcowego.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Obsługa przeglądarek niestandardowych w ewaluatora wyrażeń  
 EE może również obsługiwać przeglądarek niestandardowych, w których EE, sama dostarcza kod w celu wyświetlania typu danych. Przeglądarka niestandardowa implementuje [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfejs, który obsługuje wszystkie obowiązki wyświetlane dane w formacie, który lubisz jest pożądane; Podgląd ma pełną kontrolę nad wyświetlaniem oraz nawet umożliwić dane, które mają być modyfikowane. Wszelkie przeglądarek niestandardowych dostarczonych przez EE dołączone EE, gdy produkt jest wysyłany.  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)   
 [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

