---
title: Kontekst oceny wyrażenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1fade5bb18e59a1b9b9e2655ce01b0b5559484e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099148"
---
# <a name="expression-evaluation-context"></a>Kontekst oceny wyrażenia
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugowania, **kontekst oceny wyrażenia**:  
  
-   Reprezentuje kontekst dla wyrażenia. Ogólnie rzecz biorąc kontekst oceny odpowiada leksykalne zakresu, w którym można obliczyć wartości zmiennych, parametry, funkcje i metody. Na przykład kontekst oceny wyrażenia ramki stosu zapewni kontekst oceny zmiennych lokalnych, parametrów metod i elementów członkowskich klasy (jeśli dotyczy).  
  
-   Występuje, gdy zostało zatrzymane w punkcie przerwania. Wyrażenia. jest to struktura danych reprezentujący przeanalizowany wyrażenia, który jest gotowy do powiązania i oceny w danym kontekście.  
  
     Bardziej szczegółowo wyrażenia są tworzone przy użyciu [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody. Wyrażenie jest obliczane, generuje drukowalnych ciąg zawierający nazwę i typ zmiennej lub argumentu i jego wartość. Ten ciąg jest wyświetlany w oknie wyrażeń kontrolnych lub w oknie zmienne lokalne IDE.  
  
     Podane `BSTR` i [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu, aparat debugowania (DE) można utworzyć [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu analizując wyrażenia. Podane `IDebugExpression2` interfejsu, DE może pobrać wartość za pomocą wyrażenia synchroniczna lub asynchroniczna. Ta wartość, oraz nazwę i typ zmiennej lub argumentu, są wysyłane do środowiska IDE do wyświetlenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Obliczanie wyrażenia](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)