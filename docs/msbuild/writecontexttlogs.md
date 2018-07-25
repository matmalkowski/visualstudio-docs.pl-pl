---
title: WriteContextTLogs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a01dbd11411204affa082bfa0772530662657853
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230802"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
Zapisuje pliki dziennika dla bieżącego kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `intermediateDirectory`  
 Katalog, w którym mają zostać zapisane w dzienniku śledzenia.  
  
 [in] `tlogRootName`  
 Nazwa głównej nazwy pliku dziennika.  
  
## <a name="return-value"></a>Wartość zwracana  
 **HRESULT** z **Powodzenie** bitu, jeśli kontekst śledzenia został utworzony.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *FileTracker.h*  
  
## <a name="see-also"></a>Zobacz także  
 [WriteAllTLogs](../msbuild/writealltlogs.md)