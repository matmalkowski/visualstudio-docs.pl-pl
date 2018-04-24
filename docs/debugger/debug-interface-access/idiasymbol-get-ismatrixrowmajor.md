---
title: IDiaSymbol::get_isMatrixRowMajor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36b1e881-ea76-48b0-b67f-e9eb0d19bec7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af4d1817de2886ededb019942b55271480176ba8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetismatrixrowmajor"></a>IDiaSymbol::get_isMatrixRowMajor
Określa, czy macierz głównych wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_isMatrixRowMajor(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Wskaźnik do `BOOL` który określa, czy macierz głównych wiersza.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)