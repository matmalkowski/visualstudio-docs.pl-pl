---
title: IDiaSectionContrib::get_informational | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_informational method
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b8d991a5444c719696db62ab6f9c3374015ea7e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasectioncontribgetinformational"></a>IDiaSectionContrib::get_informational
Pobiera flagę wskazującą, czy sekcja zawiera komentarze lub podobne informacje.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_informational(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca `TRUE` Jeśli sekcja zawiera komentarze lub inne informacje; w przeciwnym razie zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj .directive sekcja zawiera informacje.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)