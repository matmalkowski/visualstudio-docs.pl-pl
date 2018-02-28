---
title: IDiaLoadCallback::NotifyDebugDir | Dokumentacja firmy Microsoft
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
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fad37acafae21c6e82839979360f4ed9574aef1a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Wywoływane, gdy katalog debugowania został znaleziony w pliku .exe.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fExecutable`  
 [in] `TRUE` Jeśli katalog debugowania jest do odczytu z pliku wykonywalnego (zamiast pliku .dbg).  
  
 `cbData`  
 [in] Liczba bajtów danych w katalogu debugowania.  
  
 `data[]`  
 [in] Tablica jest wypełniane katalogu debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Kod powrotny zwykle jest ignorowana.  
  
## <a name="remarks"></a>Uwagi  
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metoda wywołuje tego wywołania zwrotnego, gdy znajdzie katalog debugowania podczas przetwarzania pliku wykonywalnego.  
  
 Ta metoda usuwa potrzebę obsługi informacji o debugowaniu inną niż znaleziono w pliku PDB dla klienta do odtworzenia pliku wykonywalnego i/lub debugowania. Przy użyciu tych danych klienta można rozpoznać typu dostępne informacje o debugowaniu i określa, czy znajdują się w pliku .dbg lub pliku wykonywalnego.  
  
 Większość klientów nie wymaga tego wywołania zwrotnego, ponieważ `IDiaDataSource::loadDataForExe` metody niewidocznie otwiera zarówno .pdb .dbg pliki i gdy jest to niezbędne do obsługi symboli.  
  
## <a name="see-also"></a>Zobacz też  
 [Idialoadcallback2 —](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)