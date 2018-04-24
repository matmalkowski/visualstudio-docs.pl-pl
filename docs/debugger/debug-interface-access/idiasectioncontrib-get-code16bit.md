---
title: IDiaSectionContrib::get_code16bit | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code16bit method
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e253b440712a26b67870f76b241a85f5979158b3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasectioncontribgetcode16bit"></a>IDiaSectionContrib::get_code16bit
Pobiera flagę wskazującą, czy sekcja zawiera kod 16-bitowy.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_code16bit(  
   BOOL *pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca `TRUE` w przypadku kodu w sekcji 16-bitowy; w przeciwnym razie, zwraca `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Tej metody oznacza jedynie, czy kod jest 16-bitowych. Jeśli kod jest nie 16-bitowych, może to być dowolne inne, takie jak kod 32-bitowy lub 64-bitowej.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)