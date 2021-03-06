---
title: IEnumDebugCodeContexts2 | Dokumentacja firmy Microsoft
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
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 387dce09ee6a01b2ff092e963fa4197d833ef142
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690859"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IEnumDebugCodeContexts2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugcodecontexts2).  
  
Ten interfejs wylicza kontekstów kod związany z sesji debugowania lub z określonego programu lub dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania listę konteksty kodu dla określonego tekstu pozycji w programie lub Podaj listę konteksty kodu dla kontekstu określonego dokumentu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) uzyskać ten interfejs reprezentujący listę konteksty kodu dla pozycji określony tekst w dokumencie źródłowym programu.  
  
 Wywołaj [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) uzyskać ten interfejs reprezentujący listę wszystkich kontekstach kodu w określonego dokumentu źródłowego.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumDebugCodeContexts2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Pobiera określoną liczbę kontekstów kodu w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Pomija określoną liczbę kontekstów kodu w kolejności wyliczenia.|  
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Pobiera liczbę kontekstów kodu w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio wywołania [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) do wypełnienia listy kontekstów kod użytkownika mogą wybierać kiedy ustawienie następnej instrukcji lub wyświetlanie dezasemblacji dla pliku źródłowego. Wiele kontekstów kod może wystąpić na przykład, gdy istnieje wiele wystąpień szablonu styl C++.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)

