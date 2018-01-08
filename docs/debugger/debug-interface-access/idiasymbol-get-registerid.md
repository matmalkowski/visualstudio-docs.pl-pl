---
title: IDiaSymbol::get_registerId | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c944869d48c484f7ddf234f4e00a5d10e96f70ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
Pobiera oznaczeniem rejestru lokalizacji, gdy [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ma ustawioną wartość `LocIsEnregistered`.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca oznaczeniem rejestru lokalizacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli symbol jest określana względem rejestr, oznacza to, jeśli symbol [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ustawiono `LocIsRegRel`, użyj `get_registerId` metody następuje wywołanie [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) Metoda get przesunięcie z rejestru, w którym znajduje się symbol.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)