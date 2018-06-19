---
title: BP_LOCATION_TYPE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db35e354b2cfbe91b9c6041dc6239d2dfd2531f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108946"
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
Określa typ lokalizacji punktu przerwania dla żądania punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```csharp  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BPLT_NONE  
 Określa nie lokalizacji punktu przerwania.  
  
 BPLT_FILE_LINE  
 Określa typ lokalizacji punktu przerwania w wierszu pliku.  
  
 BPLT_FUNC_OFFSET  
 Określa typ lokalizacji punktu przerwania offset funkcji.  
  
 BPLT_CONTEXT  
 Określa typ lokalizacji punktu przerwania kontekst.  
  
 BPLT_STRING  
 Określa typ lokalizacji punktu przerwania jako ciąg.  
  
 BPLT_ADDRESS  
 Określa typ lokalizacji punktu przerwania adresu.  
  
 BPLT_RESOLUTION  
 Określa typ lokalizacji punktu przerwania rozwiązanie tego problemu.  
  
 BPLT_CODE_FILE_LINE  
 Określa typ lokalizacji punktu przerwania jako wiersz kodu źródłowego.  
  
 BPLT_CODE_FUNC_OFFSET  
 Określa typ lokalizacji punktu przerwania offset funkcji kodu.  
  
 BPLT_CODE_CONTEXT  
 Określa typ lokalizacji punktu przerwania jako kontekst kodu.  
  
 BPLT_CODE_STRING  
 Określa typ lokalizacji punktu przerwania jako ciąg kodu.  
  
 BPLT_CODE_ADDRESS  
 Określa typ lokalizacji punktu przerwania jako adres kodu.  
  
 BPLT_DATA_STRING  
 Określa typ lokalizacji punktu przerwania jako ciąg.  
  
 BPLT_TYPE_MASK  
 Określa maska bitowa, dzięki czemu można wyodrębnić typ punktu przerwania poza wartość.  
  
 BPLT_LOCATION_TYPE_MASK  
 Określa maska bitowa, dzięki czemu można wyodrębnić typ lokalizacji punktu przerwania poza wartość.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany jako parametr [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) metody.  
  
 Typ punktu przerwania i typu lokalizacji składa się typ lokalizacji punktu przerwania. Oznacza to, że typ lokalizacji punktu przerwania nigdy nie jest tylko typ punktu przerwania (na przykład `BPT_CODE`) lub typu lokalizacji (na przykład `BPLT_FILE_LINE`). Stałe wstępnie zdefiniowane dla wszystkich typów lokalizacji punktu przerwania obecnie obsługiwane znajdują się w tym wyliczeniu (`BPLT_CODE_FILE_LINE` za pośrednictwem `BPLT_DATA_STRING`).  
  
 `BPT_CODE` i `BPT_DATA` są elementami członkowskimi [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) wyliczenia.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)