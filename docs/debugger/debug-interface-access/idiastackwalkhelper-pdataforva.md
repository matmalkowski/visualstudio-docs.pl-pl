---
title: IDiaStackWalkHelper::pdataForVA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9eb500539184d6ac5e7e3cb00e753a00f3585057
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31463221"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Zwraca PDATA bloku danych skojarzone z wirtualnym adresem.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `va`  
 [in] Określa wirtualny adres danych do uzyskania.  
  
 `cbData`  
 [in] Rozmiar danych w bajtach do uzyskania.  
  
 `pcbData`  
 [out] Zwraca liczbę bajtów, które zostały pobrane rzeczywisty rozmiar danych.  
  
 `pbData`  
 [w, out] Buforu, który jest wypełniane żądanych danych. Nie może być `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie istnieje żadne PDATA dla określonego adresu. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 PDATA (sekcji o nazwie ".pdata") z compiland zawiera informacje dotyczące obsługi funkcji wyjątków.  
  
 Obiekt wywołujący wie, jak dużo danych jest zwracana więc obiekt wywołujący nie trzeba uzyskać jak dużo danych jest dostępna. W związku z tym jest możliwa do stosowania tę metodę, aby zwrócić błąd, jeśli `pbData` parametr jest `NULL`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)