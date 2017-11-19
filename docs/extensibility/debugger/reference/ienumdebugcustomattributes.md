---
title: IEnumDebugCustomAttributes | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCustomAttributes
helpviewer_keywords: IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 74074505b9109638280d9fe8dad113b4dd13ba9e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Wylicza atrybutów niestandardowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symbol implementuje ten interfejs do obsługi atrybuty niestandardowe (za pośrednictwem [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) interfejs).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) zwraca tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IEnumDebugCustomAttributes`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Pobiera określoną liczbę atrybutów niestandardowych w kolejności wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Pomija określoną liczbę atrybutów niestandardowych w kolejności wyliczenia.|  
|[Resetowanie](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Resetuje sekwencję wyliczenia na początku.|  
|[Klonowania](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Pobiera liczbę atrybutów niestandardowych w moduł wyliczający.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Symbol dostawcy interfejsów](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)