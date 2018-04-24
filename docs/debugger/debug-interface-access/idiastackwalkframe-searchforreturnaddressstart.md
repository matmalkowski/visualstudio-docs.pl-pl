---
title: IDiaStackWalkFrame::searchForReturnAddressStart | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddressStart method
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2581233ceaba4ccf7d4e8593caf7f8b4dd306364
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkframesearchforreturnaddressstart"></a>IDiaStackWalkFrame::searchForReturnAddressStart
Wyszukuje ramka stosu określony dla adres zwrotny lub prawie określony adres.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT searchForReturnAddressStart (   
   IDiaFrameData* frame,  
   ULONGLONG      startAddress,  
   ULONGLONG*     returnAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `frame`  
 [in] [Idiaframedata —](../../debugger/debug-interface-access/idiaframedata.md) obiekt, który reprezentuje bieżącej ramki stosu.  
  
 `startAddress`  
 [in] Jest adresem pamięci wirtualnej, z którego można rozpocząć wyszukiwanie.  
  
 `returnAddress`  
 [out] Zwraca adres, aby zwracany najbliższej funkcji `startAddress`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiastackwalkframe —](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)