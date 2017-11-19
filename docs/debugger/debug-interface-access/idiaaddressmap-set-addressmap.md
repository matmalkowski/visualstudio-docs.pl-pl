---
title: IDiaAddressMap::set_addressMap | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49dc861b6c250c83a6c30e2dbd0fb5035671ff28
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Zawiera adres mapy do obsługi tłumaczeń Układ obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbData`  
 [in] Liczba elementów w `data` parametru.  
  
 `data[]`  
 [in] Tablica [diaaddressmapentry — struktura](../../debugger/debug-interface-access/diaaddressmapentry.md) struktury definiujące mapowania translacji.  
  
 `imagetoSymbols`  
 [in] `TRUE` Jeśli `data` parametru definiuje mapowanie z nowy układ obrazu do oryginalnego układu (zgodnie z opisem symbole debugowania). `FALSE`Jeśli `data` mapowanie do układu obrazu z oryginalnego układu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj DIA pobiera mapy translacji adresów z pliku bazy danych (.pdb) programu. Jeśli brakuje wartości [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metoda jest wywoływana dwukrotnie jeden raz z `imagetoSymbols` ustawiona `TRUE` i jeden raz z `imagetoSymbols` ustawiono parametr `FALSE`. Adres mapy tłumaczeń nie można włączyć za pomocą [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) metody ile obu mapach tłumaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Diaaddressmapentry — struktura](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [Idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)