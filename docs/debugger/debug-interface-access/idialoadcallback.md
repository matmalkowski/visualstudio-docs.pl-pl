---
title: "Idialoadcallback — | Dokumentacja firmy Microsoft"
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
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5cc40b8041ea5427d223a70c7d3d9347c48be286
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Odbiera wywołania zwrotne z symboli DIA lokalizowanie procedury, umożliwiając w ten sposób raport dotyczący postępu próba lokalizacji do interfejsu użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaLoadCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Następujące metody są udostępniane przez ten interfejs:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Wywoływane, gdy katalog debugowania został znaleziony w pliku .exe.|  
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Wywoływane, gdy plik .dbg candidate został otwarty.|  
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Wywoływane, gdy został otwarty plik PDB kandydata.|  
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Określa, czy zapytania rejestru mogą być używane można zlokalizować ścieżki wyszukiwania symboli.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Określa, czy jest dozwolony dostęp do serwera symboli do rozpoznawania symboli.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja kliencka implementuje ten interfejs i zawiera odwołanie do niej w wywołaniu [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody.  
  
 Aby uzyskać dodatkowe ograniczenia, które mogą być nałożone na proces ładowania, zobacz [idialoadcallback2 —](../../debugger/debug-interface-access/idialoadcallback2.md) interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiareadexeatoffsetcallback —](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [Idiareadexeatrvacallback —](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)