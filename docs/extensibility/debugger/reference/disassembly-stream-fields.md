---
title: DISASSEMBLY_STREAM_FIELDS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a8735992574699ba2b108fc493e9003ca52c9b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103529"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Określa, jakie informacje pobrać o polu dezasemblacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DSF_ADDRESS  
 Inicjowanie użycia `bstrAddress` pola.  
  
 DSF_ADDRESSOFFSET  
 Inicjowanie użycia `bstrAddressOffset` pola.  
  
 DSF_CODEBYTES  
 Inicjowanie użycia `bstrCodeBytes` pola.  
  
 DSF_OPCODE  
 Inicjowanie użycia `bstrOpCode` pola.  
  
 DSF_OPERANDS  
 Inicjowanie użycia `bstrOperands` pola.  
  
 DSF_SYMBOL  
 Inicjowanie użycia `bstrSymbol` pola.  
  
 DSF_CODELOCATIONID  
 Inicjowanie użycia `uCodeLocationId` pola.  
  
 DSF_POSITION  
 Inicjowanie użycia `posBeg` i `posEnd` pól.  
  
 DSF_DOCUMENTURL  
 Inicjowanie użycia `bstrDocumentUrl` pola.  
  
 DSF_BYTEOFFSET  
 Inicjowanie użycia `dwByteOffset` pola.  
  
 DSF_FLAGS  
 Inicjowanie użycia `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) pola.  
  
 DSF_OPERANDS_SYMBOLS  
 Dołącz nazwy symbolu w `bstrOperands` pola.  
  
 DSF_ALL  
 Określa wszystkie pola dla strumienia dezasemblacji.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako parametr [odczytu](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metody, aby wskazać, które pola [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury mają być zainicjowany.  
  
 Używany do `dwFields` członkiem `DisassemblyData` struktury, aby wskazać pola, które są używane i ważne, gdy struktura jest zwracany.  
  
 Te wartości mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Odczyt](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)