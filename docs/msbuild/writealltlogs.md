---
title: WriteAllTLogs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8de6a67be8390f2b4353b05eea489c07e095b092
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="writealltlogs"></a>WriteAllTLogs
Zapisuje dzienniki śledzenia dla wszystkich wątków i konteksty.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `intermediateDirectory`  
 Katalog, w którym będą przechowywane w dzienniku śledzenia.  
  
 [in] `tlogRootName`  
 Nazwa głównego nazwa pliku dziennika.  
  
## <a name="return-value"></a>Wartość zwracana  
 **HRESULT** z **zakończyło się pomyślnie** ustawiony bit, jeśli kontekst śledzenia został utworzony.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** FileTracker.h  
  
## <a name="see-also"></a>Zobacz też  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)