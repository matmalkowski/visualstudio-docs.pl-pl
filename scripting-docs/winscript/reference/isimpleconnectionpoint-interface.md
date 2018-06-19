---
title: Interfejs ISimpleConnectionPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de40f66a9e5721b8dacac634c6fb77982017c155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796327"
---
# <a name="isimpleconnectionpoint-interface"></a>Interfejs ISimpleConnectionPoint
Zapewnia prostą metodę opisujące i wyliczania zdarzenia wywoływane w punkcie określonego połączenia. Ten interfejs również ułatwia podłączanie `IDispatch` obiektu z tymi zdarzeniami. Ten interfejs jest implementowany przez proces debugowania Manager (PDM) i używane przez aparaty skryptów.  
  
 Ten interfejs jest dostępny z `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Oprócz dziedziczone z metody `IUnknown`, `ISimpleConnectionPoint` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Ustanawia połączenie między obiektu punktu połączenia proste i odbiorczy klienta.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Zwraca identyfikator DISPID i nazwę dla każdego zdarzenia w określonym zakresie zdarzeń.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Zwraca liczbę zdarzeń widoczne w tym interfejsie.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Przerywa połączenie doradczych wcześniej ustanowione za pośrednictwem `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugProperty](../../winscript/reference/idebugproperty-interface.md)