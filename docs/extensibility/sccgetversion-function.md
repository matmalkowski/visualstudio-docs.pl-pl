---
title: Funkcja SccGetVersion | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70beb89f13d2f752f3adb0f25e2b370fa272171a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)