---
title: IDebugAlias | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d92e239a561b22b164de90f43aa2e42f46cefd5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683808"
---
# <a name="idebugalias"></a>IDebugAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugAlias](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugalias).  
  
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Reprezentuje liczbowych aliasu dla zmiennej. Alias jest po prostu inną nazwę zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń (EE) implementuje ten interfejs do obsługi wartości liczbowych aliasów dla zmiennych.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) tworzy alias dla określonego obiektu. Aby wyszukać aliasy, użyj [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) lub [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Następujące metody są zdefiniowane w `IDebugAlias` interfejsu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Pobiera obiekt, do którego odwołuje się ten alias.|  
|[Getname —](../../../extensibility/debugger/reference/idebugalias-getname.md)|Pobiera nazwę aliasu.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Pobiera `ICorDebugValue` interfejsu, który zapewnia dostęp do zarządzanego kodu informacji dotyczących tego obiektu (tylko kod zarządzany).|  
|[Metody Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Oznacza to, alias jako nie jest już używana.|  
  
## <a name="remarks"></a>Uwagi  
 Alias jest liczbą dziesiętną w postaci ciągu, a następnie znak #, na przykład 1001#.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy oceny wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)

