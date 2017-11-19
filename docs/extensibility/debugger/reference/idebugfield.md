---
title: IDebugField | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField
helpviewer_keywords: IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b13b14bcbc44bc74b044bcecb8aad99dff2d323a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfield"></a>IDebugField
Ten interfejs reprezentuje pole, czyli Opis symbolu lub typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawca symbol implementuje ten interfejs jako klasa podstawowa dla wszystkich pól.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest klasa podstawowa dla wszystkich pól. Na podstawie wartości zwracanych z [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), ten interfejs może zwracać interfejsy wyspecjalizowanego przy użyciu [QueryInterface](/cpp/atl/queryinterface). Ponadto zwracać wiele interfejsów `IDebugField` obiektów z różnych metod.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugField`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Pobiera zawiera informacje dotyczące symboli lub typu.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Pobiera rodzaj pola.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Pobiera typ pola.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Pobiera kontener pola.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Pobiera adres pola.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Pobiera rozmiar pola, w bajtach.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Pobiera rozszerzone informacje dotyczące pola.|  
|[Równości](../../../extensibility/debugger/reference/idebugfield-equal.md)|Porównuje dwa pola.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Pobiera niezależny od typu informacji o symbolu lub typu.|  
  
## <a name="remarks"></a>Uwagi  
 Typ jest odpowiednikiem języka C `typedef`.  
  
 W poniższym przykładzie języka C++ `weather` jest typem klasy i `sunny` i `stormy` są symbole:  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Czy pole reprezentuje symbol lub można określić typu przez wywołanie metody [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) i sprawdzeniu [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) wynik. Jeśli `FIELD_KIND_TYPE` ustawiono bit, pole jest typu i w razie `FIELD_KIND_SYMBOL` ustawiono bit, jest symbolu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Symbol dostawcy interfejsów](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)