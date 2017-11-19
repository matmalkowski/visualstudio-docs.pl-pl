---
title: THREADPROPERTIES | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: THREADPROPERTIES
helpviewer_keywords: THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b4ec394deef3b317d91e6cbe22bbc1d95a6aca5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="threadproperties"></a>THREADPROPERTIES
Opisuje właściwości wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 dwFields  
 Kombinacja flag z [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) wyliczenie opisujące, które pola struktury są prawidłowe.  
  
 dwThreadId  
 Identyfikator wątku.  
  
 dwSuspendCount  
 Wątek zawiesić count.  
  
 dwThreadState  
 Wartość z zakresu od [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) Wyliczenie wskazujące stan operacyjny wątku.  
  
 bstrPriority  
 Ciąg określający priorytetu wątku; na przykład "Powyżej Normal", "Normal" lub "Czas krytyczne".  
  
 bstName  
 Nazwa wątku.  
  
 bstrLocation  
 Lokalizacja wątku (zazwyczaj ramki stosu najwyższego poziomu), zwykle wyrażona jako nazwa metody, których wykonywania jest obecnie zatrzymany.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest wypełniane przez wywołanie do [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metody. Tak zwrócone informacje jest zwykle używana do wypełniania **wątków** okna.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)