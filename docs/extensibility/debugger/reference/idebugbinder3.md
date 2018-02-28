---
title: IDebugBinder3 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 43465f919806f16154b8f3328aad7496c83ec235
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs umożliwia dostęp do typów, aliasy i usług niestandardowego wizualizatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania implementuje ten interfejs obsługuje aliasów, niestandardowego wizualizatora usług i dostęp do informacji o typie obiektu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfejsu uzyskuje ten interfejs, za pomocą [QueryInterface](/cpp/atl/queryinterface).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz metody udostępniane przez [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfejsu, tego interfejsu implementuje następujące:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Pobiera obiekt pamięci reprezentująca pamięci, z którym powiązany jest ten obiekt.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Pobiera wyjątek skojarzone z tym obiektem (jeśli istnieje)|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Pobiera alias otrzymuje jej nazwę|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Pobiera tablicę wszystkie aliasy dla tego obiektu|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Pobiera liczbę typy argumentów skojarzone z tym obiektem|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Pobiera listę typów argumentu skojarzone z tym obiektem|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Pobiera interfejs do usługi wizualizatora|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Konwertuje lokalizacji obiektu lub adres pamięci 64-bitowej do kontekstu pamięci.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Obliczanie wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)