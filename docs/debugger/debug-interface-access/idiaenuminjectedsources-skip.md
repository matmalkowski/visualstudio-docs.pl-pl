---
title: IDiaEnumInjectedSources::Skip | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumInjectedSources::Skip method
ms.assetid: 4aad6a51-f2d3-4064-b216-60d830d0a560
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0415169f34a3b80b00521564623b3a844fa52fe4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenuminjectedsourcesskip"></a>IDiaEnumInjectedSources::Skip
Pomija określoną liczbę źródeł wprowadzony w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba źródeł wprowadzony w kolejności wyliczenie do pominięcia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` Jeśli istnieją już wprowadzony źródła do pominięcia.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)