---
title: IDiaSymbol::get_addressOffset | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d00838fc3f76221293241656743bbf5a2a7f4d26
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetaddressoffset"></a>IDiaSymbol::get_addressOffset
Pobiera przesunięcia część adresu. Używany, gdy [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) ma ustawioną wartość `LocIsStatic`.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Zwraca przesunięcia część adresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.  
  
> [!NOTE]
>  Zwracana wartość `S_FALSE` oznacza, że właściwość nie jest dostępna symbolu.  
  
## <a name="remarks"></a>Uwagi  
 Dla statycznych elementów członkowskich znajdujących się w bibliotece DLL zewnętrznych przesunięcie zwracane przez tę metodę może być 0, zgodnie z tej metody polega na uzyskaniu elementu członkowskiego wirtualnego adresu. Wirtualne adresy są prawidłowe tylko wtedy, gdy [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) metody w [idiasession —](../../debugger/debug-interface-access/idiasession.md) interfejsu została wywołana z parametrem różną od zera, określając adres ładowania biblioteki dll.  
  
 Aby uzyskać sekcji część adresu, należy wywołać [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) metody.  
  
## <a name="requirements"></a>Wymagania  
  
|Wymaganie|Opis|  
|-----------------|-----------------|  
|Nagłówek:|dia2.h|  
|Wersja:|V7.0 DIA SDK|  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md)   
 [Locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md)   
 [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)