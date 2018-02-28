---
title: IDebugApplication::FireDebuggerEvent | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4cb02390602b6b93b8c233f245ede395833d67e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Wyzwala zdarzenie generyczne debugera `IApplicationDebugger` interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 [in] Identyfikator GUID obiektu.  
  
 `punk`  
 [in] Obiekt zdarzenia do przekazania do debugera.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Metoda nie jest obecnie zaimplementowana.|  
  
## <a name="remarks"></a>Uwagi  
 Semantyka identyfikator GUID i `IUnknown` są całkowicie zdefiniowane aplikacji/debugera.  
  
 Ta metoda umożliwia dla niestandardowych rozszerzeń modelu debugera; nie jest obecnie zaimplementowana.  
  
 Ta metoda powoduje `IApplicationDebugger::onDebuggerEvent` do wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)