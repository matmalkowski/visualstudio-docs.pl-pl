---
title: IDiaSymbol::get_addressOffset | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e13e130febd36f4b9bf8e0964ac00b78647b034
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)