---
title: IDebugApplicationNodeEvents::onRemoveChild | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNodeEvents.onRemoveChild
apilocation: scrobj.dll
helpviewer_keywords: IDebugApplicationNodeEvents::onRemoveChild
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a62f187286f66f8adff8acda339e02a02bc6225
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeeventsonremovechild"></a>IDebugApplicationNodeEvents::onRemoveChild
Obsługuje zdarzenie, gdy węzeł podrzędny zostanie usunięty z obiektu węzła debugowania aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prddpChild`  
 [in] Aplikacji podrzędnym, który został usunięty.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje zdarzenie, gdy węzeł podrzędny zostanie usunięte z obiektu węzła debugowania aplikacji.  
  
 Implementacje z `IDebugApplicationNode` interfejsu Zgłoś to zdarzenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)   
 [Interfejs IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)