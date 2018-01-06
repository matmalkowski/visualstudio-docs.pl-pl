---
title: IDebugObject2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2
helpviewer_keywords: IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 40b52cf5c36db3bf4fa07004df9a171e77c2520e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs zawiera dodatkowe informacje o obiekcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń implementuje ten interfejs do oferują obsługę aliasy i uzyskiwania dostępu do informacji o obiekcie.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu można uzyskać interfejsu za pomocą [QueryInterface](/cpp/atl/queryinterface). Ponadto [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) zwraca tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz metod na [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu `IDebugObject2` interfejsu implementuje następujące:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Pobiera pola lub zmiennej (jeśli istnieją) mogą który kopii właściwości reprezentowany przez ten obiekt.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Pobiera obiekt zarządzany kod reprezentujący wartość tego obiektu.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Tworzy unikatowy identyfikator dla tego obiektu lub zwraca istniejącego aliasu.|  
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Pobiera aliasu skojarzonego z tym obiektem, jeśli istnieje.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Pobiera typ obiektu.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Określa, czy ten obiekt reprezentuje dane użytkownika.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Określa, czy stan Edytuj i Kontynuuj nie jest już prawidłowy.<br /><br /> Ewaluatora wyrażenia niestandardowego nie implementuje tę metodę (zawsze powinien zwrócić `E_NOTIMPL`).|  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) omówienie na aliasów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Obliczanie wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)