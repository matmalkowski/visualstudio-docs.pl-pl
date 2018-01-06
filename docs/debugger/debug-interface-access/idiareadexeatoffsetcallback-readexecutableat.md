---
title: IDiaReadExeAtOffsetCallback::ReadExecutableAt | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1250bef977c887be9d4d98fb4372a597c4e22072
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Odczytuje określoną liczbę bajtów, licząc od wskazanego przesunięcia z plikiem wykonywalnym.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 fileOffset  
 [in] Przesunięcie w pliku wykonywalnym ma rozpocząć się odczyt.  
  
 cbData  
 [in] Liczba bajtów do odczytania.  
  
 pcbData  
 [out] Zwraca liczbę bajtów do odczytu.  
  
 dane]  
 [w, out] Tablica jest wypełniane Bajty odczytane z pliku.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez kod obsługi DIA załadować bajtów danych z pliku wykonywalnego przy użyciu przesunięcia bezwzględna do pliku. Ta metoda jest wywoływana wspierających [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiareadexeatoffsetcallback —](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)