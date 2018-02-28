---
title: IDiaSymbol::get_frontEndMajor | Dokumentacja firmy Microsoft
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
- IDiaSymbol::get_frontEndMajor method
ms.assetid: f8a067c5-3306-4fc5-bc20-8910a47ed504
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fed60a541fa63e6bb733c82c87b7b55eb4c24e6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetfrontendmajor"></a>IDiaSymbol::get_frontEndMajor
Pobiera numer wersji głównej frontonu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_frontEndMajor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca numer wersji głównej frontonu. Zobacz uwagi.  
  
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