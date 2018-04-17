---
title: THREADSTATE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5a2153b6f97727cbf436c66686160cece15c287
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="threadstate"></a>THREADSTATE
Określa stan wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 THREADSTATE_RUNNING  
 Wskazuje, że wątek jest uruchomiony.  
  
 THREADSTATE_STOPPED  
 Wskazuje, że wątek jest zatrzymany z powodu punktu przerwania.  
  
 THREADSTATE_FRESH  
 Wskazuje, że wątku został utworzony, ale nie jest jeszcze uruchomiona kodu.  
  
 THREADSTATE_DEAD  
 Wskazuje, że wątek jest martwy.  
  
 THREADSTATE_FROZEN  
 Wskazuje, że wątek jest zablokowana (mogą być wykonywane nie wykonywania).  
  
## <a name="remarks"></a>Uwagi  
 Używany do `dwThreadState` pole [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) struktury.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)