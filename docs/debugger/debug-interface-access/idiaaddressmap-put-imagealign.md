---
title: IDiaAddressMap::put_imageAlign | Dokumentacja firmy Microsoft
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
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1769ec6286cda1c6616c97978bdec94e0c5f2f5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Ustawia wyrównanie obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 NewVal  
 [in] Nowa wartość wyrównanie obrazu pliku wykonywalnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Obrazy (załadować pliki wykonywalne) są wyrównane do granice określonej pamięci. Wyrównanie takie mogą mieć wpływ przez bieżący architektura systemu i opcje czasu kompilacji i łącza. Wyrównanie obrazu jest zawsze włączona bajtowych granicach. Następujące wartości wyrównanie obrazu są prawidłowe: 1, 2, 4, 8, 16, 32 i 64-bajtowych granicach.  
  
 Bieżący wyrównanie obrazu może zostać pobrany z wywołaniem do [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) metody.  
  
> [!NOTE]
>  Obraz jest już załadowany w czasie, który można wywołać tej metody. `put_imageAlign` Metody zwykle jest używana, gdy obraz został przeniesiony lub zmienić i nowych wyrównania jest wymagana.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaaddressmap —](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)