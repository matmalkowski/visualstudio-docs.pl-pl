---
title: IJsDebugDataTarget::ReadBSTR — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadBSTR
apilocation:
- jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85fbdb556b59c67610ad65b7e1f056399ad6da58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794614"
---
# <a name="ijsdebugdatatargetreadbstr-method"></a>IJsDebugDataTarget::ReadBSTR — Metoda
Odczytuje BSTR z docelowego debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres do odczytu.  
  
 `pString`  
 [out] BSTR odczytywać cel debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca E_JsDEBUG_INVALID_MEMORY_ADDRESS, jeśli adres nie jest prawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugdatatarget — interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)