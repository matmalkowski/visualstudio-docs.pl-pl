---
title: Interfejs IDebugPropertyEnumType_All | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75de35bd42ea91e7d27523ba42c392650686041a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794197"
---
# <a name="idebugpropertyenumtypeall-interface"></a>Interfejs IDebugPropertyEnumType_All
`IDebugPropertyEnumType` Interfejsy są zdefiniowane tak, aby każdy z ich IID mogą być przekazywane jako filtru w celu `IDebugProperty::EnumMembers` podczas żądania odpowiedniego modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Zwraca ciąg tekstowy opisujące nazwę|  
  
 Następujące interfejsy dziedziczyć `IDebugPropertyEnumType_All`, i mieć żadnych dodatkowych metod.  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)