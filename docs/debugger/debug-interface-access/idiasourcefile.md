---
title: Idiasourcefile — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile interface
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a810d43df678d79a57a755681907b8c472fdd82d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasourcefile"></a>IDiaSourceFile
Reprezentuje plik źródłowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDiaSourceFile : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDiaSourceFile`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDiaSourceFile::get_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Pobiera wartość klucza proste liczba całkowita, która jest unikatowa dla tego obrazu.|  
|[IDiaSourceFile::get_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Pobiera nazwę pliku źródłowego.|  
|[IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Pobiera typ sumy kontrolnej.|  
|[IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Pobiera moduł wyliczający jednostki kompilacji z numery wierszy odwołujące się do tego pliku.|  
|[IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Pobiera liczbę bajtów sumy kontrolnej.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Uzyskanie przez wywołanie metody tego interfejsu [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) lub [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) metody. Zapoznaj się z przykładem, aby uzyskać szczegółowe informacje.  
  
## <a name="example"></a>Przykład  
 Ta funkcja wyświetla nazwy wszystkich plików źródłowych, przyczyniając się do określonej tabeli.  
  
```C++  
void ShowSourceFiles(IDiaTable *pTable)  
{  
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSourceFiles ),  
                               (void**)&pSourceFiles )  
                  )  
       )  
    {  
        CComPtr<IDiaSourceFile> pSourceFile;  
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR fileName;  
            if ( pSourceFile->get_fileName( &fileName) == S_OK )  
            {  
                printf( "file name: %ws\n", fileName );  
            }  
            pSourceFile = NULL;  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Dia2.h  
  
 Biblioteki: diaguids.lib  
  
 Biblioteki DLL: msdia80.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)   
 [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)   
 [IDiaLineNumber::get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)   
 [IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)   
 [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)