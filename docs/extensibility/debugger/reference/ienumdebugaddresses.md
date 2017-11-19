---
title: IEnumDebugAddresses | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugAddresses
helpviewer_keywords: IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db531c35ea3bbb6176095f19897404d192096e22
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Ten interfejs reprezentuje kolekcję obiektów implementacja [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawcę symbol podać zestawy obiektów implementujących [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu. Należy pamiętać, że nie jest to standardowy wyliczenia modelu COM z powodu obecności [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) metody.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest zwracany przez [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) i [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Ten interfejs implementuje poniższych metod.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Pobiera zestaw dalej [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektów z wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Pomija określoną liczbę wpisów.|  
|[Resetowanie](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Resetuje wyliczenia do pierwszej pozycji.|  
|[Klonowania](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Pobiera kopię w bieżącym wyliczeniu.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Pobiera liczbę wpisów w wyliczeniu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest zwykle używany przez aparat debugowania w celu określenia odpowiedniego adresu ma zostać przypisany do ewaluatora wyrażenia.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Symbol dostawcy interfejsów](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)