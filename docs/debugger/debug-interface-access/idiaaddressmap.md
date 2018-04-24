---
title: Idiaaddressmap — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb1593f59125c4b6325bfd97015485cc2a4d85f6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Zapewnia kontrolę nad jak DIA SDK oblicza wirtualnych i względną wirtualnych adresów dla obiektów debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDiaAddressMap`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Wskazuje, czy mapa adresów została ustanowiona dla określonej sesji.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Określa, czy mapa adres powinien być używany do translacji adresów symbolu.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Wskazuje, czy włączono obliczania i Użyj względnych adresów wirtualnych.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Umożliwia klientowi Włączanie lub wyłączanie obliczania względnych adresów wirtualnych.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Pobiera bieżący wyrównanie obrazu.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Ustawia wyrównanie obrazu.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Ustawia obraz nagłówków, aby włączyć translację adresów wirtualnych względną.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Zawiera adres mapy do obsługi tłumaczeń Układ obrazu.|  
  
## <a name="remarks"></a>Uwagi  
 Kontroli, podana przez ten interfejs jest hermetyzowany w dwóch zestawów danych, należy podać: obraz nagłówki i rozwiąż mapy. Większość klienci używają [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodę, aby znaleźć informacje o debugowaniu właściwe dla obrazu, a także metoda zwykle można odnaleźć wszystkie niezbędne nagłówki i map samych danych. Jednak niektórzy klienci implementuje specjalne przetwarzania i wyszukiwania danych. Tacy klienci użyć metod `IDiaAddressMap` interfejsu zapewnienie DIA SDK w wynikach wyszukiwania.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest dostępny z DIA obiektu session. Wywołania klienta `QueryInterface` metody interfejsu DIA sesji obiektu, zwykle [idiasession —](../../debugger/debug-interface-access/idiasession.md), aby pobrać `IDiaAddressMap` interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)