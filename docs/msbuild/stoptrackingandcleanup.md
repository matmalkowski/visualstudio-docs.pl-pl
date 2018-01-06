---
title: StopTrackingAndCleanup | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: StopTrackingAndCleanup
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c4ed935391ecdca464bc4b7e3b6e38342ad5afdc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Zatrzymuje wszystkie śledzenia i zwalnia wszystkie pamięci używane w sesji śledzenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca **HRESULT** z **zakończyło się pomyślnie** bitu zatrzymanie śledzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** FileTracker.h  
  
## <a name="see-also"></a>Zobacz też  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)