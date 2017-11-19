---
title: EXCEPTION_INFO | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EXCEPTION_INFO
helpviewer_keywords: EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8bb60642857f0f07562feffe7b48e0454a73097e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
Zawiera opis wyjątku lub błędów czasu wykonywania zgłoszony przez debugowany program.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 pProgram  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje program, w którym wyjątek wystąpił.  
  
 bstrProgramName  
 Nazwa programu, w którym wyjątek wystąpił.  
  
 bstrExceptionName  
 Nazwa wyjątku.  
  
 dwCode  
 Kod identyfikacji błąd wyjątku lub czasu wykonywania.  
  
 dwState  
 Wartość z zakresu od [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) wyliczenia, który definiuje stan wyjątku.  
  
 guidType  
 Identyfikator GUID języka, albo `guidLang` lub `guidEng`.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazywana jako parametr [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) i [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) metody. Ta struktura jest również przekazany do [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) metodę, aby wypełnić.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)