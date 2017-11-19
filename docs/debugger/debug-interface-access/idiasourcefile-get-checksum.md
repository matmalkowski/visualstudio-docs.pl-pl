---
title: IDiaSourceFile::get_checksum | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2bcfbc701f6f4799a51d09fac4c4eb184e6f5d7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
Pobiera liczbę bajtów sumy kontrolnej.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbData`  
 [in] Rozmiar buforu danych w bajtach.  
  
 `pcbData`  
 [out] Zwraca liczbę bajtów sumy kontrolnej. Ten parametr nie może być `NULL`.  
  
 `data`  
 [w, out] Buforu, który jest wypełniony bajtów sumy kontrolnej. Jeśli ten parametr ma `NULL`, następnie `pcbData` zwraca liczbę bajtów wymaganą.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby określić typ algorytmu sumy kontrolnej, który został użyty do generowania bajtów sumy kontrolnej, należy wywołać [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) metody.  
  
 Suma kontrolna zwykle są generowane na podstawie obrazu pliku źródłowego, zmiany w pliku źródłowym są uwzględniane w zmiany w bajtach sumy kontrolnej. Jeśli sumy kontrolnej, z jaką bajty są niezgodne sumy kontrolnej generowane na podstawie załadowanego obrazu pliku, a następnie plik należy traktować jako uszkodzony lub zmodyfikowany.  
  
 Typowy sum kontrolnych są nigdy nie więcej niż 32 bajtów, ale nie przyjęto założenie, że jest maksymalny rozmiar sumy kontrolnej. Ustaw `data` parametr `NULL` można pobrać liczby bajtów wymaganej można pobrać sumy kontrolnej. Następnie przydzielić buforu odpowiedni rozmiar i wywołać tę metodę raz z bufor nowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)