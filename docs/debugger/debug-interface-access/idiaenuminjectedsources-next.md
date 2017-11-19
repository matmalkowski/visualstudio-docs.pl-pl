---
title: IDiaEnumInjectedSources::Next | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumInjectedSources::Next method
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aadfe4a6d4e66cca92f6e84cef23ebeace77afa1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
Pobiera określoną liczbę źródeł wprowadzony w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba źródeł wprowadzony w moduł wyliczający, które mają zostać pobrane.  
  
 rgelt  
 [out] Zwraca tablicę [idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md) obiektów, które reprezentuje żądany wprowadzony źródeł.  
  
 pceltFetched  
 [out] Zwraca liczbę źródeł wprowadzony w pobranych modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli istnieją już wprowadzony źródła. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [Idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md)