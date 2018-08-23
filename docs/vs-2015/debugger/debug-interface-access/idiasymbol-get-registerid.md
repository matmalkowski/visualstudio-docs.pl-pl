---
title: Idiasymbol::get_registerid — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c56467426840fe9bd9cbb62c77b6f0889126647
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677103"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiasymbol::get_registerid —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-registerid).  
  
Pobiera oznaczenie Zarejestruj się w lokalizacji, gdy [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ustawiono `LocIsEnregistered`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca oznaczenie rejestru lokalizacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli symbol jest określana względem rejestru, oznacza to, jeśli symbol [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) jest ustawiona na `LocIsRegRel`, użyj `get_registerId` metody następuje po wywołaniu [idiasymbol::get_offset —](../../debugger/debug-interface-access/idiasymbol-get-offset.md) Metoda pobieranie przesunięcia z rejestru, w którym znajduje się symbol.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)



