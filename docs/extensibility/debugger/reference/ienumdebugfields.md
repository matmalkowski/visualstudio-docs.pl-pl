---
title: IEnumDebugFields | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a475d7e163cd146a0fd200c1bcac2f3a572ef9e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Ten interfejs reprezentuje kolekcję obiektów implementacja [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawcę symbol podać zestawy obiektów implementujących [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu. Należy pamiętać, że nie jest to standardowy wyliczenia modelu COM z powodu obecności [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) metody.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest zwracany przez [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) i [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Ten interfejs implementuje poniższych metod.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Pobiera zestaw dalej [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektów z wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Pomija określoną liczbę wpisów.|  
|[Resetowanie](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Resetuje wyliczenia do pierwszej pozycji.|  
|[klonowania](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Pobiera kopię w bieżącym wyliczeniu.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Symbol dostawcy interfejsów](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)