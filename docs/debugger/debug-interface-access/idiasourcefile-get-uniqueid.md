---
title: IDiaSourceFile::get_uniqueId | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3714ce733b0388e3ac462a9495360171971a6750
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasourcefilegetuniqueid"></a>IDiaSourceFile::get_uniqueId
Pobiera wartość klucza proste liczba całkowita, która jest unikatowa dla tego obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca wartość klucza proste liczba całkowita, która jest unikatowa dla tego obrazu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Porównanie kluczy zamiast ciągi można przyspieszyć przetwarzania numeru wiersza.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)