---
title: Wykonywanie zapytania. Plik PDB | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f329d285ec0f9014335b883e0206a426a9aab8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="querying-the-pdb-file"></a>Używanie zapytań dotyczących pliku .Pdb
Plik bazy danych programu (rozszerzenia .pdb) to plik binarny, który zawiera typie i symboliczną informację o debugowaniu zebranych w trakcie kompilowanie i łączenie projektu. Plik PDB jest tworzony podczas kompilowania programu C/C++ przy użyciu **/zi** lub **/zi** lub [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], lub [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] programu z **/debug** Opcja. Pliki obiektów zawierają odwołania do pliku PDB dla informacji debugowania. Aby uzyskać więcej informacji na pdb, pliki, zobacz [PDB, pliki](http://msdn.microsoft.com/en-us/1761c84e-8c2c-4632-9649-b5f99964ed3f). Aplikacji DIA można użyć następujące ogólne kroki, aby uzyskać szczegółowe informacje o różnych symbole, obiekty i elementy danych w ramach obrazu wykonywalnego.  
  
### <a name="to-query-the-pdb-file"></a>W zapytaniu pliku .pdb  
  
1.  Uzyskanie źródła danych, tworząc [idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md) interfejsu.  
  
    ```C++  
    CComPtr<IDiaDataSource> pSource;  
    hr = CoCreateInstance( CLSID_DiaSource,  
                           NULL,  
                           CLSCTX_INPROC_SERVER,  
                           __uuidof( IDiaDataSource ),  
                          (void **) &pSource);  
  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    ```  
  
2.  Wywołanie [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) lub [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) można załadować informacji o debugowaniu.  
  
    ```C++  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    ```  
  
3.  Wywołanie [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) otworzyć [idiasession —](../../debugger/debug-interface-access/idiasession.md) uzyskanie dostępu do informacji o debugowaniu.  
  
    ```C++  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Użyj metody w `IDiaSession` zapytania dla symboli w źródle danych.  
  
    ```C++  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Użyj `IDiaEnum*` informacje o debugowaniu interfejsy, wyliczenia i skanowanie za pomocą symboli lub innych elementów.  
  
    ```C++  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )  
    {  
         // Do something with each IDiaTable.  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiadatasource —](../../debugger/debug-interface-access/idiadatasource.md)