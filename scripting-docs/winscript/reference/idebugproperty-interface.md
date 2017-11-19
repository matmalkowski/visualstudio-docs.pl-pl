---
title: Interfejs IDebugProperty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2888a6d781ecd501128545e483971a47859d9cda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugproperty-interface"></a>Interfejs IDebugProperty
Używany do opisania hierarchiczna właściwości jednostki debugowany, zawierający nazwę, typ i wartość. Najczęściej `IDebugProperty` jest używany do opisu wynik wyrażenia, oceny instrukcji lub rejestru oceny.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugProperty` interfejsu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Pobierz `DebugPropertyInfo` opisujący to`IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Pobiera informacje o rozszerzonych właściwości.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Ustawia wartości właściwości z ciągu.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Wylicza elementy członkowskie właściwości.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Pobiera element nadrzędny właściwości.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dbgprop.h