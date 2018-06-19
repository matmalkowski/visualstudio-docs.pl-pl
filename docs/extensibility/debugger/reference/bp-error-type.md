---
title: BP_ERROR_TYPE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 676ec19fec1406d85e6a7d9e66865b2794f72aa6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103009"
---
# <a name="bperrortype"></a>BP_ERROR_TYPE
Określa typ błędu punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 BPET_NONE  
 Określa błąd braku punktu przerwania.  
  
 BPET_TYPE_WARNING  
 Określa błąd przerwania stylu ostrzeżenie.  
  
 BPET_TYPE_ERROR  
 Określa błąd przerwania stylu błędu.  
  
 BPET_SEV_HIGH  
 Określa o wysokiej ważności punktu przerwania.  
  
 BPET_SEV_GENERAL  
 Określa błąd przerwania średniej ważności.  
  
 BPET_SEV_LOW  
 Określa o niskiej ważności punktu przerwania.  
  
 BPET_TYPE_MASK  
 Określa błąd przerwania stylu maski.  
  
 BPET_SEV_MASK  
 Określa błąd ważność maska stylu punktu przerwania.  
  
 BPET_GENERAL_WARNING  
 Określa błąd ogólne ostrzeżenie stylu punktu przerwania.  
  
 BPET_GENERAL_ERROR  
 Określa błąd ogólny błąd typu punktu przerwania.  
  
 BPET_ALL  
 Określa wszystkie typy błąd punktu przerwania.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości mogą być łączone z bitowego `OR` i używane do `dwType` członkiem [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury. Przekazany jako parametr [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) metody.  
  
 Typ błędu przerwania składa się z typu i ważności. Oznacza, że typ błędu przerwania nigdy nie tylko typem (na przykład `BPET_TYPE_ERROR`,) lub ważności (na przykład `BPET_SEV_GENERAL`) przez samego siebie. `BPET_GENERAL_WARNING` i `BPET_GENERAL_ERROR` podać wstępnie zdefiniowanych wartości ogólne punktów przerwania ostrzeżeń i błędów.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)