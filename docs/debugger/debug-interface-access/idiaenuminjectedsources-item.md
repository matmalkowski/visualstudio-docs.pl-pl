---
title: IDiaEnumInjectedSources::Item | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b53112756a35c190668e76ba3bb1114ec60eb85
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Pobiera źródło wprowadzony za pomocą indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 indeks  
 [in] Indeks o [idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md) obiektu do pobrania. Indeks jest z zakresu od 0 do `count`-1, gdy `count` zwróconego przez [IDiaEnumInjectedSources::get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) metody.  
  
 injectedSource  
 [out] Zwraca [idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md) obiekt reprezentujący wprowadzony źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [Idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md)