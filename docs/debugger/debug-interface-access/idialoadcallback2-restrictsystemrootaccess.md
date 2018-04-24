---
title: IDiaLoadCallback2::RestrictSystemRootAccess | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 000d0b5ce21b6b50b1abab76aa8bf4a7bb1cd62a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
Określa, czy potrzeby wyszukiwania plików PDB jest dozwolone w katalogu głównym systemu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT RestrictSystemRootAccess();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Inne niż powrotnych kodu `S_OK` uniemożliwia wyszukiwanie katalog główny systemu plików PDB.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)