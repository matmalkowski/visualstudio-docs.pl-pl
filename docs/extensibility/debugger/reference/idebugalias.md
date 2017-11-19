---
title: IDebugAlias | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias
helpviewer_keywords: IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 128dc9001faba06b1c95c5ebc364f319891ce409
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Reprezentuje alias liczbowa zmiennej. Alias jest po prostu inną nazwę zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń (EE) implementuje ten interfejs obsługuje numeryczny aliasów dla zmiennych.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) tworzy alias dla konkretnego obiektu. Aby wyszukać aliasy, użyj [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) lub [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Następujące metody są zdefiniowane w `IDebugAlias` interfejsu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Pobiera obiekt, do którego odwołuje się ten alias.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Pobiera nazwę aliasu.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Pobiera `ICorDebugValue` interfejsu, która zapewnia dostęp do zarządzanego kodu informacji dotyczących tego obiektu (tylko kod zarządzany).|  
|[Metoda Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Oznacza to, alias jako nie jest już używana.|  
  
## <a name="remarks"></a>Uwagi  
 Alias jest liczbą dziesiętną w postaci ciągu, a następnie znak #, na przykład 1001#.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Obliczanie wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)