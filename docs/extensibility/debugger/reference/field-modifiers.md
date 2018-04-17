---
title: FIELD_MODIFIERS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0040795564aa1d1d599a55928b888ec7cfcfd97e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
Określa Modyfikatory dla typu pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```csharp  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 FIELD_MOD_ACCESS_TYPE  
 Wskazuje, czy pole nie jest dostępna.  
  
 FIELD_MOD_ACCESS_PUBLIC  
 Wskazuje, czy pole ma dostęp do publicznego.  
  
 FIELD_MOD_ACCESS_PROTECTED  
 Wskazuje ochronę w polu dostępu.  
  
 FIELD_MOD_ACCESS_PRIVATE  
 Wskazuje, czy pole ma dostęp do prywatnego.  
  
 FIELD_MOD_NOMODIFIERS  
 Wskazuje, czy pole nie ma żadnych modyfikatorów.  
  
 FIELD_MOD_STATIC  
 Wskazuje, czy pole ma statycznej.  
  
 FIELD_MOD_CONSTANT  
 Wskazuje, że pole jest stałą.  
  
 FIELD_MOD_TRANSIENT  
 Wskazuje, że pole jest przejściowy.  
  
 FIELD_MOD_VOLATILE  
 Wskazuje, że pole jest nietrwały.  
  
 FIELD_MOD_ABSTRACT  
 Wskazuje, że pole jest abstrakcyjny.  
  
 FIELD_MOD_NATIVE  
 Wskazuje, że pole jest native.  
  
 FIELD_MOD_SYNCHRONIZED  
 Wskazuje, że pole jest zsynchronizowany.  
  
 FIELD_MOD_VIRTUAL  
 Wskazuje, że pole jest wirtualna.  
  
 FIELD_MOD_INTERFACE  
 Wskazuje, że pole jest interfejsem.  
  
 FIELD_MOD_FINAL  
 Wskazuje, że pole jest końcowym.  
  
 FIELD_MOD_SENTINEL  
 Wskazuje, że pole jest wartownik.  
  
 FIELD_MOD_INNERCLASS  
 Wskazuje, że pole jest klasą wewnętrzny.  
  
 FIELD_TYPE_OPTIONAL  
 Wskazuje, że pole jest opcjonalne.  
  
 FIELD_MOD_BYREF  
 Wskazuje, że pole jest argument odwołania. Jest to specjalnie z myślą o argumenty metody.  
  
 FIELD_MOD_HIDDEN  
 Wskazuje, że pole musi ukryte lub w innym kontekście; na przykład [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] statycznych zmiennych lokalnych.  
  
 FIELD_MOD_MARSHALASOBJECT  
 Wskazuje, że pole reprezentuje obiekt z `IUnknown` interfejsu.  
  
 FIELD_MOD_SPECIAL_NAME  
 Wskazuje, czy pole ma specjalną nazwę, na przykład `.ctor` dla konstruktora ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] tylko).  
  
 FIELD_MOD_HIDEBYSIG  
 Wskazuje, czy pole ma `Overloads` zastosować dla niego — słowo kluczowe ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] tylko).  
  
 FIELD_MOD_WRITEONLY  
 Wskazuje, że pole jest tylko do zapisu. Ta wartość nie jest objęta `FIELD_MOD_ALL`, ponieważ jest użycie tylko takie pola tylko do zapisu do obliczania funkcji. Użytkownik musi jawnie poprosić o `FIELD_MOD_WRITEONLY` pola.  
  
 FIELD_MOD_ACCESS_MASK  
 Wskazuje maskę dla dostępu do pola.  
  
 FIELD_MOD_MASK  
 Wskazuje maskę dla modyfikatorów pól.  
  
## <a name="remarks"></a>Uwagi  
 Używany do `dwModifiers` członkiem [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury.  
  
 Te wartości są również przekazywane do [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) metody, aby filtrować pod kątem określonych pól.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)