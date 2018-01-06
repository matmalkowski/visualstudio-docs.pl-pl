---
title: IDiaSymbol::get_hasInlAsm | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_hasInlAsm method
ms.assetid: 7001c7cc-1459-4929-851b-a08066a803c6
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fb8906a73ca6c15418c204ad25f449f3847725de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgethasinlasm"></a>IDiaSymbol::get_hasInlAsm
Pobiera flagę określającą, czy funkcja zawiera wbudowany zestaw.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_hasInlAsm(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFlag`  
 [out] Zwraca `TRUE` Jeśli funkcja ma wbudowany zestaw; w przeciwnym razie zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|DIA SDK w wersji 8.0|  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)