---
title: IDiaFrameData::get_lengthBlock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthBlock method
ms.assetid: 2e54deb7-7744-428e-913c-1d47a2aa89b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63e5645aa92c7078ce93b8158375e9ab4c2a87d0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31460599"
---
# <a name="idiaframedatagetlengthblock"></a>IDiaFrameData::get_lengthBlock
Pobiera długość w bajtach bloku kodu opisanego przez ramki.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_lengthBlock (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca liczbę bajtów kodu w ramce.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez tę metodę jest zwykle używanych w interpretacji ciąg programu (zobacz [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) metody dla definicji ciąg program).  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)