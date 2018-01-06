---
title: FIELD_KIND | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FIELD_KIND
helpviewer_keywords: FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 095a02edb0a462e2fdbdca0f7f92018861b3d6bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="fieldkind"></a>FIELD_KIND
Określa rodzaj pole zawarte w [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```csharp  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 FIELD_KIND_TYPE  
 Wskazuje, że pole jest tylko typu.  
  
 FIELD_KIND_SYMBOL  
 Wskazuje, że pole jest symbol, typu, nazwy i inne informacje.  
  
 FIELD_TYPE_PRIMITIVE  
 Wskazuje, że pole jest typu pierwotnego.  
  
 FIELD_TYPE_STRUCT  
 Wskazuje, że pole jest strukturą.  
  
 FIELD_TYPE_CLASS  
 Wskazuje, że pole jest klasą.  
  
 FIELD_TYPE_INTERFACE  
 Wskazuje, że pole jest interfejsem.  
  
 FIELD_TYPE_UNION  
 Wskazuje, że pole jest Unii.  
  
 FIELD_TYPE_ARRAY  
 Wskazuje, że pole jest tablicą.  
  
 FIELD_TYPE_METHOD  
 Wskazuje, że pole jest metodą.  
  
 FIELD_TYPE_BLOCK  
 Wskazuje, że pole jest blok.  
  
 FIELD_TYPE_POINTER  
 Wskazuje, że pole jest wskaźnik.  
  
 FIELD_TYPE_ENUM  
 Wskazuje, że pole jest wyliczany typ danych.  
  
 FIELD_TYPE_LABEL  
 Wskazuje, że pole jest etykiety.  
  
 FIELD_TYPE_TYPEDEF  
 Wskazuje, że pole jest elementem typedef.  
  
 FIELD_TYPE_BITFIELD  
 Wskazuje, że pole jest bitfield.  
  
 FIELD_TYPE_NAMESPACE  
 Wskazuje, że pole jest przestrzenią nazw.  
  
 FIELD_TYPE_MODULE  
 Wskazuje, że pole jest modułem.  
  
 FIELD_TYPE_DYNAMIC  
 Wskazuje, że pole jest dynamiczny.  
  
 FIELD_TYPE_PROP  
 Wskazuje, że pole jest właściwością.  
  
 FIELD_TYPE_INNERCLASS  
 Wskazuje, że pole jest klasą wewnętrzny.  
  
 FIELD_TYPE_REFERENCE  
 Wskazuje, że pole jest odwołanie.  
  
 FIELD_TYPE_EXTENDED  
 Zarezerwowane do użytku w przyszłości.  
  
 FIELD_SYM_MEMBER  
 Wskazuje, że pole jest elementem członkowskim.  
  
 FIELD_SYM_LOCAL  
 Wskazuje, że pole jest lokalny.  
  
 FIELD_SYM_PARAMETER  
 Wskazuje, że pole jest parametrem.  
  
 FIELD_SYM_THIS  
 Wskazuje, że pole jest wskaźnik "this".  
  
 FIELD_SYM_GLOBAL  
 Wskazuje, że pole jest globalnego.  
  
 FIELD_SYM_PROP_GETTER  
 Wskazuje, czy pole pobiera właściwości.  
  
 FIELD_SYM_PROP_SETTER  
 Wskazuje, że pole ustawia właściwości.  
  
 FIELD_SYM_EXTENDED  
 Zarezerwowane do użytku w przyszłości.  
  
 FIELD_KIND_MASK  
 Wskazuje maska dla typów pól.  
  
 FIELD_TYPE_MASK  
 Wskazuje maskę dla typów pól.  
  
 FIELD_SYM_MASK  
 Wskazuje maskę dla informacji o symbolach.  
  
## <a name="remarks"></a>Uwagi  
 Zwrócone w wyniku wywołania [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metody.  
  
 W zależności od rodzaju pola [QueryInterface](/cpp/atl/queryinterface) można wywołać w [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejs dla bardziej konkretnych formularza interfejsu. Na przykład jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca `FIELD_TYPE_METHOD`, można wywołać `QueryInterface` i`DebugField` uzyskanie [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)