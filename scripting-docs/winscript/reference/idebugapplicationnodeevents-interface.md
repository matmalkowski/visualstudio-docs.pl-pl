---
title: Interfejs IDebugApplicationNodeEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20d0fac68bb7cdb3d7f5cb6aac6b0ab67e373c84
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794125"
---
# <a name="idebugapplicationnodeevents-interface"></a>Interfejs IDebugApplicationNodeEvents
Udostępnia interfejs zdarzeń dla `IDebugApplicationNode` interfejsu.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugApplicationNodeEvents` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Obsługuje zdarzenie, gdy węzeł podrzędny zostanie dodany do obiektu węzła debugowania aplikacji.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Obsługuje zdarzenie, gdy węzeł podrzędny zostanie usunięty z obiektu węzła debugowania aplikacji.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Obsługuje zdarzenie, co oznacza, że obiekt węzła debugowania aplikacji została odłączona od węzła nadrzędnego.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Obsługuje zdarzenie, co oznacza, że obiekt węzła debugowania aplikacji został dołączony do węzła nadrzędnego.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)