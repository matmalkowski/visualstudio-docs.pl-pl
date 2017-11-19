---
title: IActiveScriptStats::GetStat | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptStats.GetStat
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e791661de6d360f747f8d823ad073c2eb81115
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Zwraca jedną z statystyki skrypty standardowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stid`  
 [in] Określa statystykę do zwrócenia. Musi mieć wartość:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Zwróć liczbę instrukcje wykonywane, ponieważ skrypt uruchomiony lub statystyki zostały zresetowane.|  
  
 `pluHi`  
 [out] Wysoka 32 bity 64-bitowa liczba całkowita bez znaku reprezentujący statystyki.  
  
 `pluLo`  
 [out] Niski 32 bity 64-bitowa liczba całkowita bez znaku reprezentujący statystyki.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Możliwe wartości zawierają, ale nie są ograniczone do wartości w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca jedną statystyk skrypty standardowe.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Interfejs IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)