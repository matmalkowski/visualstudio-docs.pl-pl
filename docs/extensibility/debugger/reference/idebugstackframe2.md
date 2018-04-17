---
title: IDebugStackFrame2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: efa6c917e5a59c291d07757b52fab4fe8aa7b0ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Ten interfejs reprezentuje ramka stosu pojedynczego w stosie wywołań, w szczególności wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania ramki stosu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) można pobrać [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfejsu. Wywołanie [dalej](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) można pobrać [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury, która zawiera `IDebugStackFrame2` interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugStackFrame2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Pobiera kontekst kodu dla tej ramki stosu.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Pobiera kontekst dokumentu dla tej ramki stosu.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Pobiera nazwę ramki stosu.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Pobiera opis ramki stosu.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Pobiera reprezentację maszyny zależne od zakresu adresów fizycznych skojarzonych z ramki stosu.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Pobiera kontekst oceny podczas obliczania wyrażenia w bieżącym kontekście ramki stosu i wątku.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Pobiera język ramki stosu.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Pobiera opis właściwości skojarzone z ramki stosu.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Tworzy moduł wyliczający dla stosu właściwości ramki.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Pobiera wątek skojarzony z ramki stosu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest uzyskiwana tylko wtedy, gdy debugowany program został zatrzymany w punkcie przerwania (albo spowodowane przez punkt przerwania ustawiono użytkownika lub wyjątek). W tym interfejsie można uzyskać z kontekstu wyrażenia można obliczyć wyrażenia, lista rejestrów może być zwracany lub stos wywołań może być uzyskane i zbadać.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)