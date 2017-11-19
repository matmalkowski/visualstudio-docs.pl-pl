---
title: "IJsDebugDataTarget::ReadNullTerminatedString — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadNullTerminatedString
apilocation: jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94cb90b8b44aa5dab13a2e916dec22ae950e77ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString — Metoda
Odczytuje określoną liczbę znaków z elementem docelowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres do odczytu.  
  
 `characterSize`  
 [rozmiar każdego znaku w ciągu in]  
  
 `maxCharacters`  
 [in] Maksymalna liczba znaków do odczytania. wartość elementu maxCharacters powinna być uzasadnione. Wszystkie żądania dla więcej niż 128MB pamięci zakończy się niepowodzeniem.  Jeśli ten ciąg jest większy niż wartość elementu maxCharacters, ciąg wynik zostanie obcięty po wartość elementu maxCharacters.  
  
 `pString`  
 [out] BSTR odczytywać z elementem docelowym.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca wartości S_FALSE, jeśli obcięte.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugdatatarget — interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)