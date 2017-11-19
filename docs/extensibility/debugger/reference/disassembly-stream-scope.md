---
title: DISASSEMBLY_STREAM_SCOPE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords: DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9cbd0ea73c7efea5cee570548dec5570ffc53b42
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Określa zakres strumienia dezasemblacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DSS_HUGE  
 Określa, że dezasemblowanie kontekst kodu powoduje wygenerowanie moc niż zwykle chce pobierać w pojedynczym wywołaniu klienta.  
  
 DSS_FUNCTION  
 Określa, że funkcja zawarty w kontekście kod powinien dezasemblowania. Określa, że strumienia dezasemblacji reprezentuje funkcję, gdy zwracany przez [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) metody.  
  
 DSS_MODULE  
 Zwracanie przez `IDebugDisassemblyStream2::GetScope` metody, określa, czy strumień dezasemblacji reprezentuje modułu.  
  
 DSS_ALL  
 Określa dezasemblacji dla całej przestrzeni.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako argument [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) — metoda i zwrócony przez [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) metody.  
  
 Te wartości mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)