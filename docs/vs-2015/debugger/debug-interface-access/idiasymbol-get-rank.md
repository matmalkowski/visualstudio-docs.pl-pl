---
title: Idiasymbol::get_rank — | Dokumentacja firmy Microsoft
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
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbf31535c1af5e597ca3fed4d3d878f0277c48f4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682462"
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiasymbol::get_rank —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-rank).  
  
Pobiera rangę tablicy wielowymiarowej FORTRAN (liczba wymiarów).  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca liczbę wymiarów w tablicy wielowymiarowej FORTRAN.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Ranga odnosi się do liczby wymiarów w tablicy, gdy tablica jest zadeklarowana jako `myarray[1,2,3]`. W tym przykładzie randze wymiary 3 i 3. Ranga nie ma zastosowania do języka C++, która korzysta z koncepcji tablicy tablic dla każdego wymiaru (czyli `myarray[1][2][3]`).  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



