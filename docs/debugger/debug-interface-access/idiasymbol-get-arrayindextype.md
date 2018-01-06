---
title: IDiaSymbol::get_arrayIndexType | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_arrayIndexType method
ms.assetid: cd63b9ec-9694-406c-b37f-bde6bd5fcbf2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f7fd423ee6b682704a5c3cc4459a91868983efd8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetarrayindextype"></a>IDiaSymbol::get_arrayIndexType
Pobiera interfejs symbol typu indeksu tablicy symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_arrayIndexType (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt, który reprezentuje typ indeksu tablicy symbolu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku niektórych języków można określić typ używany jako indeks tablicy. Symbol zwracane z tej metody określa typu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)