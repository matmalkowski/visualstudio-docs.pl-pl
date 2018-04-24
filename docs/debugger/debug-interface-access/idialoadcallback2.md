---
title: Idialoadcallback2 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09e835d8a7bfe0bc5d7ae06f0bac457126d21956
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
Odbiera wywołania zwrotne z symboli DIA lokalizowanie procedury w celu umożliwienia ograniczenia nałożone na lokalizowania procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz metod w [idialoadcallback —](../../debugger/debug-interface-access/idialoadcallback.md) interfejsu, tego interfejsu udostępnia następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Określa, czy szuka pliku PDB w oryginalnym katalogu debugowania.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Określa, czy wyszukiwanie plik PDB jest dozwolone w ścieżce, w którym znajduje się plik .exe.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Określa, czy informacje debugowania jest dozwolone z .dbg, pliki.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Określa, czy potrzeby wyszukiwania plików PDB jest dozwolone w katalogu głównym systemu.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja kliencka implementuje ten interfejs i zawiera odwołanie do niej w wywołaniu [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody. Pamiętaj, aby zaimplementować wszystkie metody w [idialoadcallback —](../../debugger/debug-interface-access/idialoadcallback.md) również interfejs.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiareadexeatoffsetcallback —](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [Idiareadexeatrvacallback —](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)