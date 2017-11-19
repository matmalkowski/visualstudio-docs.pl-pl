---
title: IEnumDebugObjects | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugObjects
helpviewer_keywords: IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20f2d7695cfed89bc38cb73e2f00216060e2d970
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób wdrażania ewaluatorów wyrażeń jest przestarzały. Aby uzyskać informacje dotyczące wdrożenia ewaluatorów wyrażeń CLR, zobacz [Ewaluatorów wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane próbki ewaluatora wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ten interfejs reprezentuje kolekcję obiektów implementacja [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ewaluator wyrażeń implementuje ten interfejs podać zestawy obiektów implementujących [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu. Należy pamiętać, że nie jest to standardowy wyliczenia modelu COM z powodu obecności [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) metody.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) zwraca tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Ten interfejs implementuje poniższych metod.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Pobiera zestaw dalej [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektów z wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Pomija określoną liczbę wpisów.|  
|[Resetowanie](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Resetuje wyliczenia do pierwszej pozycji.|  
|[Klonowania](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Pobiera kopię w bieżącym wyliczeniu.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs umożliwia aparat debugowania Wylicz zestaw obiektów w tablicy.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)