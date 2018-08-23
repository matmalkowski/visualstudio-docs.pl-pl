---
title: Idialinenumber::get_statement — | Dokumentacja firmy Microsoft
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
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e1329cfe00bd6af4e93bc4b45c4328232b9c22df
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680228"
---
# <a name="idialinenumbergetstatement"></a>IDiaLineNumber::get_statement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [idialinenumber::get_statement —](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialinenumber-get-statement).  
  
Pobiera flagę wskazującą, czy te informacje w tym artykule opisano początku instrukcji zamiast wyrażenia w źródle programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT get_statement (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca `TRUE` Jeśli te informacje w tym artykule opisano początku instrukcji w źródle programu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcje mogą znajdować się na wiele wierszy. Ta metoda wskazuje, jeśli numer wiersza skojarzone oznacza początek instrukcji wiele wierszy.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)



