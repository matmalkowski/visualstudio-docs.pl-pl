---
title: IDiaSymbol::get_rank | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b78ba89b56c6d8c473060e39d402ee46e4ae15f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
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
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)