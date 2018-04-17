---
title: Diaaddressmapentry — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc13e8813c0e1bddd1f6cb9abd3d70b26eb5a8e1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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