---
title: IDebugObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4cff859d2aa4b3a3c88978e077102e045efe1f3b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121004"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs reprezentuje obiekt, który tworzy obiekt wiążący hermetyzacji wartości symboli i wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń implementuje ten interfejs do reprezentowania obiektu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest klasa podstawowa dla wszystkich obiektów używanych w wyrażeniach przeanalizowany ewaluatora wyrażenia. Jest zwracany przez wywołanie do [powiązać](../../../extensibility/debugger/reference/idebugbinder-bind.md) metody. [QueryInterface](/cpp/atl/queryinterface) uzyskuje wyspecjalizowanego interfejsów w tym interfejsie.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugObject`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Pobiera rozmiar obiektu.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Pobiera wartość obiektu jako serię kolejnych bajtów.|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Ustawia wartość obiektu z szeregu kolejnych bajtów.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Ustawia wartość odwołania do tego obiektu.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Pobiera kontekst pamięci, która reprezentuje adres wartość obiektu.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Tworzy kopię obiektu zarządzanego w przestrzeni adresowej aparat debugowania.|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Sprawdza, czy ten obiekt jest odwołaniem o wartości zerowej.|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Porównano do tego obiektu.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Określa, czy ten obiekt jest tylko do odczytu.|  
|[Serwer proxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Określa, czy obiekt jest przezroczystego obiektu pośredniczącego.|  
  
## <a name="remarks"></a>Uwagi  
 Ewaluator wyrażeń używa tego interfejsu jako klasę podstawową do reprezentowania obiektów w drzewie analizy.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Obliczanie wyrażenia](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md)