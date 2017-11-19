---
title: FIELD_INFO | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FIELD_INFO
helpviewer_keywords: FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b7b3bfae3923a7df3f5c499bfac5cde12d1388b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="fieldinfo"></a>FIELD_INFO
Ta struktura opisuje zmiennej lokalnej, parametr lub inne pole.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```csharp  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 dwFields  
 Kombinacja flag z [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) wyliczenie określająca, które elementy członkowskie są wypełnione.  
  
 bstrFullName  
 Pełna nazwa pola.  
  
 bstrName  
 Krótka nazwa pola.  
  
 bstrType  
 Typ pola.  
  
 dwModifiers  
 Kombinacja flag z [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) wyliczenie opisujące pola.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest przekazywana do [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metody, gdzie jest wypełnione.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)