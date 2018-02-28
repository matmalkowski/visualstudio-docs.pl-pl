---
title: IDebugContainerField | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: eb08e269cd5fa2d98b91d8a7ac2107e4784ca02e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Ten interfejs reprezentuje symbol lub typu, który jest kontenerem dla innych symboli lub typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symbol implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu. Ten interfejs jest również klasę podstawową dla wszystkich interfejsów, które reprezentują kontenery.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wiele metod w wielu interfejsach zwrócić tego interfejsu. Ponieważ jest to klasa podstawowa dla wszystkich kontenerów, wyspecjalizowanego interfejsów można uzyskać z tego interfejsu za pomocą [QueryInterface](/cpp/atl/queryinterface). Interfejsy obejmują [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), i [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz metod na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu, tego interfejsu implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Tworzy moduł wyliczający dla pól kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Tablice (kontenery zmiennych), klas (kontenerami dla metod i zmienne) i metody (kontenery parametrów i zmiennych lokalnych) są wszystkie przykłady kontenerów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Symbol dostawcy interfejsów](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)