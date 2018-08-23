---
title: SetThreadCount | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- SetThreadCount
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6d9e8e107d4935b8de659dc40f60ccaa7831def
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680608"
---
# <a name="setthreadcount"></a>SetThreadCount
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [SetThreadCount](https://docs.microsoft.com/visualstudio/msbuild/setthreadcount).  
  
  
Ustawia liczbę wątku globalnych i przypisuje obliczony wynik w bieżącym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `threadCount`  
 Liczba wątków używanych.  
  
## <a name="return-value"></a>Wartość zwracana  
 [Wartość HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) przy użyciu [sukces] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) ustawiony bit, jeśli liczba wątków został zaktualizowany.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** FileTracker.h



