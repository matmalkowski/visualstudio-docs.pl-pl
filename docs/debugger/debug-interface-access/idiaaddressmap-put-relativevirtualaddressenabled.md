---
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2bfaf90afcd2129379d1ce7ae3f2d8afb619ca1e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Zezwala na kliencie włączyć lub wyłączyć Obliczanie i Użyj względnych adresów wirtualnych (RVA).  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 NewVal  
 [in] Ustaw `TRUE` Aby włączyć, lub `FALSE` można wyłączyć.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Adresy dla obiektów debugowania opisanego przez interfejsy DIA i względem obrazu wykonywalnego podstawowej, można pobrać jako względną wirtualnych adresów.  
  
 Użycie RVAs jest włączona, gdy segmentów są wstępnie załadowane z pliku PDB. Aby uzyskać bieżący stan wykorzystania RVAs, należy wywołać [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) metody.  
  
 `put_relativeVirtualAddress` Można wywołać metody, aby włączyć RVAs po pomyślnym nawiązaniu połączenia z [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metody przejęło nowe nagłówki obrazu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)