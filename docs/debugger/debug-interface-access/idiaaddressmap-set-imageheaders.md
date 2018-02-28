---
title: IDiaAddressMap::set_imageHeaders | Dokumentacja firmy Microsoft
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
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 74556e2e67478cef9b495d3740dc910b62cc8293
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
Ustawia obraz nagłówków, aby włączyć translację wirtualny adres względny.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 cbData  
 [in] Liczba bajtów danych nagłówka. Musi być `n*sizeof(IMAGE_SECTION_HEADER)` gdzie `n` jest liczba nagłówków sekcji w pliku wykonywalnego.  
  
 dane]  
 [in] Tablica `IMAGE_SECTION_HEADER` struktury ma być używany jako nagłówki obrazu.  
  
 originalHeaders  
 [in] Ustaw `FALSE` z nowego obrazu, jeśli nagłówki obrazu `TRUE` jeśli odzwierciedlają oryginalnego obrazu, przed uaktualnieniem. Zwykle będzie to wartość `TRUE` tylko w połączeniu z wywołań [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `IMAGE_SECTION_HEADER` Struktury jest zadeklarowany w pliku Winnt.h i reprezentuje format nagłówka sekcji obrazu pliku wykonywalnego.  
  
 Zależą od obliczenia wirtualny adres względny `IMAGE_SECTION_HEADER` wartości. Zazwyczaj DIA pobiera z pliku programu bazy danych (.pdb). Jeśli te wartości są spełnione, nie można obliczyć względną wirtualnych adresów jest DIA i [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) metoda zwraca `FALSE`. Klient musi wywoływać [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) metodę umożliwiającą włączenie obliczeń wirtualny adres względny po podaniu Brak nagłówków obrazu z samego obrazu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)