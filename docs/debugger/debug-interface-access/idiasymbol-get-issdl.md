---
title: IDiaSymbol::get_isSdl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6aa0e116-da75-4643-a4d7-d8e142231e21
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5fdffdc4f5f86077d50ac46e1888206d18bf98cb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetissdl"></a>IDiaSymbol::get_isSdl
Określa, czy moduł jest skompilowana przy użyciu opcji/SDL.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_isSdl(  
   BOOL *pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Wskaźnik do `BOOL` Określa, czy moduł jest skompilowana przy użyciu opcji/SDL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)