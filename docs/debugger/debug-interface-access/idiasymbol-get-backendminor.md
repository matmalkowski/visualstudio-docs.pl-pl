---
title: IDiaSymbol::get_backEndMinor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 292613903d30145f776654dbd3789894c5c3380b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465671"
---
# <a name="idiasymbolgetbackendminor"></a>IDiaSymbol::get_backEndMinor
Pobiera zaplecza podrzędny numer wersji kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca numer wersji pomocniczej zaplecza. Zobacz uwagi.  
  
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