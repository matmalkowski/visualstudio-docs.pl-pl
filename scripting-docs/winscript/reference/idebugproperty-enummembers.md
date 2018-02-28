---
title: IDebugProperty::EnumMembers | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cb57f2609fcd9a80e2a9e0dfd63637e6f700047
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Wylicza elementy członkowskie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFieldSpec`  
 [in] Określa `DBGPROP_INFO_FLAGS` stałe, które określają pola, które w strukturach właściwości debugowania wyliczany mają zostać wypełnione.  
  
 `nRadix`  
 [in] Podstawa ma być używana podczas interpretacji wszelkie informacje numeryczne.  
  
 `refiid`  
 [in] Identyfikator IID jest przekazywany do filtrowania modułu wyliczającego. Uzyskanie identyfikatora IID jest jednym z `IDebugPropertyEnumType` interfejsów, które dziedziczą z `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 [out] Zwraca `IEnumDebugPropertyInfo` interfejsu, który wylicza właściwości elementów członkowskich.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zwykle `S_OK`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Interfejs IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [Interfejs IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)