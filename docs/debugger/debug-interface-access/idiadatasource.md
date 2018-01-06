---
title: "Idiadatasource — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 51a277d9ff1bf190aa87d7c4e9d8d852f8c38323
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiadatasource"></a>IDiaDataSource
Inicjuje dostęp do źródła symboli debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDiaDataSource`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Pobiera nazwę pliku dla ostatniego błędu obciążenia.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Otwiera i przygotowuje plik programu bazy danych (.pdb) jako źródło danych debugowania.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Otwiera i sprawdza, czy plik bazy danych (.pdb) programu odpowiada informacjami podpisu; przygotowuje plik PDB jako źródło danych debugowania.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Otwiera i przygotowuje skojarzonych z plikiem.exe/.dll danych debugowania.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Przygotowanie debugowania dane przechowywane w pliku bazy danych (.pdb) program dostępne za pośrednictwem strumienia danych w pamięci.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Otwiera sesji podczas wykonywania zapytań symboli.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie do jednej z metod obciążenia `IDiaDataSource` otwarte źródła symbolu. Pomyślne wywołanie [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) metoda zwraca [idiasession —](../../debugger/debug-interface-access/idiasession.md) interfejs, który obsługuje badania źródła danych. Jeśli metoda load zwrócą błąd związany z plikami programu [IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) metoda zwraca wartość zawiera nazwę pliku skojarzone z powodu błędu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs są uzyskiwane przez wywołanie metody `CoCreateInstance` funkcji z identyfikatorem klasy `CLSID_DiaSource` i identyfikator interfejsu `IID_IDiaDataSource`. W przykładzie przedstawiono sposób uzyskiwania tego interfejsu.  
  
## <a name="example"></a>Przykład  
  
```C++  
  
      IDiaDataSource* pSource;  
HRESULT hr = CoCreateInstance(CLSID_DiaSource,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaDataSource,  
                              (void**) &pSource);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)