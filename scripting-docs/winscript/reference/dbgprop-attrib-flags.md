---
title: DBGPROP_ATTRIB_FLAGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_ATTRIB_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43db6cd118e2097d857d5c41334341c595088302
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792133"
---
# <a name="dbgpropattribflags"></a>DBGPROP_ATTRIB_FLAGS
Zawiera opis różnych atrybutów `IDebugProperty`. Element członkowski `DebugPropertyInfo` struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum {  
DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,  
   DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,  
   DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,  
   DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,  
   DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,  
   DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,  
   DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,  
   DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,  
   DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,  
   DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,  
   DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,  
   DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,  
   DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,  
   DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,  
   DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,  
   DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000  
   DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000,  
};  
  
```  
  
## <a name="members"></a>Elementy członkowskie  
 DBGPROP_ATTRIB_NO_ATTRIB  
 Wskazuje żadnych atrybutów.  
  
 DBGPROP_ATTRIB_VALUE_IS_INVALID  
 Oznacza to, że wartość w `DebugPropertyInfo::bstrValue` jest nieprawidłowy.  
  
 DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  
 Wskazuje, czy odwołanie lub właściwość zawiera elementy podrzędne.  
  
 DBGPROP_ATTRIB_VALUE_READONLY  
 Wskazuje, czy wartość jest tylko do odczytu.  
  
 DBGPROP_ATTRIB_ACCESS_PUBLIC  
 Wskazuje obiekt, który ma dostęp publiczny.  
  
 DBGPROP_ATTRIB_ACCESS_PRIVATE  
 Wskazuje obiekt, który ma dostęp do prywatnego.  
  
 DBGPROP_ATTRIB_ACCESS_PROTECTED  
 Wskazuje obiekt, który zawiera chronione dostępu.  
  
 DBGPROP_ATTRIB_ACCESS_FINAL  
 Wskazuje obiekt, który ma dostęp do końcowego.  
  
 DBGPROP_ATTRIB_STORAGE_GLOBAL  
 Wskazuje globalne magazynu.  
  
 DBGPROP_ATTRIB_STORAGE_STATIC  
 Wskazuje statycznego magazynu.  
  
 DBGPROP_ATTRIB_STORAGE_FIELD  
 Wskazuje obiekt, który jest właściwością.  
  
 DBGPROP_ATTRIB_STORAGE_VIRTUAL  
 Wskazuje magazynu wirtualnego.  
  
 DBGPROP_ATTRIB_TYPE_IS_CONSTANT  
 Wskazuje, że typ obiektu jest stałą.  
  
 DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  
 Oznacza to gniazdo wątku synchronizowane.  
  
 DBGPROP_ATTRIB_TYPE_IS_VOLATILE  
 Oznacza to gniazdo volatile względem magazynu trwałego.  
  
 DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  
 Wskazuje, że to miejsce ma atrybuty niż te wstępnie zdefiniowane usługi bits.  
  
 DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  
 Wskazuje, czy wartość jest wartości zwracanej przez funkcję.  
  
## <a name="remarks"></a>Uwagi  
 Te flagi są również używane do filtrowania elementów podrzędnych obiektu. Wartości mogą być łączone z bitowego OR.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [Struktura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)