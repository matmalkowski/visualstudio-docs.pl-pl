---
title: IDiaEnumLineNumbers::Clone | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumLineNumbers::Clone method
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 10a4c01d61c92cced088caf706d1dcecf01e43ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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