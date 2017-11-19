---
title: Struktura DebugPropertyInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9baade1a742a06c952906c05c574e752806bc9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="debugpropertyinfo-structure"></a>Struktura DebugPropertyInfo
Opis obiektu o charakterze hierarchiczna mającą nazwę, typ i wartość. Jest używany do opisu właściwości debugowania zmiennych lokalnych, parametrów i zmiennych czujki wyrażeń i rejestruje.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 dwValidFields  
 Wyliczany typ danych używany do określenia pola, które są zainicjowane.  
  
 bstrName  
 Nazwa właściwości w kontekście.  
  
 bstrType  
 Typ właściwości jako ciąg sformatowany.  
  
 bstrValue  
 Wartość właściwości jako ciąg sformatowany.  
  
 bstrFullName  
 Pełna nazwa właściwości.  
  
 dwAttrib  
 Wyliczenie określa flagi dla atrybutów właściwości debugowania.  
  
 pDebugProp  
 `IDebugProperty` Opisanego przez informacji w tym `DebugPropertyInfo` struktury.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)