---
title: SetThreadCount | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 059c3015bf542dda6a420c80620bc74c9ee6ca6b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="setthreadcount"></a>SetThreadCount
Ustawia liczbę wątków globalne i przypisuje tej liczby do bieżącego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `threadCount`  
 Liczba wątków używanych.  
  
## <a name="return-value"></a>Wartość zwracana  
 **HRESULT** z **zakończyło się pomyślnie** ustawiony bit, jeśli liczba wątków został zaktualizowany.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** FileTracker.h