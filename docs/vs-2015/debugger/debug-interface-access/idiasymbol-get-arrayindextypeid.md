---
title: Idiasymbol::get_arrayindextypeid — | Dokumentacja firmy Microsoft
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
- IDiaSymbol::get_arrayIndexTypeId method
ms.assetid: 124f86e2-6f66-4541-87c3-799f435b731e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a47eda45032bbab591b5ea7c8e9ab427bb26aa93
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42671046"
---
# <a name="idiasymbolgetarrayindextypeid"></a>IDiaSymbol::get_arrayIndexTypeId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idiasymbol::get_arrayindextypeid —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-arrayindextypeid).  
  
Pobiera identyfikator typu indeksu tablicy symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_arrayIndexTypeId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca identyfikator typu indeksu tablicy symbolu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.  
  
> [!NOTE]
>  Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Identyfikator jest wartością unikatową, utworzone przez DIA SDK, aby oznaczyć wszystkie symbole jako unikatowy.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



