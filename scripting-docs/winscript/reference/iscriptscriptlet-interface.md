---
title: Interfejs IScriptScriptlet | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3fa3253997d3a09a7170f3795bf8a7bbf8a182c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptscriptlet-interface"></a>Interfejs IScriptScriptlet
Obiekt, który implementuje `IScriptScriptlet` interfejsu reprezentuje skryptów programu obsługi zdarzeń.  
  
 Oprócz dziedziczone z metody `IScriptEntry`, `IScriptScriptlet` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Zwraca nazwę zdarzenia, który jest skojarzony z skryptlet.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Zwraca nazwę zdarzenie proste, która jest skojarzona z skryptlet. Jest to nazwa jednowyrazowej, która nie zawiera żadnego odstępu.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Zwraca ostatni identyfikator w pełni kwalifikowanej nazwy skryptletu obiektu hosta.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Ustawia nazwę zdarzenia, który jest skojarzony z skryptlet.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Ustawia nazwę zdarzenia prostego skojarzony z skryptlet. Jest to nazwa jednowyrazowej, która nie zawiera żadnego odstępu.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Ustawia identyfikator ostatniego w pełni kwalifikowanej nazwy skryptletu obiektu hosta.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy tworzenia aktywnych skryptów](../../winscript/reference/active-script-authoring-interfaces.md)