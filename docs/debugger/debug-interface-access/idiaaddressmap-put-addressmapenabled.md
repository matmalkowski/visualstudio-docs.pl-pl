---
title: IDiaAddressMap::put_addressMapEnabled | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: caf138a951b2857bee4f56bf6b8713f98bf4c1b4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Określa, czy mapa adres powinien być używany do translacji adresów symbolu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 NewVal  
 [in] Ustaw `TRUE` Aby włączyć translację symboli, lub `FALSE` można wyłączyć.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wykonywalny procesorów po aktualizacji czasami pliku wykonywalnego. DIA zawiera mechanizm obsługi tłumaczenia symboli do nowego układu.  
  
 Podczas ładowania pliku PDB przechowywane w pliku mapy adres jest włączone. Brak sytuacji, gdy aplikacja kliencka może być konieczne podanie mapy własnego adresu przez wywołanie metody [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metody. Jeśli `set_addressMap` metody zakończy się pomyślnie, należy wywołać aplikacja kliencka `put_addressMapEnabled` metody z `NewVal` parametr `TRUE` umożliwia korzystanie z tego adresu mapy.  
  
 Bieżący stan mapowania adresów włączania mogą zostać pobrane z wywołaniem do [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)