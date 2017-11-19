---
title: "Idiareadexeatoffsetcallback — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aaeee00b1e077a587d33e5b1362dda666fcae698
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
Umożliwia aplikacji klienta przekazać plik wykonywalny określony przez położenie pliku w bajtach.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaReadExeAtOffsetCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDiaReadExeAtOffsetCallback`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Odczytuje określoną liczbę bajtów, licząc od wskazanego przesunięcia z plikiem wykonywalnym.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja kliencka implementuje ten interfejs w celu zapewnienia bajtów plik wykonywalny przy użyciu bezwzględnego przesunięcia do pliku wykonywalnego. Aby użyć wirtualnego adresem względnym, zaimplementuj [idiareadexeatrvacallback —](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ta metoda jest implementowany przez aplikację klienta i przekazane do [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody jako metody alternatywnej dla odczytu pliku.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiareadexeatrvacallback —](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)