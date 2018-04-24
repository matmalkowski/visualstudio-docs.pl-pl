---
title: IDiaEnumLineNumbers::Clone | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Clone method
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb864ea3331db9a8150099d85bc6fc5c64436c7b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumlinenumbersclone"></a>IDiaEnumLineNumbers::Clone
Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Clone (   
   IDiaEnumLineNumbers** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppenum`  
 [out] Zwraca [idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md) obiekt, który zawiera zduplikowane modułu wyliczającego. Zduplikowany wiersz, który liczby nie są tylko moduł wyliczający.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)