---
title: IDebugManagedObject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e096d7c11e044f62f82fb8162aac5553e38b3a29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs umożliwia ewaluatora wyrażenia (EE) może wywołać właściwości lub metod wystąpień klasy wartości (na przykład `System.Decimal`) i ustawić ich wartości bez wywoływania elementu [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) na debugowany program.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń implementuje ten interfejs do reprezentowania obiektu kodu zarządzanego, takich jak zmiennej.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Aby uzyskać ten interfejs, należy wywołać [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) na [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący wystąpienie klasy wartości.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz dziedziczone z metody [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugManagedObject` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Zwraca interfejs reprezentujący obiekt kodu zarządzanego i z których wszystkie odpowiednie kodu zarządzanego można uzyskać interfejsu.|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Ustawia wartość tego obiektu. wartość obiektu określonego kodu zarządzanego.|  
  
## <a name="remarks"></a>Uwagi  
 Ewaluatora wyrażeń używa tego interfejsu do przechowywania obiektów kodu zarządzanego w drzewie analizy.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Obliczanie wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Ocena](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)