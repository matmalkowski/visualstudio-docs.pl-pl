---
title: IDiaSourceFile::get_checksumType | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83d1aa687ec7f19df61031d4ff334751ccabaebd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
Pobiera typ sumy kontrolnej.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca typ sumy kontrolnej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Typ Suma kontrolna jest wartość, która może być zmapowana do algorytmu sumy kontrolnej. Na przykład standardowy format pliku PDB zwykle może mieć jedną z następujących wartości:  
  
|Typ sumy kontrolnej|Etykieta CryptoAPI|Opis|  
|-------------------|---------------------|-----------------|  
|0|\<Brak >|Nie istnieje sumy kontrolnej.|  
|1|`CALG_MD5`|Suma kontrolna wygenerowanych przy użyciu algorytmu wyznaczania wartości skrótu MD5.|  
|2|`CALG_SHA1`|Suma kontrolna wygenerowanych przy użyciu algorytmu wyznaczania wartości skrótu SHA1.|  
  
 `CryptoAPI` Etykiety są z `ALG_ID` wyliczenia. Aby uzyskać więcej informacji dotyczących tworzenia skrótów algorytmów, zapoznaj się `CryptoAPI` części programu Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Aby uzyskać bajtów rzeczywista suma kontrolna dla pliku źródłowego, należy wywołać [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)