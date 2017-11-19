---
title: IEnumRemoteDebugApplications::Skip | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumRemoteDebugApplications.Skip
apilocation: scrobj.dll
helpviewer_keywords: IEnumRemoteDebugApplications::Skip
ms.assetid: 9f6578d9-8de5-419c-b1b5-7cb07b6367fb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f20fb057cf70e49a1f7324901f5ab77369e77251
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ienumremotedebugapplicationsskip"></a>IEnumRemoteDebugApplications::Skip
Pomija określoną liczbę segmentów w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba segmentów w kolejności wyliczenie do pominięcia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pomija określoną liczbę segmentów w kolejności wyliczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)