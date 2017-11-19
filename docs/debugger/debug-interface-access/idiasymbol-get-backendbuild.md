---
title: IDiaSymbol::get_backEndBuild | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_backEndBuild method
ms.assetid: 423af497-9294-438e-92b4-456c6f56dc56
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc1d06aa488335c8a7d551d59d9ecf3d3beea9f2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetbackendbuild"></a>IDiaSymbol::get_backEndBuild
Pobiera numer kompilacji zapleczu kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_backEndBuild (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca numer kompilacji zaplecza. Zobacz uwagi.  
  
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
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)