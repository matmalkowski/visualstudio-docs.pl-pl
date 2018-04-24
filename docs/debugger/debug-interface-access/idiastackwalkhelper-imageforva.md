---
title: IDiaStackWalkHelper::imageForVA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0986a6a0b4596671cb11b40b938848387124462f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Zwraca początek obrazu pliku wykonywalnego w pamięci podany wirtualny adres gdzieś w obszarze pamięci plik wykonywalny.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vaContext`  
 [in] Wirtualny adres, który znajduje się gdzieś w miejscu do pliku wykonywalnego.  
  
 `pvaImageStart`  
 [out] Zwraca adres początkowy wirtualnego obrazu pliku wykonywalnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)