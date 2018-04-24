---
title: IDiaDataSource::loadDataFromIStream | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2421e25c51d005a069de316d1d465eca80a0432b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Przygotowanie debugowania dane przechowywane w pliku bazy danych (.pdb) program dostępne za pośrednictwem strumienia danych w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pIStream  
 [in] <xref:IStream> Obiekt reprezentujący strumienia danych do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|E_PDB_FORMAT|Podjęto próbę dostępu do pliku, którego format nie jest przestarzały.|  
|E_INVALIDARG|Invalidparameter.|  
|E_UNEXPECTED|Źródło danych zostało już przygotowane.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia danych debugowania dla pliku wykonywalnego, które mają zostać uzyskane od ilości pamięci za pomocą <xref:IStream> obiektu.  
  
 Aby załadować plik PDB bez weryfikacji, należy użyć [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metody.  
  
 Aby sprawdzić poprawność plik PDB przed określone kryteria, należy użyć [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) metody.  
  
 Aby uzyskać dostęp do proces ładowania danych (za pośrednictwem mechanizmu wywołanie zwrotne), należy użyć [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)