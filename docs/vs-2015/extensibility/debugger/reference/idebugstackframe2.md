---
title: IDebugStackFrame2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57544c6ec8d329886d12bdcf2e8c622f7da53e4e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690056"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugStackFrame2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe2).  
  
Ten interfejs reprezentuje ramkę stosu w stosie wywołań, w szczególności wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący ramkę stosu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) można pobrać [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfejsu. Wywołaj [dalej](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) można pobrać [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strukturę, która zawiera `IDebugStackFrame2` interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugStackFrame2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Pobiera kontekst kodu dla tej ramki stosu.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Pobiera kontekst dokumentu dla tej ramki stosu.|  
|[Getname —](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Pobiera nazwę ramki stosu.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Pobiera opis ramki stosu.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Pobiera reprezentację zależnych od maszyny, zakresu adresów fizycznych skojarzonych z ramki stosu.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Pobiera kontekst oceny do wykonywania oceny wyrażenia w bieżącym kontekście ramki stosu i wątku.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Pobiera język ramki stosu.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Pobiera opis właściwości skojarzone z ramki stosu.|  
|[Enumproperties —](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Tworzy moduł wyliczający stosu właściwości ramki.|  
|[Getthread —](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Pobiera wątek skojarzony z ramki stosu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs otrzymuje tylko wtedy, gdy program poddawany został zatrzymany w punkcie przerwania (albo spowodowane przez użytkownika zestaw punktu przerwania lub wyjątku). W tym interfejsie kontekście wyrażenia można uzyskać można obliczyć wyrażenia, listę rejestrów, które mogą być zwracane lub stos wywołań, które mogą być uzyskane i badania.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)

