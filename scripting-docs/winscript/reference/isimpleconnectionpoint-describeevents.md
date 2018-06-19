---
title: ISimpleConnectionPoint::DescribeEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42dab9558d46eae0fbb640c60264a79877708321
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796360"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Zwraca identyfikator DISPID i nazwę dla każdego zdarzenia w określonym zakresie zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iEvent`  
 [in] Indeks pierwszego zdarzenia do pobrania.  
  
 `cEvents`  
 [in] Liczba zdarzeń do pobrania.  
  
 `prgid`  
 [out] Tablica wartości DISPID zdarzenia.  
  
 `prgbstr`  
 [out] Tablica nazw zdarzeń.  
  
 `pcEventsFetched`  
 [out] Rzeczywista liczba zdarzeń pobrane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`S_FALSE`|Więcej zdarzeń żądano nie były dostępne. Zdarzenia niedostępne są reprezentowane DISPID_NULL i BSTR wartości null.|  
|`E_INVALIDARG`|Brak elementów może zostać pobrane.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca identyfikator DISPID i nazwy dla każdego zdarzenia w określonym zakresie zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)