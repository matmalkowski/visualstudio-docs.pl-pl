---
title: DEBUGPROP_INFO_FLAGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d9ecaab348ca69a792c39a8cb74e998d8f3a6aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104342"
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Określa, jakie informacje do pobrania dotyczące obiektu właściwości debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DEBUGPROP_INFO_FULLNAME  
 Inicjowanie użycia `bstrFullName` pola.  
  
 DEBUGPROP_INFO_NAME  
 Inicjowanie użycia `bstrName` pola.  
  
 DEBUGPROP_INFO_TYPE  
 Inicjowanie użycia `bstrType` pola.  
  
 DEBUGPROP_INFO_VALUE  
 Inicjowanie użycia `bstrValue` pola.  
  
 DEBUGPROP_INFO_ATTRIB  
 Inicjowanie użycia `dwAttrib` pola.  
  
 DEBUGPROP_INFO_PROP,  
 Inicjowanie użycia `pProperty` pola, które zawiera [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfejsu.  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Oznacza, że pole wartości może zawierać wartość rozwinięty automatycznie, jeśli jest dostępna dla tego typu obiektu.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Przestarzałe.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Zwraca wszystkie wartości beautified lub elementy członkowskie (czyli bez formatowania wartości).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 Nie zwraca żadnych specjalnych syntezatora wartości (na przykład nie należy wywoływać `ToString()` obiektu w celu utworzenia wartości).  
  
 DEBUGPROP_INFO_NONE  
 Określa, że ustawiono żadnych flag.  
  
 DEBUGPROP_INFO_STANDARD  
 Inicjowanie użycia `dwAttrib`, `bstrName`, `bstrType`, i `bstrValue` pól.  
  
 DEBUGPROP_INFO_All  
 Wskazuje maskę wszystkie flagi.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są przekazywane do [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), i [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) metod, aby określić pola, które mają zostać zainicjowany [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury.  
  
 Te wartości są używane również do `dwFields` członkiem `DEBUG_PROPERTY_INFO` struktury, aby wskazać, które pola struktury są używane i prawidłowe, gdy struktura jest zwracany.  
  
 Te wartości mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)