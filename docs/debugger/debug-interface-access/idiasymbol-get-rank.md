---
title: IDiaSymbol::get_rank | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 623c700c6f9a30b6142faeb7e1b31881d0e0fe11
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
Pobiera rangę tablicy wielowymiarowej FORTRAN (liczba wymiarów).  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca liczbę wymiarów tablicy wielowymiarowej FORTRAN.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Ranga odwołuje się do liczby wymiarów w tablicy, której tablicy jest zadeklarowany jako `myarray[1,2,3]`. W tym przykładzie ma pozycję Wymiary 3 i 3. Pozycja nie ma zastosowania do języka C++, który korzysta z koncepcji tablicy tablic do każdego wymiaru (czyli `myarray[1][2][3]`).  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)