---
title: Diaaddressmapentry — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 0a29de8f18a9d3123d73210d0e362c2ae2d32641
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
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