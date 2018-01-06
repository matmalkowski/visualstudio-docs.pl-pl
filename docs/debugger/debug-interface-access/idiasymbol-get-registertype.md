---
title: IDiaSymbol::get_registerType | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f1c98ab0-8aef-4a07-a686-28b8a54418ef
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b6ed4fb8ad9d50ca54174ff4794097b378173630
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetregistertype"></a>IDiaSymbol::get_registerType
Pobiera typ rejestru.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_registerType(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Wskaźnik do `DWORD` zawierający typ rejestru.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)