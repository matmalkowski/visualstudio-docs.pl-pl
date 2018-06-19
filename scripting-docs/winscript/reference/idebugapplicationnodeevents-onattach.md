---
title: IDebugApplicationNodeEvents::onAttach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAttach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAttach
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a45fff15ce4f7faf6cf8714cbf01289e69f67691
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793942"
---
# <a name="idebugapplicationnodeeventsonattach"></a>IDebugApplicationNodeEvents::onAttach
Obsługuje zdarzenie, co oznacza, że obiekt węzła debugowania aplikacji został dołączony do węzła nadrzędnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prddpParent`  
 [in] Węzeł aplikacji debugowania, który jest nadrzędny tego węzła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje zdarzenie, co oznacza, że obiekt węzła debugowania aplikacji został dołączony do węzła nadrzędnego.  
  
 Implementacje z `IDebugApplicationNode` interfejsu Zgłoś to zdarzenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)   
 [Interfejs IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)