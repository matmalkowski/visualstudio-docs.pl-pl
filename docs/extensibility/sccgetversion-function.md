---
title: Funkcja SccGetVersion | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetVersion
helpviewer_keywords: SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f64b1412d0750bba4d3985d33286915e22f1474
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="sccgetversion-function"></a>Funkcja SccGetVersion
Ta funkcja pobiera numer wersji API dodatku typu Plug-in kontroli źródła obsługiwane przez wtyczkę kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 A `LONG` typu danych, która zawiera numer wersji obsługiwanych API dodatku typu Plug-in kontroli źródła:  
  
|WORD|Opis|  
|----------|-----------------|  
|HIWORD|Wersja główna|  
|LOWORD|Wersja pomocnicza|  
  
## <a name="remarks"></a>Uwagi  
 Na przykład jeśli wtyczka do kontroli źródła obsługuje wersji 1.3 API dodatku typu Plug-in kontroli źródła, ta funkcja zwróci 0x0103.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)