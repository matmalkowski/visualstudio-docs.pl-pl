---
title: ISimpleConnectionPoint::Advise | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ec43d135401386a3f54f2c047040897f038ba19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Ustanawia połączenie między obiektu punktu połączenia proste i odbiorczy klienta.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdisp`  
 [in] Wskaźnik do `IDispatch` interfejsu na komputerze klienckim na powiadomienia ujścia. Zbiornik klienta odbiera połączenia wychodzące z punktu połączenia proste.  
  
 `pdwCookie`  
 [out] Wskaźnik do zwrócony tokenu, który unikatowo identyfikuje tego połączenia. Obiekt wywołujący używa tego tokenu później można usunąć połączenia przez przekazanie jej `ISimpleConnectionPoint::Unadvise` metody. Jeśli połączenie nie zostało pomyślnie nawiązane, ta wartość wynosi zero.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ustanawia połączenie między obiektu punktu połączenia proste i odbiorczy klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)