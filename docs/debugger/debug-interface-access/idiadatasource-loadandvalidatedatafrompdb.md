---
title: IDiaDataSource::loadAndValidateDataFromPdb | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb140470e45f49806087941127638f56ce5d7150
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Otwiera i sprawdza, czy plik bazy danych (.pdb) programu odpowiada informacjami podpisu i przygotowuje plik PDB jako źródło danych debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdbPath`  
 [in] Ścieżka do pliku PDB.  
  
 `pcsig70`  
 [in] Podpis identyfikatora GUID do weryfikacji podpisu pliku PDB. Pliki .pdb tylko [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] i nowszym mają podpisy identyfikatora GUID.  
  
 `sig`  
 [in] Podpis 32-bitowej do weryfikacji podpisu pliku PDB.  
  
 `age`  
 [in] Sprawdź wartość wieku. Wiek nie musi odpowiadać wartości czasu znane, jest on używany do określenia, czy plik PDB jest zsynchronizowany z odpowiedniego pliku .exe.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono możliwe wartości zwracane dla tej metody.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Nie można otworzyć pliku lub plik ma nieprawidłowy format.|  
|E_PDB_FORMAT|Podjęto próbę dostępu do pliku, którego format nie jest przestarzały.|  
|E_PDB_INVALID_SIG|Podpis jest niezgodny.|  
|E_PDB_INVALID_AGE|Niezgodna wiek.|  
|E_INVALIDARG|Nieprawidłowy parametr.|  
|E_UNEXPECTED|Źródło danych zostało już przygotowane.|  
  
## <a name="remarks"></a>Uwagi  
 Plik PDB zawiera zarówno podpis, jak i wiek wartości. Te wartości są replikowane w pliku .exe lub .dll, który pasuje do pliku PDB. Przed przygotowaniem źródła danych, ta metoda sprawdza, czy podpisu i wieku pliku .pdb nazwanego zgodne podanych wartości.  
  
 Aby załadować plik PDB bez weryfikacji, należy użyć [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) metody.  
  
 Aby uzyskać dostęp do proces ładowania danych (za pośrednictwem mechanizmu wywołanie zwrotne), należy użyć [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody.  
  
 Aby załadować plik PDB bezpośrednio z pamięci, należy użyć [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) metody.  
  
## <a name="example"></a>Przykład  
  
```C++  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)