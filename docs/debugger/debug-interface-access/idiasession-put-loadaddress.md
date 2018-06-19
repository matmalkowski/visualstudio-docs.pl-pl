---
title: IDiaSession::put_loadAddress | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: b0b04db800e5b61ef1598fe4c81a9ab362e375e3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31462649"
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