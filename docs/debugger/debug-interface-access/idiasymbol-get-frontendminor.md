---
title: IDiaSymbol::get_frontEndMinor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1f276239d76f02b9db68f7acacc52e693056f061
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetfrontendminor"></a>IDiaSymbol::get_frontEndMinor
Pobiera frontonu podrzędny numer wersji.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca front.end podrzędny numer wersji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Kompilator zazwyczaj składa się z dwóch podstawowe elementy: frontonu (analizator), która obsługuje analizowania kodu źródłowego w postaci pośredniej, oraz zaplecze (generator kodu), konwertująca pośredniego formularza do zestawu. Nie jest rzadko frontonem ma inną wersję niż wewnętrznej.  
  
 Frontonu lub zaplecza numer wersji składa się z trzech części: \<głównych >.\< drobne >. \<kompilacji >, gdzie \<głównych > numer wersji głównej \<pomocnicza > jest numerem wersji pomocniczej i \<kompilacji > jest numer kompilacji. Na przykład 13.10.3077.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)