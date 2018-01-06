---
title: IDiaFrameData::get_functionStart | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c7cd995a695f809737c0dbc4adfab0e76e2c8266
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaframedatagetfunctionstart"></a>IDiaFrameData::get_functionStart
Pobiera flagę wskazującą, czy blok zawiera punkt wejścia funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca `TRUE` Jeśli blok zawiera punkt wejścia; w przeciwnym razie zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Istnieje możliwość ramka stosu nie będzie uruchomienia funkcji, ponieważ ramka reprezentuje wbudowanego metody lub funkcji wstawione do funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)