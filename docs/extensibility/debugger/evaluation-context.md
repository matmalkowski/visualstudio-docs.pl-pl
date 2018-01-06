---
title: Kontekst oceny | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9a490ef7c4ea42fe85c291ee913d7ad5e1cda1bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="evaluation-context"></a>Kontekst oceny
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Gdy aparat debugowania (DE) wywołuje ewaluatora wyrażenia (EE), trzech argumentów przekazanych do [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ustalić kontekst Znajdowanie i ocena symbole, jak pokazano w poniższej tabeli.  
  
## <a name="arguments"></a>Argumenty  
  
|Argument|Opis|  
|--------------|-----------------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interfejs, który określa obsługi symboli (SH) ma być używany do identyfikowania symbolu.|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfejsu, który określa bieżącego punktu wykonania. To można znaleźć metody, który zawiera kod wykonywany.|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interfejsu, który może służyć do znajdowania wartości i typ symbolu podanej nazwy.|  
  
 `IDebugParsedExpression::EvaluateSync`Zwraca [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejs reprezentujący wartość wynikową i jej typie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenie klucza ewaluatora interfejsów](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)