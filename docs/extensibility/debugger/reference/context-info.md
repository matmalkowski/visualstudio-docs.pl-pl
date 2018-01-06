---
title: CONTEXT_INFO | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_INFO
helpviewer_keywords: CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 46168fefd491aeeae05c6406bd2b985fc5649bd1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="contextinfo"></a>CONTEXT_INFO
Ta struktura opisuje kontekstu pamięci lub kontekst kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 dwFields  
 Kombinacja flag z on [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) wyliczenia, która określa pola, które są wypełnione**.**  
  
 bstrModuleUrl  
 Nazwa modułu, w którym znajduje się kontekst.  
  
 bstrFunction  
 Nazwa funkcji, w którym znajduje się kontekst.  
  
 posFunctionOffset  
 A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktura, która identyfikuje przesunięcie wierszy i kolumn funkcji skojarzony z kontekstem kodu.  
  
 bstrAddress  
 Adres w kodzie, w którym znajduje się w danym kontekście.  
  
 bstrAddressOffset  
 Przesunięcie adresu w kodzie, w którym znajduje się w danym kontekście.  
  
 bstrAddressAbsolute  
 Bezwzględny adres w pamięci, w którym znajduje się w danym kontekście.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest zwracana z wywołania [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) metody.  
  
 Typowym zastosowaniem ta struktura jest wspierających **pamięci** okna debugowania.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)