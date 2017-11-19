---
title: FIELD_INFO_FIELDS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FIELD_INFO_FIELDS
helpviewer_keywords: FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1aa1c2363ecf3cb6bfd9531112c87d8bcaeefe4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Określa, jakie informacje pobrać o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 FIF_FULLNAME  
 Inicjowanie użycia `bstrFullName` w [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury.  
  
 FIF_NAME  
 Inicjowanie użycia `bstrName` w `FIELD_INFO` struktury.  
  
 FIF_TYPE  
 Inicjowanie użycia `bstrType` w `FIELD_INFO` struktury.  
  
 FIF_MODIFIERS  
 Inicjowanie użycia `bstrModifiers` w `FIELD_INFO` struktury.  
  
## <a name="remarks"></a>Uwagi  
 Te wartości są również przekazywane jako argument [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metodę, aby określić, które pola [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury mają być zainicjowany.  
  
 Te wartości są również używane w `dwFields` członkiem `FIELD_INFO` struktury, aby wskazać pola, które są używane i prawidłowe.  
  
 Te flagi mogą być łączone z bitowego `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)