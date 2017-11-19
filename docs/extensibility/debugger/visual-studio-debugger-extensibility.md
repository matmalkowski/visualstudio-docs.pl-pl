---
title: "Rozszerzalność debugera programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b9a14f95fbed47670b3c5b5db19e4e0e6b8ba074
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-debugger-extensibility"></a>Rozszerzalność debugera programu Visual Studio
Visual Studio zawiera debugera kodu źródłowego całkowicie interakcyjny, udostępnieniem wydajny i łatwy w użyciu narzędzia śledzeniu usterki w programie. Debuger ma pełnej obsługi języka Visual Basic, C#, C/C++ i JavaScript. Jednak w przypadku [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], która jest dostępna z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), innych języków programowania, może być obsługiwany w debugerze przy użyciu tej samej funkcji zaawansowanych.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuger ma debugowania składników, które są kolei, specyficzne dla języka debugowany wspólnej frontonu (czyli interfejsu użytkownika). Nowe języki, wszystkie, które są niezbędne do działu pomocy technicznej przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugera jest utworzenie niezbędne składniki wewnętrzne, takie jak aparat debugowania (DE). To miejsce [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] polega na.  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Obejmuje pełne odwołanie do wszystkich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementy wymagane do utworzenia nowego DE. Ponadto istnieją przykłady i samouczki, które ułatwią rozpoczęcie pracy.  
  
 Dla przykładu end-to-end języka systemu projektu z debugowaniem pomocy technicznej, zobacz [próbki IronPython](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 W poniższych sekcjach opisano sposób rozszerzyć debugera przy użyciu [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Opisano, co [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania ofert oraz instrukcje dotyczące instalowania zestawu SDK.  
  
 [Tworzenie aparat debugowania niestandardowych](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Dokumenty niestandardowy proces DE, od przygotowania programu do DE do odłączenia DE.  
  
 [Zapisywanie Ewaluator wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Wyjaśnia, czy należy napisać ewaluatora wyrażeń.  
  
 [Wybieranie strategii wdrażania aparat debugowania](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 W tym artykule omówiono implementowania Twojej DE.  
  
 [Odwołanie](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Dokumenty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowanie interfejsu API.  
  
 [Przykłady](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Zawiera łącza do zwykłej próbki ewaluatora wyrażenia środowiska uruchomieniowego języka i przykładowe aparat debugowania.
