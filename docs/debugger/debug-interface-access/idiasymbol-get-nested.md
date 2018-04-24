---
title: IDiaSymbol::get_nested | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_nested method
ms.assetid: 6ae46d43-8486-48d6-a6f2-d73ebf4023e3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c43ffa3306254cb9ed14c9d987f24dd170f1d6c3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetnested"></a>IDiaSymbol::get_nested
Pobiera flagę określającą, czy jest zagnieżdżony typ danych zdefiniowany przez użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_nested (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca `TRUE` Jeśli jest zagnieżdżony typ danych zdefiniowany przez użytkownika; w przeciwnym razie zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)