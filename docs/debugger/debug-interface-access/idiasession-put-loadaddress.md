---
title: IDiaSession::put_loadAddress | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f4721ee818c4dc75d883c7accd2faa162521de13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Ustawia adres obciążenia dla pliku wykonywalnego, który odpowiada symboli w tym magazynie symboli.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `NewVal`  
 [in] Załaduj adres do pliku wykonywalnego.  
  
## <a name="remarks"></a>Uwagi  
 Właściwości wirtualnego adresu (VA) symbolu są obliczane przy użyciu wartości tej metody. Wirtualne adresy nie zostaną obliczone, chyba że ta właściwość ma wartość inną niż zero.  
  
> [!NOTE]
>  Tej metody należy wywołać po przejściu [idiasession —](../../debugger/debug-interface-access/idiasession.md) obiektu i przed rozpoczęciem przy użyciu obiektu, jeśli należy użyć dowolnej właściwości wirtualnych symboli.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)