---
title: "Idiareadexeatrvacallback — | Dokumentacja firmy Microsoft"
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
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fdc876897d5106f4d03d5b25b51dec5572837f21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Umożliwia aplikacji klienta umożliwiają określanie wartości bajtów plik wykonywalny określony przez wirtualny adres względny.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDiaReadExeAtRVACallback`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Odczytuje określoną liczbę bajtów, licząc od określonej wirtualnej adres względny (RVA) z pliku wykonywalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja kliencka implementuje ten interfejs w celu zapewnienia bajtów plik wykonywalny przy użyciu adresu względnego wirtualnego do pliku wykonywalnego. Aby korzystać z przesunięciem bezwzględna do pliku, należy zaimplementować [idiareadexeatoffsetcallback —](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ta metoda jest implementowany przez aplikację klienta i przekazane do [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody jako metody alternatywnej dla odczytu pliku.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)