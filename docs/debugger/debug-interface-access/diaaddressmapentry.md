---
title: "Diaaddressmapentry — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1324ea79ec60a61e315253573b9d4aa3ced2695
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
W tym artykule opisano wpis w mapie adres.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Elementy  
 `rva`  
 Wirtualny adres względny (RVA) w obrazie A.  
  
 `rvaTo`  
 Wirtualny adres względny `rva` jest mapowany na obrazie B.  
  
## <a name="remarks"></a>Uwagi  
 Mapa adres zawiera tłumaczenia z jednego obrazu układu (A) do innej (B). Tablica `DiaAddressMapEntry` strukturami posortowane według `rva` definiuje mapę adresu.  
  
 Tłumaczenie adresów `addrA`, w obrazie A adres `addrB`, ilustracji B, wykonaj następujące czynności:  
  
1.  Mapy dla wejścia, wyszukaj `e`, z największą `rva` mniejsze niż lub równe `addrA`.  
  
2.  Ustaw `delta = addrA - e.rva`.  
  
3.  Ustaw `addrB = e.rvaTo + delta`.  
  
 Tablica `DiaAddressMapEntry` struktury są przekazywane do [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dia2.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)