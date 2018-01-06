---
title: WriteAllTLogs | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: WriteAllTLogs
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8abc76ef0c9d3e04f0aae676af0bfa20183b3a8d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="writealltlogs"></a>WriteAllTLogs
Zapisuje dzienniki śledzenia dla wszystkich wątków i konteksty.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`intermediateDirectory`  
 Katalog, w którym będą przechowywane w dzienniku śledzenia.  
  
 [in]`tlogRootName`  
 Nazwa głównego nazwa pliku dziennika.  
  
## <a name="return-value"></a>Wartość zwracana  
 **HRESULT** z **zakończyło się pomyślnie** ustawiony bit, jeśli kontekst śledzenia został utworzony.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** FileTracker.h  
  
## <a name="see-also"></a>Zobacz też  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)