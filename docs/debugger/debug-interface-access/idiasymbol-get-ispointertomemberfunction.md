---
title: IDiaSymbol::get_isPointerToMemberFunction | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aa9b5599-9602-41be-ab50-d84b90bee72f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d241fdc15af586dc218e9667e02c45dafda0e356
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetispointertomemberfunction"></a>IDiaSymbol::get_isPointerToMemberFunction
Określa, czy ten symbol jest wskaźnikiem do funkcji członkowskiej.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_isPointerToMemberFunction(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Wskaźnik do `BOOL` określający, czy ten symbol jest wskaźnikiem do funkcji członkowskiej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)