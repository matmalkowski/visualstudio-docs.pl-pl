---
title: Interfejs IEnumDebugPropertyInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugPropertyInfo interface
ms.assetid: c5eea4da-8414-408a-a8f6-6a9ca8745868
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61504d60ccb59a0632376bf8e1ef762382b06326
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794623"
---
# <a name="ienumdebugpropertyinfo-interface"></a>Interfejs IEnumDebugPropertyInfo
Wylicza `DebugPropertyInfo` struktury.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IEnumDebugPropertyInfo`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|Pobiera określoną liczbę `DebugPropertyInfo` struktury w kolejności wyliczenia.|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|Pomija określoną liczbę `DebugPropertyInfo` struktury w kolejności wyliczenia.|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|Pobiera liczbę `DebugPropertyInfo` struktury w moduł wyliczający.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dbgprop.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)