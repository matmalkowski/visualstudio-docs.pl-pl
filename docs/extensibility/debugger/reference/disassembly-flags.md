---
title: DISASSEMBLY_FLAGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd1aa9c73fad40d07be371ad7f9b3108464aeb34
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101365"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Określa flagi dezasemblacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DF_DOCUMENTCHANGE  
 Wskazuje, czy ta instrukcja znajduje się w innym dokumencie od poprzedniego.  
  
 DF_DISABLED  
 Wskazuje, że ta instrukcja nie zostanie wykonany.  
  
 DF_INSTRUCTION_ACTIVE  
 Wskazuje, że ta instrukcja jest jedną z następnej instrukcji do wykonania (może istnieć więcej niż jeden).  
  
 DF_DATA  
 Wskazuje, że ta instrukcja jest naprawdę danych (nie kodu).  
  
 DF_HASSOURCE  
 Wskazuje, czy ta instrukcja ma źródła. Instrukcje, takich jak kodu kolekcji profilowania lub odzyskiwanie, mieć nie odpowiadającego jej źródła.  
  
 DF_DOCUMENT_CHECKSUM  
 Oznacza to, że `bstrDocumentUrl` pole zawiera dane sumy kontrolnej adresem URL dokumentu. W sekcji uwag [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury sposób przechowywania danych sumy kontrolnej.  
  
## <a name="remarks"></a>Uwagi  
 Używane jako `dwFlags` członkiem [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury.  
  
 Te flagi mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)