---
title: "IJsDebugProperty::GetMembers — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugProperty.GetMembers
apilocation: jscript9diag.dll
ms.assetid: a32b5372-d9cb-4b9a-9bc2-81b5e1df365c
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 066db431f27eca01fab63d10d0396575b3895527
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugpropertygetmembers-method"></a>IJsDebugProperty::GetMembers — Metoda
Pobiera elementy członkowskie tego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMembers(  
   JS_PROPERTY_MEMBERS members,  
   IJsEnumDebugProperty **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `members`  
 [in] Flagi, aby określić zawartość informacji elementu członkowskiego.  
  
 `ppEnum`  
 [out] Elementy członkowskie obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugproperty — interfejs](../../winscript/reference/ijsdebugproperty-interface.md)