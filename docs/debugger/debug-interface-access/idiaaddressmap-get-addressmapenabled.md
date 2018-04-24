---
title: IDiaAddressMap::get_addressMapEnabled | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cacee6377eebcc4e73f8f650bff4f4d3e500af66
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Wskazuje, czy mapa adresów została ustanowiona dla określonej sesji.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pRetVal  
 [out] Zwraca `TRUE` włączenie mapowanie adresów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wykonywalny procesorów po aktualizacji czasami pliku wykonywalnego. DIA zawiera mechanizm obsługi tłumaczenia symboli do nowego układu.  
  
 Aplikacje klienckie można ustawić Mapa adresów dla określonej sesji pobierając [idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md) interfejsu z [idiasession —](../../debugger/debug-interface-access/idiasession.md) interfejsu i wywoływania [IDiaAddressMap::set_ addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metody następuje wywołanie [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) metody. `get_addressMapEnabled` Metoda zwraca wyniki wywołania `put_addressMapEnabled` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)