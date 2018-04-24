---
title: IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f71db30a3e4cba957e6aba0981587276af714e3e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Odczytuje określoną liczbę bajtów, licząc od określonej wirtualnej adres względny (RVA) z pliku wykonywalnego.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `relativeVirtualAddress`  
 [in] Adres RVA w pliku wykonywalnym ma rozpocząć się odczyt.  
  
 `cbData`  
 [in] Liczba bajtów do odczytania.  
  
 `pcbData`  
 [out] Zwraca liczbę bajtów do odczytu.  
  
 `data[]`  
 [w, out] Tablica jest wypełniane Bajty odczytane z pliku.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez kod obsługi DIA załadować bajtów danych z plik wykonywalny przy użyciu wirtualnego adresu względnego. Ta metoda jest wywoływana wspierających [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiareadexeatrvacallback —](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)