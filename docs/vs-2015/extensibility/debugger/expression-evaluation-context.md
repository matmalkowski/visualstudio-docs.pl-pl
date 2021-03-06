---
title: Kontekst oceny wyrażeń | Dokumentacja firmy Microsoft
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
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fc2c2ecc4f7867c2ad39ba72f9edcb72c0935ce5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681454"
---
# <a name="expression-evaluation-context"></a>Kontekst oceny wyrażeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [oceny wyrażenia kontekstu](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluation-context).  
  
W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugowania **oceny wyrażenia kontekstu**:  
  
-   Reprezentuje kontekst do obliczenia wyrażenia. Ogólnie rzecz biorąc kontekst oceny odpowiada zakresie leksykalnym, w którym można obliczyć wartości zmiennych, parametrów, funkcje i metody. Na przykład oceny wyrażenia kontekstu skojarzonego z ramką stosu zapewni kontekście ocenianie zmiennych lokalnych, parametrów metod i składowych klasy (jeśli dotyczy).  
  
-   Występuje po zatrzymaniu w punkcie przerwania programu. Wyrażenia jest strukturą danych, reprezentujący przeanalizowany wyrażenie, które jest gotowe do powiązania i oceny w danym kontekście.  
  
     Bardziej szczegółowo wyrażenia są tworzone przy użyciu [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody. Gdy wyrażenie jest obliczane, generuje drukowalnych ciąg zawierający nazwę i typ zmiennej lub argumentu i jego wartość. Ten ciąg jest wyświetlany w oknie czujki lub okno zmiennych lokalnych w IDE.  
  
     Biorąc pod uwagę `BSTR` i [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu, aparat debugowania (DE) można utworzyć [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu, analizując wyrażenia. Biorąc pod uwagę `IDebugExpression2` interfejsu, DE może pobrać wartość do obliczenia wyrażenia synchroniczna lub asynchroniczna. Tę wartość, wraz z nazwą i typ zmiennej lub argumentu, są wysyłane do IDE do wyświetlenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy oceny wyrażenia](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Konteksty debugera](../../extensibility/debugger/debugger-contexts.md)

