---
title: IDiaLoadCallback2::RestrictReferencePathAccess | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03c3a6239b41fec44098850973ddcd4839b808a8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Określa, czy wyszukiwanie plik PDB jest dozwolone w ścieżce, w którym znajduje się plik .exe.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT RestrictReferencePathAccess();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Inne niż powrotnych kodu `S_OK` zapobiegające szuka pliku .pdb w ścieżce, w którym znajduje się plik .exe.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)