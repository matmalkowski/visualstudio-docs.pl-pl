---
title: IDiaSession::put_loadAddress | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa8f7c12e07f68d8c3fdd85f0d33d964847abf22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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