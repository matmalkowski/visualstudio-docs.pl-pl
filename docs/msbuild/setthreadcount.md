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
ms.openlocfilehash: 9cc9a1ae5f7fb51981f3cebc4d6fa658f614de6d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151843"
---
# <a name="setthreadcount"></a>SetThreadCount
Ustawia liczbę wątku globalnych i przypisuje obliczony wynik w bieżącym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `threadCount`  
 Liczba wątków używanych.  
  
## <a name="return-value"></a>Wartość zwracana  
 **HRESULT** z **Powodzenie** bitu, jeśli liczba wątków został zaktualizowany.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *FileTracker.h*