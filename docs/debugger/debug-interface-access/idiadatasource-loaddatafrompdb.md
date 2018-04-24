---
title: IDiaDataSource::loadDataFromPdb | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1910d54ad1a9d2964869beb4854ea97600569b7c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Otwiera i przygotowuje plik programu bazy danych (.pdb) jako źródło danych debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pdbPath  
 [in] Ścieżka do pliku PDB.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Nie można otworzyć pliku lub określić, że plik ma nieprawidłowy format.|  
|E_PDB_FORMAT|Podjęto próbę dostępu do pliku, którego format nie jest przestarzały.|  
|E_INVALIDARG|Nieprawidłowy parametr.|  
|E_UNEXPECTED|Źródło danych zostało już przygotowane.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ładuje dane debugowania bezpośrednio z pliku PDB.  
  
 Aby sprawdzić poprawność plik PDB przed określone kryteria, należy użyć [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metody.  
  
 Aby uzyskać dostęp do proces ładowania danych (za pośrednictwem mechanizmu wywołanie zwrotne), należy użyć [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody.  
  
 Aby załadować plik PDB bezpośrednio z pamięci, należy użyć [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metody.  
  
## <a name="example"></a>Przykład  
  
```C++  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)