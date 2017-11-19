---
title: IEnumDebugCodeContexts2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugCodeContexts2
helpviewer_keywords: IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9d0d54e9a3987ab8b2493d9e999955febd73ac4a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Ten interfejs wylicza kontekstów kodu skojarzonego z sesji debugowania lub z określonego programu lub dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania listę konteksty kod dla określonego tekstu pozycji w programie lub listę konteksty kodu dla kontekstu określonego dokumentu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) uzyskać ten interfejs reprezentujący listę konteksty kodu dla pozycji określonego tekstu w dokumencie źródłowym programu.  
  
 Wywołanie [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) uzyskać ten interfejs reprezentujący listę wszystkie konteksty kodu w określonego dokumentu źródłowego.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IEnumDebugCodeContexts2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Pobiera określoną liczbę kontekstów kodu w kolejności wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Pomija określoną liczbę kontekstów kodu w kolejności wyliczenia.|  
|[Resetowanie](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Resetuje sekwencję wyliczenia na początku.|  
|[Klonowania](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Pobiera moduł wyliczający różnych kontekstach kodu.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio wywołania [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) do wypełnienia listy kontekstów kodu użytkownik może wybrać od kiedy ustawienie następnej instrukcji lub przedstawiający dezasemblacji dla pliku źródłowego. Wielu kontekstów kodu mogą wystąpić, na przykład, jeśli istnieje wiele wystąpień szablon stylu C++.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)