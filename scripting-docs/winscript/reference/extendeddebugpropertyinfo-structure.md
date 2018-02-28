---
title: Struktura ExtendedDebugPropertyInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee06b0ace93f068e0530a3aa62b8c28d11069f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="extendeddebugpropertyinfo-structure"></a>Struktura ExtendedDebugPropertyInfo
Rozszerza `DebugPropertyInfo` struktury z dodatkowych członków charakteryzujących właściwości rozszerzonej.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `dwValidFields`  
 Wyliczany typ danych używany do określenia pola, które są zainicjowane.  
  
 `bstrName`  
 Nazwa właściwości w kontekście.  
  
 `bstrType`  
 Typ właściwości jako ciąg sformatowany.  
  
 `bstrValue`  
 Wartość właściwości jako ciąg formatowania.  
  
 `bstrFullName`  
 Pełna nazwa właściwości.  
  
 `dwAttrib`  
 Wyliczenie określa flagi dla atrybutów właściwości debugowania.  
  
 `pDebugProp`  
 `IDebugProperty`Obiekt odpowiadający to `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Identyfikator wysyłania.  
  
 `nType`  
 Typ właściwości rozszerzonej.  
  
 `varValue`  
 Wartość właściwości rozszerzonej, jeśli można zmieścić w VARIANT.  
  
 `plbValue`  
 Bajtów danych rzeczywistych wartości właściwości.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty`Obiekt odpowiadający to `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [Interfejs IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)